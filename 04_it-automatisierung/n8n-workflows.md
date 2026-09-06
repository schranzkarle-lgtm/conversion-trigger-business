# 🔧 n8n Workflow & Automation Blueprints

## 📋 Komplette n8n Automation (Copy-Paste Ready)

### WORKFLOW 1: Lead Magnet → Email Optin

```json
{
  "name": "Lead Magnet Funnel",
  "nodes": [
    {
      "name": "Leadpages Form Submit",
      "type": "webhook",
      "description": "Triggered wenn jemand Lead Magnet Form einträgt"
    },
    {
      "name": "Extract Email & Name",
      "type": "functionItem",
      "code": "return {\n  email: $input.first().json.email,\n  name: $input.first().json.name,\n  timestamp: new Date().toISOString()\n}"
    },
    {
      "name": "Brevo Add Contact",
      "type": "brevo",
      "operation": "createContact",
      "email": "{{ $node['Extract Email & Name'].json.email }}",
      "attributes": {
        "FIRSTNAME": "{{ $node['Extract Email & Name'].json.name }}",
        "TAGS": ["lead_magnet_optin"]
      }
    },
    {
      "name": "Send Welcome Email",
      "type": "brevo",
      "operation": "sendEmail",
      "to": "{{ $node['Extract Email & Name'].json.email }}",
      "subject": "Hier ist dein kostenloses Hebel #1 🎁",
      "body": "[HTML Email Template]"
    },
    {
      "name": "Send Lead Magnet PDF",
      "type": "brevo",
      "operation": "sendEmail",
      "attachments": "https://yoursite.com/hebel-1.pdf",
      "to": "{{ $node['Extract Email & Name'].json.email }}"
    },
    {
      "name": "Log to Google Sheets",
      "type": "google_sheets",
      "action": "append",
      "spreadsheet": "Conversion Hooks Analytics",
      "range": "Leads!A:E",
      "data": [
        "{{ $node['Extract Email & Name'].json.timestamp }}",
        "{{ $node['Extract Email & Name'].json.email }}",
        "{{ $node['Extract Email & Name'].json.name }}",
        "lead_magnet",
        "pending"
      ]
    }
  ]
}
```

---

### WORKFLOW 2: Payment Received → Deliver Product

```json
{
  "name": "Payment Delivery Automation",
  "nodes": [
    {
      "name": "Stripe Webhook",
      "type": "webhook",
      "description": "payment_intent.succeeded"
    },
    {
      "name": "Extract Payment Details",
      "type": "functionItem",
      "code": "return {\n  customer_email: $input.first().json.billing_details.email,\n  amount: $input.first().json.amount / 100,\n  currency: $input.first().json.currency,\n  timestamp: new Date().toISOString()\n}"
    },
    {
      "name": "Brevo Tag as Customer",
      "type": "brevo",
      "operation": "updateContact",
      "email": "{{ $node['Extract Payment Details'].json.customer_email }}",
      "tags": ["paid_customer", "conversion_hooks_buyer"]
    },
    {
      "name": "Send E-Book Download",
      "type": "brevo",
      "operation": "sendEmail",
      "to": "{{ $node['Extract Payment Details'].json.customer_email }}",
      "subject": "Dein Zugang ist ready! 🎉",
      "body": "[HTML mit Download Button: https://yoursite.com/ebook-7-hooks.pdf]"
    },
    {
      "name": "Send Course Access Link",
      "type": "brevo",
      "operation": "sendEmail",
      "body": "Hier ist dein Zugang zu Video Tutorials + Community"
    },
    {
      "name": "Log Revenue",
      "type": "google_sheets",
      "action": "append",
      "range": "Revenue!A:D",
      "data": [
        "{{ $node['Extract Payment Details'].json.timestamp }}",
        "{{ $node['Extract Payment Details'].json.customer_email }}",
        "{{ $node['Extract Payment Details'].json.amount }}",
        "paid"
      ]
    },
    {
      "name": "Schedule Follow-Up Email",
      "type": "delay",
      "time": "2 days"
    },
    {
      "name": "Send Implementation Email",
      "type": "brevo",
      "operation": "sendEmail",
      "to": "{{ $node['Extract Payment Details'].json.customer_email }}",
      "subject": "Challenge: Zeig mir dein erstes Post! 🚀"
    }
  ]
}
```

