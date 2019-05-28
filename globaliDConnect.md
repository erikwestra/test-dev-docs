![globaliD Logo](images/giD_logo.png)

# globaliDConnect
Seamless, secure and trusted user onboarding and login

[Overview](#overview)
&nbp;[Web/Mobile Support](#webmobile-support)
**  
**

[Overview  2](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.yhatfolndvla)

[Web/Mobile Support  2](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.ixvqjj85g7mx)

[Attestation Requirements  2](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.f0pf9rfavyoa)

[Getting Started  3](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.eitdkwprd0qg)

[Redirect URL  3](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.q86ztdt1gqy)

[Attestation Consent Request Configuration (ACRC)](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.ro16ehbxwxm5) 3

[Specifications](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.2dhbr65mnxr) 4

[URL format](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.la5tvbxyjmfa) 4

[URl parameters](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.82jdz0hhxx8q) 5

[Response handling](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.biuxnfb00fmd) 6

### Overview

globaliDConnect is an OAuth2 protocol that mediates between your application and a user’s identity. It securely communicates your requirements for access, ensures that the user fulfils such requirements before permitting access, and allows users to explicitly consent to share personal data with you. Using globaliDConnect, users experience smooth, near-instant onboard or log in to your service by scanning a web QR code or by tapping a button on mobile.

globaliDConnect is a lightweight solution with heavyweight benefits, including:

 * A complete onboarding solution that allows you to focus your on building your product instead of on data collection and compliance.
    
 * Fortifying your solution against hackers by doing away with usernames and passwords, thereby eliminating a common point of entry.
    
 * Protecting against fraud by permitting entry only to users who have successfully obtained the required attestations from the attesting agencies you trust.
    
 * A secure and seamless one-touch login experience that delights users and reduces friction to access.

### Web/Mobile Support

On web, globaliDConnect displays a QR code that the user may scan to onboard or to log in. When opening globaliDConnect on mobile, the QR code is hidden, instead displaying a button to open the globaliD App, as well as links to download the globaliD App from the Play or App stores.

### Attestation Requirements

globaliDConnect allows you to customize the specific attestations required for users to access your services. You may define the types of personal data that you will require users to attest, as well as the attesting agencies and freshness of any attestations that you will accept.

When users onboard through globaliDConnect, the globaliD App will guide them through the process of requesting any required attestations that they do not yet have attached to their globaliD Names, as shown in the first image below. If they already have attestations that conform to your requirements, the user will simply be asked to consent to share their attestations with you, as shown in the second image below.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NDEwNjgzMTIsMTU0MTU5MDAsLTIwOD
g3NDY2MTJdfQ==
-->