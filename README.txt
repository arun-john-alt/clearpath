CLEARPATH — QUICK GUIDE

Clearpath is a personal cash-flow planner and transaction log. It runs in your
browser without a server, account, analytics, or external runtime dependencies.
The public app starts empty. Your private setup and backups contain financial
information and must remain private.

GET STARTED

1. Open the app, or deploy the generic index.html using the instructions below.
2. Import your private setup JSON from Settings. Review the import before
   replacing any existing data. Import a backup to resume an existing log.
3. Check the snapshot/start month, opening cash, loan opening balances, recurring
   plans, and one-off bills. An unknown opening cash amount is not a zero bank
   balance: forecasts use zero provisionally and show the resulting funding need.
4. Review expected income separately from income already received. Set education,
   investment, reserve, and optional scenario assumptions to amounts you can fund.
5. Export a JSON backup after setup and regularly after recording transactions.

RECORD ACTIVITY ACCURATELY

Planned items are budgets, not bank transactions. Add money actually received or
paid in Activity. For a planned item, select the matching plan and the month it
settles. The payment date records when cash moved; the matching month can differ
for a late bill or an advance payment.

A partial payment leaves the unpaid part of that plan in the forecast. Mark an
item complete only when no more money is expected for that occurrence. If the
actual total exceeds the budget, the forecast keeps the larger actual total.
Unlinked entries are additional activity; they do not replace an existing plan.

For a loan payment, enter principal only when you know the principal portion.
The full payment reduces cash; only its stated principal reduces the linked loan
balance. Interest is not principal. Do not log the same payment twice as both an
expense and a debt payment. Do not overwrite an opening loan balance with today's
balance while retaining principal payments already applied to that snapshot.
To allocate an aggregate EMI across loans, record its individual loan payments
against the same EMI plan/month. Their total must equal the actual payment; do
not also retain a duplicate entry for the full aggregate EMI.

PUBLIC GITHUB PAGES DEPLOYMENT

1. Create a separate repository or publishing folder containing ONLY the generic
   public index.html. Its seed must be null and it must contain no private setup,
   backup, transactions, names, notes, screenshots, or financial figures.
2. Commit that public file. In repository Settings > Pages, select the intended
   publishing source/branch and folder. Open the resulting HTTPS Pages URL.
3. Import the private setup JSON through the running app on your own device.
   Importing uses your browser; the file is not added to the repository or site.
4. Keep private JSON files outside the publishing folder and outside Git history.
   A .gitignore entry does not remove a file that has already been committed.

If using the source bundle, publish only public/. The dist/ and deliverables/
folders also contain private files and are not safe to publish as whole folders.

Do not publish a personalized standalone HTML build: embedded financial data is
readable in its source. A public app is acceptable only when it contains empty,
generic defaults. Hosting a page is not access control for data embedded in it.

For stronger separation, use a dedicated origin that serves only this app. Other
scripts hosted on the same origin can access its localStorage. Different project
paths under the same GitHub Pages hostname are not separate storage boundaries.
Avoid adding analytics, third-party scripts, or untrusted code to that origin.

PRIVACY, STORAGE, AND BACKUPS

Local storage is browser/device-specific, unencrypted, and not a cloud backup.
Anyone with access to the browser profile may be able to read it. This app has no
password, encryption, multi-user separation, automatic sync, or bank connection.
Use a trusted device/profile and protect exported backups like bank statements.

Browser data clearing, private-browsing cleanup, profile changes, storage limits,
or a different URL origin can make saved data unavailable. Direct file:// storage
behavior varies by browser; use a stable HTTPS origin for regular use. Export a
backup before moving the app, clearing browser data, importing another dataset,
or changing devices. Test a restore before relying on a backup.

Backups contain the current setup and log, not an independent bank statement.
Clearpath does not upload or recover your backups for you. Keep dated copies in
your own protected storage. Never put them in a public repository or share a
screen containing private data without checking it first.

FORECAST CONVENTIONS AND LIMITS

* Recorded cash uses opening cash and actual transactions. Forecast cash combines
  actuals with only the remaining amounts of matching planned occurrences.
  Entries before the snapshot month do not change that snapshot again. Imported
  future-dated entries do not count as cash already available today.
* A negative forecast is an unfunded cash shortage. The app does not create a new
  loan, overdraft, or fictitious income to cover it. Month-end cash also does not
  guarantee that money will be available for every bill within that month.
* Annual premiums are counted in their scheduled payment months. Their monthly
  reserve figure is information, not a second expense. Liquidity thresholds are
  targets, not payments. Education/investment provisions reduce available cash;
  they do not forecast investment returns or account balances.
  Monthly goal settings begin at the opening month. For a later start date, leave
  that setting at zero and create a dated plan instead.
* Expected income, future bonuses, salary rises, and inflation are assumptions.
  Scenario switches do not turn these assumptions into actual receipts.
* Aggregate EMI plans control projected cash. Loan balances are tracked only from
  explicitly allocated actual principal. Unknown APRs/EMIs remain unknown; the
  app does not infer exact whole-debt payoff dates from incomplete loan data.
* Home-loan comparisons are hypothetical amortization illustrations for the
  comparison principal and rate. They exclude other debts, approval conditions,
  fees, future rate changes, and affordability checks. Scenario prepayments do
  not silently become cash-flow payments: add an explicit plan or actual entry.
* A refinance moves debt. Closing one account with a new loan does not itself
  reduce total debt. Update the loan snapshot and cash records consistently.

Check statements, take-home income after business costs/tax, loan terms, and bill
dates before relying on a plan. Locked investments are not emergency cash. Keep
education amounts provisional until the timing and cost of the goal are known.

REFERENCE DOCUMENTATION

MDN — Window.localStorage:
https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage

GitHub — Creating a GitHub Pages site:
https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site

GitHub — About GitHub Pages:
https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages

RELEASE SAFETY

The public distribution consists only of index.html, README.txt and .nojekyll.
Its embedded starting state is null. Application updates keep the same local
storage key and do not reset your entries. The hosted app starts empty on a new
origin: import a fresh backup for recorded activity, or your initial setup JSON
if you have not recorded any activity yet.

Use one active editing tab. Conflicting storage changes require a reload before
saving. If saved JSON cannot be read, Export backup downloads the original raw
text for recovery, rather than an empty replacement. Keep that file even if it
cannot currently be imported. Restore/reset confirmations protect against
accidental replacement; verify that backup downloads actually finish.

GitHub Pages receives normal page requests and may log visitor IP addresses.
No financial entry, private setup or backup is uploaded by this app.
