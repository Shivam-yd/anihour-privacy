# AniHour privacy website — free GitHub Pages

Repository: https://github.com/Shivam-yd/anihour-privacy

Public policy URL: **https://shivam-yd.github.io/anihour-privacy/privacy-policy/**

Only public privacy-page files belong in this repository. Never upload mobile app source, signing keys, credentials, or private documents.

## Hosting configuration

In the repository's **Settings → Pages**:

- Source: **Deploy from a branch**
- Branch: **main**
- Folder: **/ (root)**
- Custom domain: **empty**
- HTTPS enforced.

Do not add a `CNAME` file. This setup uses GitHub's free address and requires no GoDaddy or other DNS changes. Only the policy webpage is hosted, not the mobile app or a backend.

## Updating the policy

The source is `artifacts/mobile/lib/privacy-policy.json`. Run:

```sh
pnpm --filter @workspace/mobile run privacy:export
```

Copy `public/privacy-policy/index.html` to both `index.html` and `privacy-policy/index.html` in the public policy repository, then let Pages republish. Keep `.nojekyll` in its root. Keep the offline app policy and website text identical.

After an update, open the public URL without signing in and check that the full policy loads over HTTPS. Use that same address in Play Console and the app's policy configuration.

Google Play declarations, signed Android packaging, and Android device testing remain separate release requirements.
