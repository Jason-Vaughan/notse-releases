# Security Policy

Notse handles license keys, machine fingerprints, and opens a network port on the helper machine. We take security reports seriously.

## Reporting a vulnerability

**Do not file security issues publicly.** Email **support@jasonvaughan.com** with the subject prefix `[SECURITY]` and we'll route it privately.

Helpful detail to include:
- Affected version (Notse app version + helper version)
- Operating system + setup (Mac alone, or Mac + Windows helper)
- A description of the issue and its impact
- Steps to reproduce, if you have them
- Whether the issue is currently being exploited in the wild (please tell us)

## What's in scope

Vulnerabilities in:
- The macOS app (`Notse.app`)
- The Windows / macOS helper (`NotseHelper.exe` / `notse-helper`)
- The WebSocket protocol between Mac and helper
- License validation (client-side enforcement)
- Bundled auto-update mechanism

## What's not in scope

These are upstream services we use but don't control:
- **Stripe** (payment processing) — report to [Stripe's security team](https://stripe.com/contact/security)
- **Keygen.sh** (license issuance) — report to [Keygen](https://keygen.sh/security/)
- **Apple notarization / Gatekeeper** — report to Apple
- **Microsoft SmartScreen** — report to Microsoft
- **Resend** (license-key email delivery) — report to [Resend](https://resend.com/security)

If you find an issue in one of these, please report directly to that vendor. We'll happily coordinate if there's a Notse-specific angle.

## Response timeline

- Initial acknowledgement: within 3 business days of receipt
- Triage + severity assessment: within 1 week
- Fix timeline: depends on severity and complexity — coordinated with the reporter

## Disclosure

We prefer coordinated disclosure: we work with the reporter on a fix, ship it, then publicly acknowledge the report (with the reporter's name if they want credit) in the relevant release notes. Please give us a reasonable window before public disclosure.

## Thank you

Independent security review is a real help. If your report leads to a fix that ships, we're happy to credit you in the release notes — let us know in your initial email whether you want that.
