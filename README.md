# Eventeny CSV Validator

A simple JavaScript-based web application to validate CSV files containing ticket purchase data and detect fraudulent accounts.

## Features

The validator checks for the following fraud indicators:

1. **Fraudulent Accounts**: Accounts with more than 4 tickets
2. **Potentially Fraudulent Accounts**: 
   - Accounts with more tickets than badges purchased
   - Accounts with no convention badges but any number of tickets

## Usage

1. Open `index.html` in a web browser (or use a local web server)
2. Drag and drop your CSV file onto the upload area, or click "Choose File"
3. View the validation results showing:
   - Summary statistics (fraudulent, potentially fraudulent, and valid accounts)
   - Detailed account-by-account breakdown with issue descriptions

## CSV Format

The CSV file must contain the following columns:
- `Purchaser email` - Used to identify unique accounts
- `Ticket name` - Used to distinguish between badges and tickets

### Badge Types (Convention Badges)
- Registration 3 Day
- Registration Friday
- Registration Saturday
- Registration Sunday
- Registration - Child
- Registration - Youth
- Dealer's Badge
- Dealer's Comp Badge

### Ticket Types
- Friday Concert VIP
- Friday Concert GA
- Charity Ball
- Concert Ticket
- (Any other non-badge ticket types)

## Running Locally

You can run a simple HTTP server to test the application:

```bash
# Python 3
python3 -m http.server 8000

# Node.js (with http-server)
npx http-server -p 8000

# Then open http://localhost:8000 in your browser
```

## Validation Rules

1. **Maximum Tickets**: An account can buy up to 4 tickets. Accounts exceeding this limit are flagged as fraudulent.

2. **Ticket-to-Badge Ratio**: An account that has more tickets than badges purchased will be flagged as potentially fraudulent.

3. **No Badges**: An account that has purchased no convention badges but any number of tickets is flagged as potentially fraudulent.
