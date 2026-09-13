# Illustration delivery and privacy

Updated: September 14, 2026

This note describes the static assets in this repository and the optional unit
downloads used by current Tanren builds. The app's public privacy policy is
https://www.randaworks.com/tanren/privacy/.

## What the app sends

After the user confirms a unit download, the app makes an HTTPS GET for a public
`.scenepack` file at `raw.githubusercontent.com`. The request URL identifies the
requested pack by a fixed content hash. That hash is shared by all users of the
same pack; it is not a user identifier and does not anonymize the connection.

The app does not add learner records, answers, profiles, account credentials, or
custom user/device identifiers to the URL, query, or request body. Its native
URLSession uses an ephemeral configuration with no cookie storage. Standard
network metadata, including the client's IP address, request time, requested
path, and normal client headers, can still reach the delivery service. The
requested file can be associated with its learning unit using the public catalog.

Downloaded illustration files stay on the device until removed. The app stores
them separately from learner data, excludes the re-downloadable image storage
from backups, and supports deleting or re-downloading a selected unit. Shared
images needed by another selected unit remain available.

## Repository operator and hosting provider

This repository contains static files and has no learner-data endpoint,
authentication service, advertising script, or analytics SDK. Asset requests go
to GitHub's hosting infrastructure. Public source files do not mean that a
network request is anonymous or that the hosting provider retains no logs.

GitHub's [General Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement)
describes service usage information, including IP addresses, device information,
and request dates and times, as well as potential processing purposes and
retention criteria. Its general statement does not establish a precise retention
period or a complete field-by-field use and identity-linkage description for this
particular unauthenticated raw-content request.

The repository operator cannot configure GitHub's raw-content access-log
retention through this repository. Making the repository public, changing this
README, disabling cookies in the app, or using hashed filenames does not switch
off GitHub's infrastructure logging. GitHub Pages settings concern a separate
service; these asset URLs use `raw.githubusercontent.com`.

## App Store privacy disclosure

Apple's [App Privacy guidance](https://developer.apple.com/app-store/app-privacy-details/)
distinguishes data used only to service a request in real time from data retained
afterward. Data categories and purposes must match actual handling, including
relevant external services. Optional downloads alone do not establish Apple's
optional-disclosure exception.

This repository note does not certify **Data Not Collected**, **Data Not Linked
to You**, or any other App Store label. Before relying on such a label, establish
which raw-delivery metadata is retained, why, whether it is linked to an identity
or other datasets, and whether it is used for cross-service advertising or data
broker sharing. Record the applicable provider evidence with the app's release
review. A README change is not a change to those provider practices.

## Reporting an issue

For an image error or delivery failure, use this repository's Issues with a pack
hash or non-personal description. Do not post learner records, private backups,
names, credentials, IP addresses, or access logs in a public issue. For questions
about GitHub's own processing, use the contact channels in GitHub's privacy
statement rather than publishing personal details here.
