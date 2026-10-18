# Legal pages for Missing Time

Published via GitHub Pages at https://souciance-ci.github.io/legal/

| Page | What it is |
|---|---|
| `privacy.html` | Privacy policy |
| `terms.html` | End user licence agreement |
| `dpa.html` | Data processing addendum, incorporating the SCCs |
| `scc-annexes.html` | Annexes I, II and III to the Standard Contractual Clauses |
| `tia.html` | Transfer impact assessment (Schrems II) |
| `dpia.html` | DPIA support pack, for the customer's Article 35 assessment |

Everything is published rather than "available on request". A compliance reviewer who can
read the answer in thirty seconds does not open a ticket.

## The one thing still missing

- [ ] **Appoint an EU representative (GDPR Art. 27) and a UK representative.**

This is the only remaining gap, and it cannot be written: it requires actually mandating a
company in the EU and in the UK, in writing, and paying them. Specialist providers do this
for a few hundred euros a year each.

It is required because the app systematically monitors the behaviour of people in the EU,
which rules out the "occasional processing" exemption in Art. 27(2)(a). **Do not publish
a clause claiming a representative exists until one is actually mandated**, and add their
name and postal address to the privacy policy and the addendum once they are.

Also outstanding, but neither is a document:

- [ ] Have a lawyer read `terms.html` and `dpa.html`.
- [ ] Decide on a company structure before the first paying customer. Processing other
      companies' HR data as a natural person means personal assets answer for professional
      liabilities.

## Keeping them true

These pages make verifiable claims. **If the app's behaviour changes, these change in the
same commit.** A privacy policy that drifts from the code is worse than none.

| Claim | Where it is true in the code |
|---|---|
| Admin-only access | `src/resolvers/auth.js`, called by every resolver |
| No email or comment used | `narrow()` in `src/resolvers/worklogs.js` |
| 26-week retention, deleted by age | `prune()` in `src/resolvers/settings.js`, on read and on write |
| Deletion on uninstall | `avi:forge:uninstalled:app` trigger in `manifest.yml` |
| No outbound network call | absence of `permissions.external` in `manifest.yml` |
| No write to Jira | scopes in `manifest.yml` are read-only |
| No personal data in logs | `console.log` calls in `src/resolvers/scheduled.js` |

The TIA commits to a review on any change to egress, write permissions, storage keys,
logging, or sub-processors. That list is not decorative: it is the trigger condition for
redoing the assessment.

