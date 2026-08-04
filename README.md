# Choice Hotels (choice-hotels)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Choice Hotels International (NYSE: CHH) is a United States hotel franchisor headquartered in North Bethesda, Maryland, operating 7,575 hotels with 656,825 rooms open across 49 states, the District of Columbia and 50 countries and territories as of December 31, 2025. Its brands include Comfort, Quality, Clarion, Sleep Inn, Econo Lodge, Rodeway Inn, MainStay Suites, Suburban Studios, WoodSpring Suites, Everhome Suites, Cambria Hotels, Ascend Hotel Collection and the Radisson Americas brands. Choice sits on the supply side of the travel distribution chain as a franchisor rather than an owner: its proprietary choiceEDGE central reservation system pushes rate, inventory and availability to ChoiceHotels.com, the Choice Privileges mobile apps, the global distribution systems (Sabre, Amadeus), the OTAs (Expedia, Booking.com) and metasearch (Kayak, Tripadvisor), while its proprietary choiceADVANTAGE property management system runs the majority of its franchised properties. API posture is honestly none-published — no public developer portal, no published API reference, no machine-readable contract, and no exit path.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/choice-hotels/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/choice-hotels/refs/heads/main/apis.yml)

## Tags

- Travel
- United States
- Hospitality
- Hotels
- Booking
- Reservations
- Distribution
- Franchising
- Loyalty

## Timestamps

- **Created:** 2026-07-28
- **Modified:** 2026-07-28

## APIs

None. Choice Hotels publishes no public API, no developer portal, and no machine-readable contract.

A TIBCO Mashery API management layer is live at `api.choicehotels.com`, but every probed path returns HTTP 596 with `X-Mashery-Error-Code: ERR_596_SERVICE_NOT_FOUND` — the gateway exists, no public service is mapped to it. `developer.choicehotels.com` returns HTTP 404 from a Mashery Proxy under a `CN=mashery.com` certificate with no `choicehotels.com` SAN: a hostname pointed at Mashery with no provisioned portal. The Internet Archive's earliest record of that hostname, from March 2012, is a `robots.txt` returning HTTP 401 — the developer surface has been credential-gated for more than a decade.

## Switching Cost

Recorded in full in [`review.yml`](review.yml). In short:

| Dimension | Finding |
| --- | --- |
| Interface shape | `none-published` — no OpenAPI, no OpenTravel/OTA or HTNG reference; choiceEDGE and choiceADVANTAGE are described as proprietary in the FY2025 Form 10-K |
| Second source | `no-alternative` — Choice-branded inventory originates only in Choice's CRS; GDS, OTA and bed-bank routes re-intermediate Choice rather than replace it |
| Exit path | `no-export-published` — no export, dump, bulk or portability operation exists, because no API surface exists |
| Identifier portability | GDS chain codes and per-property GDS/OTA codes travel; Choice Privileges member numbers, confirmation numbers and choiceADVANTAGE property IDs do not |
| Contractual lock-in | Franchise agreements "typically have an initial term of between 10 and 30 years" and "typically contain liquidated damages provisions" on early termination (FY2025 Form 10-K). Nothing is published about API or data terms |
| Distribution model | `gds-intermediated` — the 10-K names Sabre, Amadeus, Expedia, Booking.com, Kayak and Tripadvisor as CRS channels alongside direct booking |
| NDC posture | Not applicable — NDC is an airline distribution standard |
| Access gate | `commercial-agreement` — a franchise agreement for hotel owners, a SkyTouch /CONNECT vendor request for technology partners, an existing GDS/OTA relationship for distributors |

For a franchisee, leaving Choice means re-flagging a physical building; the technology estate is inseparable from the brand licence. For a technology vendor, the only way in is a certification queue Choice controls.

## Security Posture

Choice Hotels does publish one real, verifiable public program: a [Responsible Disclosure / Vulnerability Disclosure Policy](https://www.choicehotels.com/legal/responsible-disclosure). Reports go to `responsibledisclosure@choicehotels.com`, acknowledgement is committed within **five business days**, good-faith researchers are given safe harbour, and Choice states explicitly that it does **not** run a bug bounty. Social engineering, resource exhaustion, physical testing and denial of service are out of scope. Captured in [`security/choice-hotels-vulnerability-disclosure.yml`](security/choice-hotels-vulnerability-disclosure.yml).

The policy is not machine-discoverable: no `/.well-known/security.txt` is served on any Choice host — see [`well-known/choice-hotels-well-known.yml`](well-known/choice-hotels-well-known.yml) for the full probe table.

A domain-security probe of the whole estate is in [`security/choice-hotels-domain-security.yml`](security/choice-hotels-domain-security.yml). Notable finding: `api.choicehotels.com` and `developer.choicehotels.com` both present the TIBCO Mashery certificate (`CN=mashery.com`, SANs `*.mashery.com` only) with no `choicehotels.com` SAN, so a verifying HTTPS client cannot complete the handshake at all. Neither registrable domain is DNSSEC-signed or publishes CAA; both publish SPF and DMARC, but DMARC sits at `p=none`. No trust center, no published certifications, no status page.

## Artifacts

| Artifact | File | Method |
| --- | --- | --- |
| Vulnerability disclosure | [`security/choice-hotels-vulnerability-disclosure.yml`](security/choice-hotels-vulnerability-disclosure.yml) | searched |
| Domain security | [`security/choice-hotels-domain-security.yml`](security/choice-hotels-domain-security.yml) | probed |
| Well-known probe table | [`well-known/choice-hotels-well-known.yml`](well-known/choice-hotels-well-known.yml) | searched (none found) |
| llms.txt | [`llms/choice-hotels-llms.txt`](llms/choice-hotels-llms.txt) | generated |

No `openapi/`, `packages/`, `mcp/`, `scopes/`, `authentication/`, `errors/`, `conventions/`, `skills/` or `arazzo/` artifacts exist, and none were created. Every one of them derives from a machine-readable contract or a published developer surface, and Choice Hotels has neither.

## Common Properties

- [Website](https://www.choicehotels.com/)
- [Corporate Site](https://www.choicehotelsdevelopment.com/)
- [Blog](https://media.choicehotels.com/press-releases) — [RSS](https://media.choicehotels.com/press-releases?pagetemplate=rss)
- [Investor Relations](https://investor.choicehotels.com/)
- [LinkedIn](https://www.linkedin.com/company/choice-hotels-international/)
- [Wikipedia](https://en.wikipedia.org/wiki/Choice_Hotels)
- [Login — Choice Connect (franchisee)](https://connect.choicehotels.com/)
- [Login — Choice Central (franchisee)](https://apps.choicecentral.com/ccweb/content/home.html)
- [Support — Guest Help Center](https://www.choicehotels.com/help)
- [Support — ChoiceNOW franchisee help portal](https://choicehotels.service-now.com/hp)
- [Terms of Use](https://www.choicehotels.com/legal/terms-of-use)
- [Privacy Policy](https://www.choicehotels.com/legal/privacy-policy)
- [Responsible Disclosure Policy](https://www.choicehotels.com/legal/responsible-disclosure)

## Maintainers

- Kin Lane — kin@apievangelist.com
