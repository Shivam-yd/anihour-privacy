# AniHour privacy website — GitHub Pages and GoDaddy

Repository: https://github.com/Shivam-yd/anihour-privacy

Intended policy URL: **https://anihour.com/privacy-policy**

Only public privacy-page files belong in this repository. Do not upload the mobile app source, signing keys, credentials, or private documents. Preparing the repository does not enable GitHub Pages, configure DNS, or issue an HTTPS certificate.

## 1. Verify ownership in GitHub

In your GitHub **account Settings → Pages**, add `anihour.com` under verified domains. GitHub provides a unique TXT record. In GoDaddy's DNS manager, add that exact TXT record and return to GitHub to verify it. Use the generated name/value, not a guessed verification code.

Domain verification helps prevent someone else from claiming the domain for their Pages site. It is distinct from the repository's Pages settings below.

## 2. Enable the privacy website

Open the repository → **Settings → Pages**:

- Source: **Deploy from a branch**
- Branch: **main**
- Folder: **/ (root)**
- Save.
- Under **Custom domain**, confirm or enter `anihour.com` and save. The repository's `CNAME` file already contains this domain.

This is the step that enables publication. Review the public policy and contact information before enabling it.

## 3. Point the GoDaddy domain to GitHub Pages

In GoDaddy → your domain → **DNS → Manage DNS**, configure:

| Type | Name / Host | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | Shivam-yd.github.io |

Use GoDaddy's default TTL unless you have a reason to change it. Remove or replace only conflicting website records for `@`/`www`, such as a parking-page record. **Keep email MX records, domain-verification TXT records, and unrelated subdomain records.** If an existing website uses these records, changing them moves that website; review before proceeding.

Do not use wildcard DNS records. The CNAME target is the account's GitHub Pages hostname, not the repository URL or a URL with a path.

These addresses are from GitHub's official custom-domain instructions. DNS and certificate provisioning can take time; repeated app changes will not accelerate that.

## 4. Enable HTTPS and verify the live page

When GitHub's DNS check and certificate provisioning finish, enable **Enforce HTTPS** in the repository's Pages settings.

Verify in a private browser window and on a phone:

- `https://anihour.com/privacy-policy` displays the full policy without a sign-in or file download.
- A redirect to `/privacy-policy/` is acceptable.
- The certificate is valid.
- App name, developer name, contact address and data-use disclosures match the offline policy in AniHour.

Only after that verification should the URL be submitted in Google Play Console.

## Updating the policy

The source policy is `artifacts/mobile/lib/privacy-policy.json`. After changing it, run the mobile app's `privacy:export` script. Copy the generated HTML to **both** `index.html` and `privacy-policy/index.html` in the public policy repository, then let Pages republish. Do not change only the website and leave the offline policy stale.

The mobile app does not call this repository to load anime data, so this static privacy website is not a backend requirement for the installed app.

## Official instructions

- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/verifying-your-custom-domain-for-github-pages
- https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
