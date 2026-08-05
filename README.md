## 3.1. What is the PAC Proxy Solution 
The PAC Proxy is a TD SYNNEX managed API proxy that sits between the customer or reseller application and Microsoft APIs such as Partner Center, Microsoft Graph, and Azure Management. The purpose is to allow controlled access to data that only an Indirect Provider like TD SYNNEX can utilize, without exposing access to all customers or the full Partner Center environment. 

## 3.2. Why the Solution Exists   
In the CSP model, Microsoft exposes critical billing and subscription data only to the Indirect Provider. Partner Center does not support restricting API access by tenant or subscription. Without a proxy, enabling third party or customer tools would require broad access to all customers, which TD SYNNEX does not allow. The PAC Proxy solves this by enforcing strict controls at the API layer.  

## 3.3. What the Solution Allows 
&emsp;• Access to selected Partner Center, Microsoft Graph, and Azure Management API requests. 

&emsp;• Access limited to specific tenant IDs and subscription IDs approved by TD SYNNEX. 

&emsp;• Access limited to specific API paths and request methods, primarily GET requests. 

&emsp;• Use of TD SYNNEX credentials instead of customer or reseller service principals. 

&emsp;• Integration with customer ERP, billing, reporting, or third-party ISV tools. 
 
All access is explicitly approved per credential. Requests not approved are blocked by the proxy.  

## 3.4. What the Solution Does Not Allow 
&emsp;• No access to APIs that return data for all TD SYNNEX customers. 

&emsp;• No access to requests that cannot be scoped to a tenant or subscription. 

&emsp;• No access to subscriptions not purchased through TD SYNNEX. 

&emsp;• No unrestricted Partner Center access. 

If a subscription is transferred away from TD SYNNEX, the proxy access stops immediately. 

## 3.5. How the Solution Works end to end 
&emsp;• The customer or reseller application points to TD SYNNEX PAC Proxy endpoints instead of Microsoft endpoints. 

&emsp;• The application authenticates using a TD SYNNEX issued client ID and secret. 

&emsp;• TD SYNNEX validates the token and applies throttling if required. 

&emsp;• The proxy extracts the tenant ID and subscription ID from the request. 

&emsp;• The proxy checks the request against the approved list for that credential. 

&emsp;• If approved, the proxy forwards the request to Microsoft using TD SYNNEX provider credentials. 

&emsp;• Microsoft processes the request and returns the response. 

&emsp;• TD SYNNEX returns the response unchanged to the caller. 

Errors returned may come from TD SYNNEX validation or directly from Microsoft.  

## 3.6. What the Reseller / End Customer Experiences 
&emsp;• No direct access to TD SYNNEX Partner Center. 

&emsp;• No need to manage provider level permissions. 

&emsp;• One integration point for multiple tenants or subscriptions. 

&emsp;• Ability to use third party tools that previously did not work in CSP. 

All activity appears in logs under a TD SYNNEX service principal due to how Microsoft APIs operate, with traceability handled by TD SYNNEX internally.  
