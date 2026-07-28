# Choice Hotels (choice-hotels)

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

## Common Properties

- [Website](https://www.choicehotels.com/)
- [Corporate Site](https://www.choicehotelsdevelopment.com/)
- [Blog](https://media.choicehotels.com/press-releases)
- [Investor Relations](https://investor.choicehotels.com/)
- [LinkedIn](https://www.linkedin.com/company/choice-hotels-international/)
- [Wikipedia](https://en.wikipedia.org/wiki/Choice_Hotels)
- [Login — Choice Connect (franchisee)](https://connect.choicehotels.com/)
- [Login — Choice Central (franchisee)](https://apps.choicecentral.com/ccweb/content/home.html)

## Maintainers

- Kin Lane — kin@apievangelist.com
