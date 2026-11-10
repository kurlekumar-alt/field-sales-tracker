[readme.md](https://github.com/user-attachments/files/34612740/readme.md)
# Field Sales Performance Tracker
**Gratia Pharma Solutions**

> ### ⚠️ CONFIDENTIALITY & DATA INTEGRITY NOTICE
> **Only for sales employees of Gratia Pharma Solutions.**  
> By using this application, you agree to maintain strict confidentiality and data integrity. All territory call details, doctor interaction notes, client pricing, order bookings, and performance data are the exclusive proprietary property of Gratia Pharma Solutions. Unauthorized sharing, tampering, or disclosure is strictly prohibited.

---

## 1. Overview
The **Gratia Pharma Solutions Field Sales Performance Tracker** is a dedicated, mobile-first web application designed for Medical Representatives (MRs) and Sales Managers. It streamlines daily field reporting, tracks doctor and pharmacy interactions, monitors qualified sales leads, and compiles automated weekly and monthly performance rollups.

---

## 2. Core Metrics Tracked
Every field submission captures the following parameters:

| Metric | Field Type | Benchmark / Description |
| :--- | :--- | :--- |
| **Areas Covered** | Text | Specific clinics, hospitals, streets, or territory routes visited today. |
| **Doctor Visits** | Number | Standard daily target: **10 doctor calls**. |
| **Pharmacy Visits** | Number | Standard daily target: **6 chemist calls**. |
| **Potential Leads** | Number | Qualified prospects / doctors interested in new formulations or product trials. |
| **Orders Received** | Number | Count of purchase orders booked. |
| **Order Revenue** | Currency ($ / ₹) | Total commercial value of orders booked during field visits. |

---

## 3. Access Control & Security Rules

### A. Individual Representative Portal (`📱 Rep Phone Submission`)
* **Dedicated Authentication**: Each sales representative accesses their portal using an individual 4-digit PIN (default: `1234`).
* **Identity Isolation**: Reps can only submit reports under their verified profile and cannot view or enter data for colleagues.
* **Submission Locking**: Once a daily report is submitted, the record is immediately **locked** into read-only mode to prevent accidental tampering or post-facto alterations.
* **Personal History**: Reps can tap **My Past Logs** to view their complete historical archive of past submitted dates, routes, and call totals.
* **Personal Trends**: Reps can tap **My Trends** to monitor their individual weekly (50 doctor calls / 30 pharmacy visits) and monthly progress bars in real time without exposing team-wide confidential numbers.
* **PIN Customization**: Reps can change their PIN at any time using the **Change My PIN** tool.

### B. Managerial Governance (`📊 Manager Dashboard`)
* **Master Manager Authentication**: Protected by an administrative 4-digit PIN (default: `9999`).
* **Correction Rights**: In cases of genuine clerical error or route updates, only the sales manager has the privilege to edit, adjust, or correct submitted records via the **Edit** action on each log row.
* **Roster Management**: Managers can add new representatives (`➕ Add New Representative`), remove departing personnel (`🗑️`), or rename territory profiles via **Edit Team Names**.
* **One-Click Export**: Managers can download comprehensive daily, weekly, and monthly audit reports via **Export CSV Report**.

---

## 4. Free Hosting via GitHub Pages

This application runs as a lightweight, single-page client application with zero required software installations.

1. **Repository Setup**:
   * Create a new repository on [GitHub](https://github.com/) named `gratia-sales-tracker`.
   * Set repository visibility to **Public** (required for standard GitHub Pages).
2. **File Upload**:
   * Save the application file as `index.html`.
   * Upload `index.html` and this `README.md` directly into the repository root.
3. **Activate Pages**:
   * Navigate to **Settings > Pages** in your GitHub repository.
   * Under **Branch**, select `main` (or `master`), keep folder `/ (root)`, and click **Save**.
4. **Distribute Link**:
   * Open the generated link (e.g., `https://<your-username>.github.io/gratia-sales-tracker/`).
   * Share the URL with Gratia Pharma Solutions sales representatives via WhatsApp or email.
   * Instruct reps to tap browser menu > **"Add to Home Screen"** on their mobile devices to use it as an app icon.

---

## 5. Shared Cloud Storage (Google Sheets Integration)

To synchronize field submissions from multiple smartphones into a central database in real time:

1. Create a Google Sheet named `Gratia Pharma - Field Submissions`.
2. Open **Extensions > Apps Script** and paste:
   ```javascript
   function doPost(e) {
     var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
     var data = JSON.parse(e.postData.contents);
     sheet.appendRow([
       new Date(),
       data.date,
       data.repName,
       data.areasCovered,
       data.docs,
       data.pharms,
       data.leads,
       data.orders,
       data.orderValue
     ]);
     return ContentService.createTextOutput(JSON.stringify({status: "ok"}))
       .setMimeType(ContentService.MimeType.JSON);
   }
   ```
3. Deploy as a Web App (access set to *Anyone*).
4. Paste the Web App URL into the **☁️ Cloud Setup** button within the tracker.

---

## 6. Employee Compliance Statement
By logging into this application, every representative acknowledges that:
1. Daily field call reports must reflect genuine, in-person professional visits conducted on the specified date.
2. Doctor and pharmacy contact details must adhere to healthcare data privacy and institutional standards.
3. Inaccurate, falsified, or surrogate reporting constitutes a direct violation of Gratia Pharma Solutions company policy.
