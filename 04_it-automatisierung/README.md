# 4️⃣ Abteilung: IT & Automatisierung

## 💻 Mission
Setup der kompletten technischen Infrastruktur für dein automatisiertes Online-Business.

---

## 👥 Die 3 Rollen

### 💻 Web Developer
Baut Landingpages, Sales Pages, Checkout

### 🪠 Automation Engineer
Erstellt n8n Workflows, Email Sequenzen, CRM Integration

### 💳 Payment Architect
Integriert Stripe, PayPal, Email-Automation

---

## 🎉 Das Stack (Tech Stack)

```
┌─────────────────────────────────────────────┐
│         CONVERSION-TRIGGER FUNNEL           │
└─────────────────────────────────────────────┘

1. LANDINGPAGE (Pagebuilder)
   ├─ Leadpages / Unbounce / Webflow
   ├─ Lead Magnet: "Kostenlos 1 Hebel"
   └─ Opt-in Form (Email Capture)
        ↓
2. EMAIL AUTOMATION (n8n / Zapier)
   ├─ Welcome Email (sofort)
   ├─ Lead Magnet Download (PDF)
   ├─ Value Emails (Tag 2, Tag 5)
   └─ Segmentation ("Bought" vs "Not Bought")
        ↓
3. SALES PAGE (Pagebuilder)
   ├─ E-Book Sales Page (29€)
   ├─ Checkout Integration
   └─ Thank You Page + Download Link
        ↓
4. PAYMENT PROCESSING (Stripe / PayPal)
   ├─ Instant Payment Confirmation
   ├─ Automatic Invoice
   └─ Revenue Tracking
        ↓
5. DELIVERY SYSTEM
   ├─ Automatic E-Book Download
   ├─ Course Access (Teachable / Kajabi)
   └─ Community Access (Slack / Circle)
        ↓
6. UPSELL AUTOMATION
   ├─ Day 7: Advanced Course (97€)
   ├─ Day 14: 1-on-1 Coaching (297€)
   └─ Day 30: Mastermind (597€)
```

---

## 💻 Technologie-Stack (Copy-Paste Ready)

### OPTION A: Budget-Friendly (€0-50/Monat)
```
✅ Landingpage: Leadpages ($25/Monat)
✅ Email Automation: Brevo (kostenlos bis 300 Kontakte)
✅ Payment: Stripe (2.9% + 0.30€ per transaction)
✅ Hosting: Cloudflare Pages (kostenlos)
✅ Form: Typeform (kostenlos)
✅ Course Hosting: Thinkific (kostenlos bis 5 Kurse)

GESAMT: ~€50/Monat
PERFEKT FÜR: Anfänger, MVP Testing
```

### OPTION B: Growth-Stack (€100-200/Monat)
```
✅ Landingpage: Unbounce ($75/Monat)
✅ Email Automation: ActiveCampaign ($99/Monat)
✅ Payment: Stripe + Paddle
✅ Hosting: Webflow ($120/Monat)
✅ CRM: Pipedrive (kostenlos)
✅ Course: Kajabi ($149/Monat)

GESAMT: ~€150/Monat
PERFEKT FÜR: Scaling, Professional Look
```

### OPTION C: Enterprise-Stack (€300+/Monat)
```
✅ Landingpage: Custom Built (Webflow)
✅ Email Automation: ConvertKit ($99+)
✅ Payment: Stripe + Square
✅ Hosting: AWS / Vercel
✅ CRM: HubSpot ($50+)
✅ Course: Kajabi ($249+)
✅ Analytics: Google Analytics 4 + Mixpanel

GESAMT: €300-500/Monat
PERFEKT FÜR: Multiple Revenue Streams, Team
```

---

## 🚀 Quick-Start Setup (OPTION A - Budget)

### Schritt 1: Leadpage erstellen (30 Min)
```
1. Gehe zu Leadpages.net
2. Wähle Template: "Lead Magnet"
3. Passe an:
   - Headline: "Kostenlos: Der #1 Instagram Conversion Hebel"
   - Subheadline: "48 Stunden + dann ist es weg"
   - CTA Button: "Kostenlos erhalten"
4. Add Email Capture Form
5. Connect zu Brevo (Email Service)
6. Publish
```

