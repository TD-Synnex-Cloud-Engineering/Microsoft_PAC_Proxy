# Supported Endpoints

## General

For more information contact: Msft-SE-Azure-NA@tdsynnex.com

---
**Naming Conventions**
- A * by a request means it is not supported for reseller/end user access.
- A ^ by a request means it is not supported for CSP.
- The number in parenthesis after the name is the TD SYNNEX object identifier.  It should be provided anytime asking for information about an endpoint.
----

**Additional Information** 
- PAC Proxy treats the PATH as case sensitive. Using the wrong case will return a "no upstream API" error.
- The supported endpoints are as shown in the Postman collection.  Some Microsoft endpoints support variable scopes, you may not change the URL to a different scope.
- TD SYNNEX maintains multiple Partner Centers.  A separate credential is required for one Partner Center.
---
**Credentials**
- Credentials are created by TD SYNNEX.  They are only usable in the PAC Proxy solutions and will not work directly with Microsoft.
- A credential is only usable with one TD SYNNEX Partner Center. Creating credentials that work with multiple Partner Centers is not possible.
- A credential provides access to one or more end user tenants.
- A credential may be restricted to specific subscriptions, methods and endpoints.
---
## Partner Center
Requests made to the TD SYNNEX Partner Center, not an end user tenant.

See: [https://learn.microsoft.com/en-us/partner-center/developer/partner-center-rest-api-reference](https://learn.microsoft.com/en-us/partner-center/developer/partner-center-rest-api-reference)

| Item | Value | Equivalent Microsoft Host |
| --- | --- | --- |
| Base URL | `https://apipartnercenter.msapi.tdsynnex.com` | `https://api.partnercenter.microsoft.com` |
| Login Format | `https://login.msapi.tdsynnex.com/common/oauth2/token` | `https://login.microsoftonline.com/common/oauth2/token` |

## Graph - Partner Center
These Graph requests are made to the Entra ID tenant of the TD SYNNEX Partner Center. They are used by TD SYNNEX internal developers and ISVs creating portals for TD SYNNEX. They are not usable by resellers or end user customers.

See: [Use the Microsoft Graph API - Microsoft Graph | Microsoft Learn](https://learn.microsoft.com/en-us/graph/use-the-api)

| Item | Value | Equivalent Microsoft Host |
| --- | --- | --- |
| Base URL | `https://graph.msapi.tdsynnex.com` | `https://graph.microsoft.com` |
| Login Format | `https://login.msapi.tdsynnex.com/{{pacTenantId}}/oauth2/token` | `https://login.microsoftonline.com/{{pacTenantId}}/oauth2/token` |

## Azure Management - End User
Requests that use an access token generated using the **End User Tenant ID**, not the PAC tenant ID.

**IMPORTANT:** These endpoints use AOBO permissions granted to TD SYNNEX. If the end user customer did not provide sufficient permissions the endpoint will fail. Consider getting a service principal directly from the end user.

See: [Azure REST API reference documentation | Microsoft Learn](https://learn.microsoft.com/en-us/rest/api/azure/)

| Item | Value | Equivalent Microsoft Host |
| --- | --- | --- |
| Base URL | `https://managementazure.msapi.tdsynnex.com` | `https://management.azure.com` |
 Login Format | `https://login.msapi.tdsynnex.com/{{endUserTenantId}}/oauth2/token` | `https://login.microsoftonline.com/{{endUserTenantId}}/oauth2/token` |

## Azure Management - PAC
Requests that use an access token generated using the **PAC Tenant ID**, not the end user tenant ID.

See: [Azure REST API reference documentation | Microsoft Learn](https://learn.microsoft.com/en-us/rest/api/azure/)

| Item | Value | Equivalent Microsoft Host |
| --- | --- | --- |
| Base URL | `https://managementazure.msapi.tdsynnex.com` | `https://management.azure.com` |
 Login Format | `https://login.msapi.tdsynnex.com/{{pacTenantId}}/oauth2/token` | `https://login.microsoftonline.com/{{pacTenantId}}/oauth2/token` |

## AI Solutions and Security Insights (ASPX)
The Partner API for AI Business Solutions & Security Insights enables partners to integrate their existing CRM systems with Microsoft data, including usage signals, upsell propensity, incentive eligibility, referral opportunities, and other key insights.

See: [Partner REST API Reference for AI Business Solutions &amp; Security Insights](https://learn.microsoft.com/en-us/partner-center/insights/contact-types-api)

AI Business Solutions & Security Insights Partner Support: PXPartnerSupport@microsoft.com

**IMPORTANT:** Each Partner Center must be setup for ASPX. Carefully read the API reference before attempting to use these endpoints for the first time.

---

**ASPX data is only available to TD SYNNEX and ISVs developing tools for TD SYNNEX.**

---
| Item | Value | Equivalent Microsoft Host |
| --- | --- | --- |
| Base URL | `https://managementazure.msapi.tdsynnex.com` | `https://m365partner.microsoft.com` |
 Login Format | `https://login.msapi.tdsynnex.com/{{pacTenantId}}/oauth2/token` | `https://login.microsoftonline.com/{{pacTenantId}}/oauth2/token` |

