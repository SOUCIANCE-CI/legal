# Legal pages for Missing Time

Published via GitHub Pages at https://souciance-ci.github.io/legal/

Atlassian requires a public privacy policy and end-user terms before an app can be
listed. Because the app stores personal data on a customer's behalf, it also acts as a
data processor, which is why there is a DPA alongside them.

## Before submitting the app

- [ ] Replace `contact@souciance.com` in all four pages with the real support address.
- [ ] Have a lawyer read `terms.html` and `dpa.html`. They were drafted to be accurate
      about what the app does, not to be bulletproof in court.

## Keeping them true

These pages make verifiable claims: no outbound network calls, read-only Jira scopes,
26-week retention, deletion on uninstall. **If the app's behaviour changes, these change
with it, in the same commit.** A privacy policy that drifts from the code is worse than
none, and Atlassian's review checks the match.

Current claims correspond to:
- scopes `read:jira-work`, `read:jira-user`, `storage:app` in `manifest.yml`
- storage keys `settings`, `roster`, `history` in `src/resolvers/settings.js`
- `HISTORY_WEEKS = 26` in the same file
- no `fetch` to anything but `requestJira` in `src/resolvers/`
