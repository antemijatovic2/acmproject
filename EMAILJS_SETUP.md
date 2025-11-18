# EmailJS Setup Instructies

Het contactformulier gebruikt EmailJS om emails te versturen. Volg deze stappen om het in te stellen:

## Stap 1: Maak een EmailJS account aan

1. Ga naar https://www.emailjs.com/
2. Klik op "Sign Up" en maak een gratis account aan
3. Log in op je account

## Stap 2: Voeg een Email Service toe

1. Ga naar "Email Services" in het dashboard
2. Klik op "Add New Service"
3. Kies je email provider (Gmail, Outlook, etc.)
4. Volg de instructies om je email account te verbinden
5. Noteer de **Service ID** die wordt gegenereerd

## Stap 3: Maak een Email Template

1. Ga naar "Email Templates" in het dashboard
2. Klik op "Create New Template"
3. Gebruik deze template variabelen:
   - `{{from_name}}` - Naam van de afzender
   - `{{from_email}}` - Email adres van de afzender
   - `{{phone}}` - Telefoonnummer (optioneel)
   - `{{subject}}` - Onderwerp
   - `{{message}}` - Bericht

**Voorbeeld template:**
```
Onderwerp: Nieuw contactformulier bericht: {{subject}}

Van: {{from_name}} ({{from_email}})
Telefoon: {{phone}}

Bericht:
{{message}}
```

4. Noteer de **Template ID** die wordt gegenereerd

## Stap 4: Haal je Public Key op

1. Ga naar "Account" > "General"
2. Scroll naar "API Keys"
3. Kopieer je **Public Key**

## Stap 5: Configureer de website

Open `index.html` en zoek naar deze regels (rond regel 671-673):

```javascript
const EMAILJS_SERVICE_ID = 'YOUR_SERVICE_ID';
const EMAILJS_TEMPLATE_ID = 'YOUR_TEMPLATE_ID';
const EMAILJS_PUBLIC_KEY = 'YOUR_PUBLIC_KEY';
```

Vervang de waarden:
- `YOUR_SERVICE_ID` → Je Service ID uit Stap 2
- `YOUR_TEMPLATE_ID` → Je Template ID uit Stap 3
- `YOUR_PUBLIC_KEY` → Je Public Key uit Stap 4

**Voorbeeld:**
```javascript
const EMAILJS_SERVICE_ID = 'service_abc123';
const EMAILJS_TEMPLATE_ID = 'template_xyz789';
const EMAILJS_PUBLIC_KEY = 'abcdefghijklmnop';
```

## Stap 6: Pas het ontvangende email adres aan

Zoek naar regel 734 in `index.html`:

```javascript
to_email: 'ac-mario@outlook.com'
```

Vervang dit met het email adres waar je de formulier berichten wilt ontvangen.

## Test het formulier

1. Open je website
2. Vul het contactformulier in
3. Verstuur het formulier
4. Controleer of je een email ontvangt

## Gratis Tier Limieten

EmailJS gratis tier biedt:
- 200 emails per maand
- Basis email templates
- Standaard support

Voor meer emails of features, overweeg een betaald plan.

## Problemen oplossen

- **Geen email ontvangen?** Controleer je spam folder
- **Foutmelding bij verzenden?** Controleer of alle IDs correct zijn ingevuld
- **EmailJS niet geladen?** Controleer je internetverbinding

