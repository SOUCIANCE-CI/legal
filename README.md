# Legal pages for Missing Time

Published via GitHub Pages at https://souciance-ci.github.io/legal/

## Still required before charging money

- [ ] **Appoint an EU representative (GDPR Art. 27) and a UK representative.** The app
      systematically monitors the behaviour of people in the EU, so the "occasional
      processing" exemption does not apply. Specialist providers do this for a few hundred
      euros a year. **Do not publish a clause claiming a representative exists until one is
      actually mandated in writing.**
- [ ] **Complete the SCC Schedule** (Annexes I, II and III of Implementing Decision (EU)
      2021/914). The addendum incorporates the Clauses and refers to a Schedule that is not
      yet written.
- [ ] **Write the transfer impact assessment.** The addendum says one exists and is
      available on request. Four to six pages. Its conclusion is already strong: there is
      no copy of customer data anywhere we control, so there is nothing an authority could
      compel us to hand over.
- [ ] **Write the DPIA support pack.** Section 9.2 promises it.
- [ ] Have a lawyer read `terms.html` and `dpa.html`.

## Keeping them true

These pages make verifiable claims. **If the app's behaviour changes, these change in the
same commit.** A privacy policy that drifts from the code is worse than none, and three
independent reviews caught exactly that in version 1.

Current claims correspond to:

| Claim | Where it is true in the code |
|---|---|
| Admin-only access | `src/resolvers/auth.js`, called by every resolver |
| No email or comment used | `narrow()` in `src/resolvers/worklogs.js` |
| 26-week retention, deleted by age | `prune()` in `src/resolvers/settings.js`, on read and on write |
| Deletion on uninstall | `avi:forge:uninstalled:app` trigger in `manifest.yml` |
| No outbound network call | absence of `permissions.external` in `manifest.yml` |
| No write to Jira | scopes in `manifest.yml` are read-only |
| No personal data in logs | `console.log` calls in `src/resolvers/scheduled.js` |

## What version 1 got wrong

Worth remembering, because the mistake was structural rather than careless. Version 1
argued that because all data stays inside Atlassian, there was no international transfer.
That is wrong: under Chapter V, a transfer is about who the data becomes *available to*,
not where the servers are. The vendor is in Côte d'Ivoire, so there is a transfer.

The facts were right and the conclusion was wrong. Version 2 keeps every fact and replaces
the conclusion: not "there is no transfer" but "there is a transfer, and here is why it
carries less risk than most".