---

### WORKFLOW 3: Upsell Automation (Day 7)

```json
{
  "name": "Upsell Email Trigger",
  "nodes": [
    {
      "name": "Check Days Since Purchase",
      "type": "scheduled",
      "cron": "0 9 * * *",
      "description": "Daily at 9 AM"
    },
    {
      "name": "Query Recent Customers",
      "type": "google_sheets",
      "action": "query",
      "range": "Revenue!A:D",
      "where": "days_since_purchase = 7"
    },
    {
      "name": "Brevo Send Upsell",
      "type": "brevo",
      "operation": "sendBulkEmail",
      "to": "[All Customers - 7 Days]",
      "subject": "Die anderen 6 Hebel KOMBINIEREN... (97€)",
      "body": "[Upsell Email Template]"
    }
  ]
}
```

---

## 📊 Alternative: Zapier Workflows (Wenn n8n zu kompliziert)

### ZAPP 1: Leadpages → Brevo → Google Sheets
```
Trigger: Leadpages Form Submission
├─ Aktion 1: Create Contact in Brevo
├─ Aktion 2: Send Welcome Email (Brevo)
└─ Aktion 3: Append to Google Sheets
```

### ZAPP 2: Stripe → Brevo → Slack Notification
```
Trigger: Stripe Successful Payment
├─ Aktion 1: Update Contact (Brevo) - Tag as "Paid"
├─ Aktion 2: Send Download Email (Brevo)
└─ Aktion 3: Notify in Slack (Optional)
```

---

## 🚀 Setup Instructions (Step-by-Step)

### Option A: n8n Cloud (Easiest)
```
1. Gehe zu n8n.cloud
2. Sign up (kostenlos bis 1.000 Executions/Monat)
3. Create New Workflow
4. Copy-Paste die JSON Blueprints
5. Connect Credentials:
   - Stripe API Key
   - Brevo API Key
   - Google Sheets
6. Activate Workflow
```

### Option B: Zapier (Drag & Drop)
```
1. Zapier.com Sign up (kostenlos bis 100 Tasks/Monat)
2. Create Zap
3. Select Trigger (Leadpages, Stripe, etc)
4. Connect Accounts
5. Add Actions (Brevo, Google Sheets)
6. Test & Publish
```

### Option C: Make.com (Mid-Range)
```
1. Make.com Sign up
2. Create Scenario
3. Add Modules (Trigger → Actions)
4. Similar zu Zapier aber mehr Customization
```

---

## 📝 API Keys erforderlich

```bash
# Stripe
STRIPE_API_KEY=sk_live_xxxxxxxxxxxxx
STRIPE_WEBHOOK_SECRET=whsec_xxxxxxxxxxxxx

# Brevo
BREVO_API_KEY=xsrNxxxxxxxxxxxxxxxxxxxx

# Google Sheets
GOOGLE_SHEETS_API_KEY=[OAuth Token]

# Optional: Slack
SLACK_WEBHOOK_URL=https://hooks.slack.com/services/xxxxx/xxxxx/xxxxx
```

**SICHERHEIT:** Speichere API Keys niemals in Code!
Nutze Environment Variables oder n8n Credential Manager.

---

## ✅ Testing Checklist

- [ ] Test Lead Magnet Workflow (Submit Form)
- [ ] Verify Welcome Email received
- [ ] Verify PDF Download works
- [ ] Test Payment Workflow (Stripe Test Mode)
- [ ] Verify E-Book Download Email sent
- [ ] Check Google Sheets Logging
- [ ] Test Upsell Email (Manual Trigger)
- [ ] Verify All Emails arrive (Spam Check)
- [ ] Test Refund Flow

---

**Status:** 🟢 Automation Templates Ready
**Nächster Schritt:** Deploy auf n8n/Zapier + Testing
