# Elead (elead-crm)

Elead (eLEAD / Elead CRM) is an automotive dealership CRM for sales, BDC, and service, now part of CDK Global. Elead exposes a set of **partner-gated Vehicle Sales REST APIs** - Sales Opportunities, Sales Customers, Sales Activities, and Product Reference Data - published through the **CDK Fortellis Automotive Commerce Exchange**. The APIs let certified software providers and dealers search and manage prospects/customers, sales opportunities (leads), vehicles of interest and trade-ins, sales teams, and activities inside Elead CRM.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/elead-crm/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/elead-crm/refs/heads/main/apis.yml)

## Access Model (Important)

This is **not an open, self-service API**. Access is partner/certification-gated through Fortellis:

1. Register as a Fortellis user and create a Fortellis **solution** to generate `client_id` and `client_secret`.
2. A **dealership activates a subscription** for your app against their Elead CRM instance, which supplies the per-dealer `Subscription-Id`.
3. Every request carries `client_id`, `client_secret`, `Subscription-Id`, and a `Request-Id` correlation header.

There is no public free tier or self-serve production signup, and pricing is handled through CDK/Fortellis partner agreements (contact sales). There is **no public WebSocket API** - all surfaces are request/response REST over HTTPS on the Fortellis gateway (`https://api.fortellis.io`) under the `/sales/v1/elead` path prefix.

## Tags

- CRM
- Automotive
- Dealership
- Sales
- Leads
- Fortellis
- CDK Global

## Timestamps

- **Created:** 2026-07-10
- **Modified:** 2026-07-10

## APIs

### Elead Sales Opportunities API

Search and retrieve existing sales opportunities (leads) by date range, delta date, or customer Id, and create new opportunities for existing customers. Manage vehicles of interest and trade-ins, add comments, reassign the primary salesperson or BDC agent, add/remove sales-team members, update sub-status and sales steps, and send emails that log a corresponding activity.

- **Documentation:** [Elead Sales Opportunities connector](https://learn.microsoft.com/en-us/connectors/cdkeleadsalesopportunities/)
- **API Reference:** [Fortellis spec](https://apidocs.fortellis.io/specs/3c6d6b40-7215-4a81-a087-4f956bb36ec9)
- **Base URL:** `https://api.fortellis.io/sales/v1/elead`

### Elead Sales Customers API

Manage prospect and customer records inside Elead CRM. Create a customer (returning the Elead customer Id), update contact details, retrieve a customer by Id, search by first name, last name, phone number, or email address, and retrieve a customer's owned vehicles.

- **Documentation:** [Elead Sales Customers connector](https://learn.microsoft.com/en-us/connectors/cdkeleadsalescustomers/)
- **API Reference:** [Fortellis spec](https://apidocs.fortellis.io/specs/ba092364-accc-4ad9-865f-fac51c34cdb1)
- **Base URL:** `https://api.fortellis.io/sales/v1/elead`

### Elead Sales Activities API

Create scheduled and completed sales activities (including emails and appointments) tied to an opportunity, complete activities and record outcomes, and query sales-activity history with comments. **Endpoints for this API are modeled** from CDK/Elead product descriptions rather than a confirmed public reference - see `review.yml` (`endpointsModeled`).

- **Documentation:** [CDK CRM API overview](https://www2.cdkglobal.com/api-solutions-crm)
- **API Reference:** [Fortellis API directory](https://apidocs.fortellis.io/)
- **Base URL:** `https://api.fortellis.io/sales/v1/elead`

### Elead Product Reference Data API

Helper API that provides reference/lookup data for the other Vehicle Sales APIs - opportunity sources and sub-sources by company and up type, opportunity statuses, sales steps, employee positions, employees by position, sender ("from") email addresses, and a vehicle catalog of classes, years, makes, models, and trims.

- **Documentation:** [Elead Product Reference Data connector](https://learn.microsoft.com/en-us/connectors/cdkeleadproductreferencedata/)
- **API Reference:** [Fortellis spec](https://apidocs.fortellis.io/specs/8bbbe60f-b382-4315-8d19-ba48a64b2ab3)
- **Base URL:** `https://api.fortellis.io/sales/v1/elead`

## Artifacts

- [OpenAPI](openapi/elead-crm-openapi.yml) — documented Opportunities / Customers / Reference Data operations, with Activities operations flagged `x-endpoints-modeled`.
- [Plans](plans/elead-crm-plans-pricing.yml) — partner/contact-sales access model.
- [Rate Limits](rate-limits/elead-crm-rate-limits.yml) — 100 calls / 60s per connection (per CDK connector metadata).
- [FinOps](finops/elead-crm-finops.yml) — contract/partner-agreement cost view.

## Common Properties

- [Website](https://www.eleadcrm.com)
- [LinkedIn](https://www.linkedin.com/company/cdk-global)
- [Documentation](https://apidocs.fortellis.io/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
