# Security Policy

Thank you for helping keep **AzuDl - GC2GD** safe.

AzuDl - GC2GD is a Google Colab based downloader that can interact with Google Drive, YouTube cookies, PO Tokens, GitHub tokens, aria2 sessions, torrent metadata, and user-provided links. Because of that, users and contributors must be careful not to expose private files, account data, or credentials.

---

## Supported Versions

Security fixes are generally applied to the latest public release.

| Version | Supported |
|---|---|
| `1.4.20 GUI Beta` | Yes |
| Older versions | Best effort |

If you are using an older version, please update to the latest release before reporting a security issue.

---

## Sensitive Files

Never commit, upload, share, or publish real credentials or private session files.

Examples of sensitive files include:

```text
cookies.txt
youtube_cookies.txt
*_cookies.txt
*.cookies
youtube_po_token.txt
youtube_visitor_data.txt
github_token.txt
aria2_rpc_secret.txt
aria2.session
download_history.json
*.torrent from private trackers
```

These files may contain private account data, authentication material, private tracker metadata, or download history.

---

## YouTube Cookies and PO Tokens

AzuDl may support YouTube cookies and PO Tokens for user-owned sessions when YouTube requires authentication.

Important rules:

- Never commit real YouTube cookies.
- Never commit real PO Tokens.
- Never commit real GitHub tokens.
- Never paste cookies or tokens into public GitHub issues.
- Never share screenshots that reveal cookie values, tokens, account IDs, or private URLs.
- Use placeholder values when sharing examples.

Example safe placeholder:

```text
mweb+YOUR_PO_TOKEN
```

Unsafe example:

```text
mweb+real_private_token_value_here
```

---


---

## GitHub Token Safety

AzuDl may support GitHub tokens for private repositories or higher GitHub API rate limits.

Important rules:

- Never commit a real GitHub token.
- Never paste a real GitHub token into public issues or pull requests.
- Never share screenshots showing token values.
- Use fine-grained tokens with the minimum permissions needed.
- Revoke tokens immediately if they are exposed.

AzuDl may create or read a token template at:

```text
/content/drive/MyDrive/AzuDl-GC2GD/Logs/github_token.txt
```

This file must stay private and should never be uploaded to GitHub.

Safe placeholder:

```text
YOUR_GITHUB_TOKEN
```

Unsafe example:

```text
github_pat_REAL_PRIVATE_TOKEN_VALUE
```

---

## Diagnostic Logs

Diagnostic output may include repository names, file paths, URLs, and error messages.

Before sharing diagnostic logs:

- Remove private repository URLs.
- Remove private file names.
- Remove account identifiers.
- Remove any tokens, cookies, passkeys, or signed URLs.

## Google Drive Safety

AzuDl saves files to Google Drive under:

```text
/content/drive/MyDrive/AzuDl-GC2GD
```

Before sharing logs or screenshots, remove private information such as:

- Google account names
- Private folder names
- Private file names
- Private download URLs
- Personal Drive paths
- Download history entries

---

## Torrent and Private Tracker Safety

For private trackers:

- Prefer using `.torrent` files instead of magnet links.
- Do not share private `.torrent` files.
- Do not upload private tracker screenshots with passkeys, announce URLs, or tracker-specific IDs.
- Do not paste private tracker announce URLs into GitHub issues.
- Remove passkeys and private query parameters before sharing logs.

Unsafe example:

```text
https://tracker.example/announce.php?passkey=REAL_PRIVATE_PASSKEY
```

Safe example:

```text
https://tracker.example/announce.php?passkey=REDACTED
```

---

## Reporting a Vulnerability

Please do **not** open a public GitHub issue for security vulnerabilities.

Use one of these methods instead:

1. GitHub Security Advisories, if available for this repository.
2. Contact the maintainer privately through the official project links in the README.

When reporting a vulnerability, please include:

- A clear description of the issue
- Affected AzuDl version
- Steps to reproduce
- Impact
- Whether any credentials, cookies, tokens, or private files were exposed
- Suggested fix, if you have one

Please remove or redact all private data before sending logs or screenshots.

---

## Public Issue Guidelines

Public GitHub issues are fine for normal bugs, feature requests, and UI problems.

Do not include:

- Real cookies
- Real PO Tokens
- Google account data
- Private tracker passkeys
- GitHub tokens or private repository URLs
- Private `.torrent` files
- Private download links
- Full download history containing private data
- GitHub tokens or private repository URLs

Use placeholders instead.

---

## Responsible Disclosure

If you find a security problem, please give the maintainer reasonable time to investigate and fix it before public disclosure.

The goal is to protect users, their accounts, and their private files.
