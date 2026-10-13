# BELIEVE INZIDEUS TRADERS
## Grocery Business Management System (PHP / Hybrid Modular Storage / Mobile-First UI)

---

### 1. System Architecture & Data-Flow Diagram

```
+-----------------------------------------------------------------------------------+
|                           CLIENT TIER (Mobile / Tablet / Desktop)                |
|  - Responsive HTML5 / CSS3 (Tailwind CSS) / Vanilla JS UI                         |
|  - Role-Adaptive Navigation (Owner vs Employee 1 & 2)                              |
|  - Client-side validation, auto calculations (Subtotal, Tax, Discounts, Balance)   |
|  - Offline draft support & receipt thermal printing styling                       |
+------------------------------------------+----------------------------------------+
                                           | HTTPS / JSON Fetch API / Form POST
                                           v
+-----------------------------------------------------------------------------------+
|                        APPLICATION SERVER (PHP 8.2+ on Apache/Nginx)              |
|                                                                                   |
|  [Core Security & Auth Middleware]                                                |
|   - Session Fixation & Strict Cookie Security (HttpOnly, SameSite=Strict)        |
|   - Argon2id / bcrypt Password Hashing                                            |
|   - CSRF Token Validation & Rate Limiter (Brute Force Protection)                 |
|   - Role-Based Access Control (RBAC): Owner vs Employee                           |
|                                                                                   |
|  [Business Logic Controllers]                                                     |
|   - AuthController.php (Login, logout, session check)                             |
|   - DashboardController.php (KPI aggregation, stock alerts, cashflow)            |
|   - InventoryController.php (SKU, categories, units, negative stock guard)        |
|   - PurchaseController.php (Supplier bills, draft/confirm, itemized batching)     |
|   - SalesController.php (Invoices, POS entry, UPI/Cash, receipt printer)          |
|   - ExpenseController.php (Operational costs, delivery, rent, packing)           |
|   - BillUploadController.php (MIME validation, secure renaming, private cloud)   |
|   - ReportController.php (P&L, COGS engine, Excel/CSV export engine)              |
|                                                                                   |
|  [Storage Abstraction Layer (DataInterface.php)]                                  |
|   +---------------------------------------+------------------------------------+  |
|   | Adapter A: Google Sheets API v4 / GAS | Adapter B: SQLite / MySQL PDO      |  |
|   | Adapter C: Microsoft Graph API (Excel)| Adapter D: Local JSON / File Cache |  |
|   +---------------------------------------+------------------------------------+  |
+------------------------------------------+----------------------------------------+
                                           |
                    +----------------------+----------------------+
                    v                                             v
+---------------------------------------+   +---------------------------------------+
|        STRUCTURED DATA STORAGE        |   |         PRIVATE BILL STORAGE          |
|  Google Sheets / Excel Online         |   |  Private Cloud Storage                |
|  - Products, Purchases, Sales         |   |  - Non-public directory or Drive/Blob |
|  - Expenses, Customers, Suppliers     |   |  - Access only via tokenized PHP      |
|  - AuditLog, Users, CashMovements     |   |    streaming (stream_bill.php)        |
+---------------------------------------+   +---------------------------------------+
```

---

### 2. Recommended Hosting & Storage Integration

1. **Web Hosting**:
   - Standard cPanel/Linux VPS or shared hosting with PHP 8.1+, SSL/HTTPS, and OpenSSL.
   - Recommended: Hostinger, SiteGround, or AWS Lightsail / DigitalOcean LAMP droplet.

2. **Spreadsheet Integration Recommendation**:
   - **Primary**: Google Sheets API via Google Cloud Service Account (JWT) or lightweight Google Apps Script Web App webhook. Google Sheets Apps Script web app endpoint provides instant zero-dependency JSON REST API without bulky composer dependencies.
   - **Alternative**: Microsoft Graph REST API for OneDrive / Excel Online.
   - **Seamless Fallback / Production Scale**: Built-in SQLite / MySQL PDO adapter that can be toggled with a single line in `config.php`:
     ```php
     define('STORAGE_DRIVER', 'sheets'); // Options: 'sheets', 'mysql', 'local'
     ```

