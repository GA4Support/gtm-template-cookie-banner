# GA4 Support Cookie Banner

A Google Tag Manager web template that shows a cookie banner on your website and sets
[Google Consent Mode v2](https://developers.google.com/tag-platform/security/guides/consent)
for you.

The tag does three things, in this order:

1. Sets the Consent Mode v2 default to `denied` for every storage type except
   `security_storage`, before any of your other tags run.
2. Reads the `ccb_consent` cookie and restores an earlier choice, so a returning visitor is not
   asked again and your tags get the state that visitor actually gave.
3. Loads the banner interface from `dashboard.ga4support.nl`, keyed on your account ID.

The banner itself — the text, the categories, the cookie table, the consent log — is configured in
your GA4 Support dashboard, not in this template. The template has four settings, and three of
them you can leave alone.

## You need an account

The template loads a banner that belongs to your account, so it needs an account ID. If you don't
have one yet, start at [serverside-support.com](https://serverside-support.com/en/consent-banner/).
The cookie banner is part of every plan.

Your **Account ID** is in the account menu at the top right of
[dashboard.ga4support.nl](https://dashboard.ga4support.nl). It looks like `aB3dEf7h`.

## Install

1. In Google Tag Manager, go to **Templates → Tag Templates → Search Gallery** and search for
   *GA4 Support Cookie Banner*. Click **Add to workspace**.
2. Go to **Tags → New**, pick the template, and fill in your Account ID.
3. Set the trigger to the built-in **Consent Initialization - All Pages**. Nothing else; this tag
   has to run before everything.
4. Submit and publish your container.

Any tag that needs consent should fire on a later trigger than this one.

## Settings

| Setting | Default | What it does |
|---|---|---|
| Account ID | — | Which banner to load. Required. |
| Wait up to 500 ms for the visitor's choice | on | Holds your tags for half a second so a returning visitor's stored choice arrives before the first tag fires. |
| Pass ad click IDs through URLs | off | While advertising consent is denied, the Google tag appends `gclid`, `wbraid` and `dclid` to links within your own domain. Nothing is stored on the device. Useful if visitors often accept on a later page. |
| Redact ad click IDs in requests without consent | off | When advertising consent is denied, Google leaves the click IDs out of its network requests and uses cookieless domains. It protects the visitor further and it costs conversion modelling. |

The consent cookie name is fixed at `ccb_consent`. It is written by the banner script, so there is
nothing to configure and no way to get it wrong.

## What this template does not do

It does not add consent settings to your other tags. Google tags honour the Consent Mode signal by
themselves. A Meta pixel, a LinkedIn Insight Tag or a session recorder does not — those keep firing
unless you tell them otherwise. For each of those, open the tag and set **Advanced Settings →
Consent Settings → Require additional consent for tag to fire**.

A cookie banner is not, by itself, consent enforcement for third-party tags. Worth knowing before
you assume you are covered.

## Support and documentation

- Documentation: <https://serverside-support.com/en/consent-banner/>
- Support: <support@ga4support.nl>

## Licence

Apache 2.0 — see [LICENSE](LICENSE).