### Schritt 2: Email Automation (Brevo) aufsetzen (30 Min)
```
1. Brevo.com Konto erstellen (kostenlos)
2. Create Contact List: "Conversion Hooks Subscribers"
3. Create Email Template (Welcome Email)
   - Subject: "Du hast Zugang ✅ + Bonus Video"
   - Body: [Nutze Template aus Content Section]
4. Create Automation Workflow:
   - Trigger: Neue Email hinzugefügt
   - Action: Welcome Email (sofort)
   - Action: Lead Magnet PDF (sofort)
   - Delay 2 Tage
   - Action: Value Email #1
5. Test mit deiner Email
```

### Schritt 3: Sales Page (Leadpages) (45 Min)
```
1. Leadpages.net → Sales Page Template
2. Customize:
   - Headline: "Die 7 Psychologischen Hebel für Instagram-Verkäufe"
   - Sections: Problem → Solution → What You Get → Proof → FAQ → CTA
   - [Nutze Copy aus Content Section]
3. Add Payment Button (Stripe Integration)
4. Create "Thank You" Page
   - Text: "Download startet in 3 Sekunden..."
   - Redirect: E-Book Download Link
5. Publish
```

### Schritt 4: Stripe Setup (20 Min)
```
1. Stripe.com Konto erstellen
2. Add Product: "7 Conversion Hooks" (€29)
3. Create Payment Link
4. Connect zu Leadpages (Webhook)
5. Test Payment (Stripe Test Mode)
6. Live Mode aktivieren
```

### Schritt 5: Automation Flow vollständig (30 Min)
```
1. Brevo Workflow erweitern:
   - When: Payment received (via Stripe Webhook)
   - Action: Add Tag "Paid Customer"
   - Action: Move to List "Customers"
   - Action: Send Email with Download Link
   - Action: Add zu Course Access (Thinkific)
   
2. Test: Kaufe dein eigenes Produkt (€29)
   - Solltest Email sofort bekommen
   - E-Book sollte downloadbar sein
```

---

## 🔗 Webhook & Integration Setup

### Stripe → Brevo Webhook
```
1. Stripe Dashboard → Developers → Webhooks
2. Add Endpoint: https://brevo.com/webhook/stripe
3. Events: payment_intent.succeeded
4. Test Webhook
```

### Leadpages → Brevo Integration
```
1. Leadpages Settings → Integrations
2. Brevo API Key einfügen
3. Map Fields:
   - Form Email → Brevo Contact Email
   - Form Name → Brevo Contact Name
4. Test mit Dummy Submission
```

---

## 📊 Tracking & Analytics Setup

### Google Analytics 4 (Kostenlos)
```
1. analytics.google.com → Neues Property erstellen
2. Measurement ID: G-XXXXXXXXXX
3. Add zu Leadpages / Webseite
4. Track Events:
   - Lead Magnet Optin
   - Product Purchase
   - Email Click
   - Course Access
```

### Conversion Tracking Spreadsheet (Google Sheets)
```
Kolumnen:
- Date
- Leads (Email Optins)
- Sales (€29 Purchases)
- Upsells (€97 Purchases)
- Revenue
- Cost (Ads)
- ROI

Formula: ROI = (Revenue - Cost) / Cost * 100%

Target: ROI > 200% (€1 spend = €3 revenue)
```

---

## ✅ Deployment Checklist

- [ ] Leadpage erstellt & getestet
- [ ] Brevo Email Automation konfiguriert
- [ ] Sales Page live
- [ ] Stripe Payments funktionieren
- [ ] Webhooks verbunden
- [ ] E-Book Download funktioniert
- [ ] Email Sequenz läuft
- [ ] GA4 Tracking aktiv
- [ ] Test Purchase durchgeführt
- [ ] Refund Policy set
- [ ] Privacy Policy set
- [ ] Terms of Service set

---

## 🚀 Go-Live Checklist

### 48 Stunden vor Launch:
- [ ] Alle Inhalte finalisiert
- [ ] System getestet
- [ ] Email Sequenz approved
- [ ] Payment working
- [ ] Support Email Setup

### Launch Day:
- [ ] Domain live
- [ ] Lead Magnet bewerbbar
- [ ] Sales Page live
- [ ] Zahlungen akzeptieren
- [ ] Customer Support ready

### Post-Launch:
- [ ] Daily Revenue Tracking
- [ ] Email Open Rates checken
- [ ] Conversion Rate monitoren
- [ ] Customer Feedback sammeln
- [ ] Weekly Optimization

---

**Status:** 🟢 IT-Setup Ready
**Nächster Schritt:** [05_marketing-traffic](../05_marketing-traffic/README.md)
