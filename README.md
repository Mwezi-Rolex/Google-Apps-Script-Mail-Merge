# 📧 Custom CRM & Mail Merge Automation

**A zero-cost, serverless CRM solution engineered for the Strathmore Business Club (SBC) using Google Apps Script.**

### 🎯 Project Overview
**Context:** The Strathmore Business Club needed a way to communicate personally with hundreds of members without incurring the high monthly costs of enterprise CRM tools (like Mailchimp or Salesforce).
**The Solution:** I engineered a custom mail merge system directly within the Google Workspace ecosystem, enabling personalized mass communication at zero cost.

### 💡 Key Features
* **Zero-Cost Infrastructure:** Runs entirely on Google's free quotas, eliminating subscription overhead.
* **Personalized Messaging:** Dynamically inserts member details (Name, Membership ID, Status) into email templates.
* **Automated Dispatch:** Capable of handling mass communication queues for hundreds of members.
* **HTML Support:** Sends professional, rich-text HTML emails rather than plain text.

### 🛠️ Technical Implementation
* **Language:** JavaScript (Google Apps Script)
* **Data Source:** Google Sheets API
* **Services:** GmailApp Service

### 🚀 Impact
* **Cost Savings:** completely eliminated the need for paid email marketing subscriptions.
* **Scale:** Successfully handles communication for the entire club membership (hundreds of students).
* **Efficiency:** Reduced the time spent on manual email drafting by 90%.

### 📂 File Structure
* `Code.js` - The core logic handling the spreadsheet iteration and email dispatch.
* `email-template.md` - The template used for the email.
* `Mail Merge Trial - Sheet1.csv` - Example data structure required for the script to run.

---

### 💻 Code Snippet (Logic)
```javascript
// Example logic used in the system
function sendEmails() {
  var sheet = SpreadsheetApp.getActiveSheet();
  var startRow = 2; // First row of data to process
  var numRows = sheet.getLastRow() - 1; // Number of rows to process
  var dataRange = sheet.getRange(startRow, 1, numRows, 3);
  var data = dataRange.getValues();

  for (var i = 0; i < data.length; ++i) {
    var row = data[i];
    var emailAddress = row[0];
    var message = "Hello " + row[1] + ", here is your membership update...";
    MailApp.sendEmail(emailAddress, "SBC Update", message);
  }
}