3. **Private Bill Storage Security**:
   - Uploads are saved into a private storage directory above `public_html` or protected via `.htaccess` (`Deny from all`).
   - Files are sanitized and renamed with UUID: `e.g., BILL_PUR_20250524_a9f8e71c.pdf`.
   - Served only to authenticated users through a controller (`download_bill.php?id=...`) checking role permissions.

---

### 3. Folder Structure

```
believe-inzideus-traders/
├── config/
│   ├── config.php                 # App settings, environment vars, DB/Sheets toggle
│   ├── database.php               # PDO database connection (if MySQL/SQLite active)
│   ├── credentials-sample.json    # Sample Service Account credentials for Sheets
│   └── .htaccess                  # Protect config directory
├── core/
│   ├── Auth.php                   # Authentication, RBAC, session guards
│   ├── CSRF.php                   # Anti-CSRF token generator & validator
│   ├── StorageInterface.php       # Universal interface for data persistence
│   ├── SheetsAdapter.php          # Google Sheets / Apps Script client
│   ├── PdoAdapter.php             # MySQL / SQLite fallback adapter
│   └── Logger.php                 # Tamper-evident Audit log engine
├── controllers/
│   ├── AuthController.php
│   ├── DashboardController.php
│   ├── InventoryController.php
│   ├── PurchaseController.php
│   ├── SalesController.php
│   ├── ExpenseController.php
│   └── ReportController.php
├── storage/
│   ├── bills/                     # Protected uploaded receipts/bills (.htaccess Deny from all)
│   ├── backups/                   # System data snapshots
│   └── logs/                      # Audit trails
├── public/
│   ├── index.php                  # Application router / dashboard entry
│   ├── login.php                  # Secure authentication screen
│   ├── sales.php                  # Sales entry & invoice generator
│   ├── purchases.php              # Purchase recording & bill uploader
│   ├── inventory.php              # Stock master, reorder levels, categories
│   ├── expenses.php               # Expense recording
│   ├── reports.php                # P&L, stock reports, GST/tax summaries
│   ├── print-invoice.php          # Printable thermal / A4 invoice generator
│   ├── download-bill.php          # Protected file access gateway
│   └── assets/
│       ├── css/style.css          # Green & White grocery branding theme
│       ├── js/app.js              # Real-time POS calculations & modal scripts
│       └── images/                # Logo & icons
└── README.md                      # GitHub setup & deployment guide
```

---

### 4. Spreadsheet Schema & Sample Rows

#### Sheet 1: `Products`
| SKU | Name | Category | Unit | CostPrice | SellPrice | ReorderLevel | CurrentStock | Status |
|---|---|---|---|---|---|---|---|---|
| BIT-RIC-001 | Sona Masoori Rice (25kg) | Rice | packets | 1350.00 | 1580.00 | 10 | 45 | ACTIVE |
| BIT-PUL-002 | Toor Dal Premium | Pulses | kg | 145.00 | 168.00 | 25 | 120 | ACTIVE |
| BIT-OIL-003 | Cold Pressed Sunflower Oil 1L | Cooking Oils | litres | 130.00 | 155.00 | 15 | 8 | LOW_STOCK |
| BIT-MIL-004 | Foxtail Millet (Navane) | Millets | kg | 85.00 | 110.00 | 10 | 35 | ACTIVE |

#### Sheet 2: `Purchases`
| PurchaseID | Date | SupplierName | InvoiceNo | Subtotal | Tax | AdditionalCosts | TotalAmount | PaidAmount | Balance | Status | BillFileID | CreatedBy |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PUR-2025-001 | 2025-05-20 | Sri Lakshmi Agro Mills | SL-8842 | 45000.00 | 2250.00 | 500.00 | 47750.00 | 47750.00 | 0.00 | CONFIRMED | BILL_PUR_8842.pdf | employee1 |
| PUR-2025-002 | 2025-05-23 | Pure Gold Oil Traders | PG-1029 | 18500.00 | 925.00 | 200.00 | 19625.00 | 10000.00 | 9625.00 | CONFIRMED | MISSING_BILL | employee2 |

