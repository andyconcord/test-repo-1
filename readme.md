# Concord Google Ads landing pages — concordvisas.com

Netlify site `merry-elf-38f56d`, custom domain concordvisas.com (main Webflow site stays on concordvisa.com).
One folder per LP: `/<country>/<page-slug>/` (index.html + assets/). Built with the `build_lp.py` pipeline
(see project doc `lp-ca-wp-extension-deploy-notes.md` in the "google ads" Claude project).

Live pages:
- /au/482-visa-requirements/  (AU 482 Requirements — v5 Free Assessment offer, rebuilt 4 Sep 2026; live since 5 Aug 2026)
- /ca/work-permit-extension/  (CA Work Permit Extension & Renewal)
- /au/migration-agents/       (AU Registered Migration Agents — general; Free Assessment version rebuilt 4 Sep 2026; ?city= variants dropped)
- /ca/immigration-consultants/ (CA Licensed Immigration Consultants — general; supports ?city=toronto|vancouver|calgary|... )
- /au/become-a-sponsor/        (AU Employers — Standard Business Sponsorship; added 23 Oct 2026; noindex, ads only)
    Not built with build_lp.py: plain index.html + styles.css + images/ + fonts/ (hashed file names).
    Forms are styled on the page and submit straight to HubSpot (portal 442100905, ap1, Forms API v3):
      Book a consult a184ed06-6101-4955-b6d0-36fc98d1e40a (firstname, lastname, email, company) -> booking conversion X5k1… (AUD 500)
      Checklist popup 4f01eac9-b431-4edc-a0da-5668321e450b (firstname, lastname, email)        -> checklist conversion OtTH…
      'Book a free consultation' clicks -> booking-form-opened conversion 1jVV… (NZD 1). Google tag AW-18359573431.
    If fields change in HubSpot, the page's forms need the same change.

Deploy: drag a zip of this folder's CONTENTS onto the existing site's Deploys tab,
or (once connected) push to the linked Git repository.
When adding an LP: add its folder + a matching immutable-cache [[headers]] block in netlify.toml.
