# First Stock — Registration (frontend-only)

This is a frontend-only clone of the registration page at `https://king.apps-kongs.site/register?ref=93AQSR`.

Files:

- `index.html` — main page
- `styles.css` — styling
- `script.js` — client-side behavior (parses `ref` query param, validates form)

To view locally, open `index.html` in your browser or run a static server, for example:

```bash
# Python 3 (from the project folder)
python -m http.server 8000
# then open http://localhost:8000/index.html?ref=93AQSR
```

This project is frontend-only — the form submission is simulated in the browser.

New pages added:

- `login.html` — login page (simulated auth)
- `dashboard.html` — frontend dashboard (reads sessionStorage)

Quick flow to test:

```bash
# Start server from project folder
python -m http.server 8000
# Open http://localhost:8000/index.html?ref=93AQSR to register
# After register, open http://localhost:8000/login.html and login to reach dashboard
```

Plan flow:

- Click a plan on `dashboard.html` to view it in `namebank.html`.
- `namebank.html` simulates purchase and stores purchases in `localStorage`.

Buy flow:

- From `namebank.html` click `Buy Plan` to view bank details on `bank.html`.
- `bank.html` shows account details and the plan/amount; click "I've Paid" to record the purchase locally and return to the dashboard.

Withdraw flow:

- On `dashboard.html` click the `Withdraw` button next to the Available Balance.
- This navigates to `withdraw.html?amount=...` and shows a simulated "Withdraw successful" message; withdrawals are recorded in `localStorage.withdrawals`.
 - This navigates to `withdraw.html?max=...` where you can enter a custom amount (validated against the available balance). Confirming redirects to `withdraw-success.html?amount=...` and records the withdrawal in `localStorage.withdrawals`.