#### Sheet 3: `Sales`
| InvoiceNo | Date | CustomerName | CustomerPhone | TotalAmount | Discount | Tax | FinalAmount | PaidAmount | Balance | PaymentMethod | Status | CreatedBy |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| INV-2025-1001 | 2025-05-24 | Ramesh Kumar | 9876543210 | 2840.00 | 40.00 | 0.00 | 2800.00 | 2800.00 | 0.00 | UPI | COMPLETED | employee1 |
| INV-2025-1002 | 2025-05-24 | Anitha Sharma | 9845123456 | 1550.00 | 0.00 | 0.00 | 1550.00 | 1550.00 | 0.00 | CASH | COMPLETED | employee2 |

#### Sheet 4: `Expenses`
| ExpenseID | Date | Category | Description | Amount | PaymentMode | AttachmentID | CreatedBy |
|---|---|---|---|---|---|---|---|
| EXP-2025-042 | 2025-05-24 | Transport | Tempo delivery charge for Rice bags | 650.00 | CASH | EXP_REC_042.jpg | employee1 |
| EXP-2025-043 | 2025-05-24 | Packing | Polypropylene grain bags 50pcs | 450.00 | UPI | EXP_REC_043.pdf | employee2 |

#### Sheet 5: `AuditLog`
| LogID | Timestamp | User | Action | Module | RecordRef | Details |
|---|---|---|---|---|---|---|
| LOG-901 | 2025-05-24 09:15:20 | owner | LOGIN | AUTH | USER_1 | Successful login from IP 49.37.12.84 |
| LOG-902 | 2025-05-24 10:30:11 | employee1 | CREATE_SALE | SALES | INV-2025-1001 | Sale ₹2,800.00 (Stock deducted: BIT-RIC-001) |

---

### 5. User-Role Permission Matrix

| Module / Action | Owner | Employee 1 | Employee 2 |
|---|:---:|:---:|:---:|
| **Login / Logout** | Yes | Yes | Yes |
| **View Dashboard Basic KPI (Today's Sales, Purchases)** | Yes | Yes | Yes |
| **View Gross Profit, Net Profit & Valuation Cards** | **Yes** | No | No |
| **Create New Sale & Print Receipt** | Yes | Yes | Yes |
| **Sales Return / Refund Authorization** | **Yes** | Draft only | Draft only |
| **Create New Purchase & Upload Bill** | Yes | Yes | Yes |
| **Add / Edit Allowed Product Details** | Yes | Yes | Yes |
| **Negative Stock Override Authorization** | **Yes** | No | No |
| **Record Daily Operational Expenses** | Yes | Yes | Yes |
| **View Daily Sales & Purchase Reports** | Yes | Yes | Yes |
| **View Comprehensive P&L / Inventory Valuation** | **Yes** | No | No |
| **Manage Users & Reset Passwords** | **Yes** | No | No |
| **Download Audit Logs & System Backup** | **Yes** | No | No |

---

### 6. Profit and Loss (P&L) Calculation Formulas

All figures tracked and displayed in Indian Rupees (₹).

1. **Net Sales**:
   $$\text{Net Sales} = \text{Gross Sales} - \text{Sales Returns} - \text{Trade Discounts Allowed}$$

2. **Cost of Goods Sold (COGS)**:
   $$\text{COGS} = \text{Opening Inventory Value} + \text{Net Purchases} + \text{Direct Freight/Transport Costs} - \text{Closing Inventory Value}$$
   *(Traceable alternative: Sum of item quantity sold $\times$ weighted purchase cost)*

3. **Gross Profit**:
   $$\text{Gross Profit} = \text{Net Sales} - \text{COGS}$$
   $$\text{Gross Margin \%} = \left(\frac{\text{Gross Profit}}{\text{Net Sales}}\right) \times 100$$

4. **Net Profit or Loss**:
   $$\text{Net Operating Profit} = \text{Gross Profit} - \text{Total Operating Expenses (Rent, Electricity, Wages, Delivery, Packing)}$$
