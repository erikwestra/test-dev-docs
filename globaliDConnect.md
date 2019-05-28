![globaliD Logo](images/giD_logo.png)

# globaliDConnect
Seamless, secure and trusted user onboarding and login

[Overview](#overview)
&nbsp;&nbsp;&nbsp;&nbsp;[Web/Mobile Support](#webmobile-support)
&nbsp;&nbsp;&nbsp;&nbsp;[Attestation Requirements](#attestation-requirements)
[Getting Started](#getting-started)
&nbsp;&nbsp;&nbsp;&nbsp;[Redirect URL](#redirect-url)
&nbsp;&nbsp;&nbsp;&nbsp;[Attestation Consent Request Configuration (ACRC)](#attestation-consent-request-configuration-acrc)
[Specifications](#specifications)
&nbsp;&nbsp;&nbsp;&nbsp;[URL Format](#url-format)
&nbsp;&nbsp;&nbsp;&nbsp;[URI Parameters](#uri-parameters)
&nbsp;&nbsp;&nbsp;&nbsp;[Response Handling](#response-handling)

## Overview

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

| User does not yet have the required attestations | User already has the required attestations |
| ------------------ | ------------------ |
| ![Missing Attestations](images/attestations-1.png) | ![Has Attestations](images/attestations-2.png) |

## Getting Started

The [specifications](#specifications) below are provided for your information. Once you’re ready to get started, please email us at [hello@global.id](mailto:hello@global.id) with the following information:
 * [Redirect URL](#redirect-url).
 * [Attestation Consent Request Configuration (ACRC)](#attestation-consent-request-configuration-acrc) if you would like to limit access to users who have attested specific information.
 * 
Once we receive, review and approve this information, we will provide you with a `client_id`, `client_secret`, and `acrc_id`, which you may use to load the globaliDConnect authentication client and obtain access tokens or authorization codes. We will send these to you via email in a password-protected encrypted archive.

### Redirect URL

This is the redirect URL to which users will be returned following successful onboarding or login. It should be in HTTPS format. You may provide multiple URLs (e.g. to different environments) if you wish. We will provide a unique `client_id` and `client_secret` for each environment.

### Attestation Consent Request Configuration (ACRC)

This configuration defines the set of attestations that users are required to have in order to access your service. You may call our APIs to retrieve a [list of available attestation agencies](https://openapi.globalid.net/index.html#/Attestations/AttestationsGetAgenciesWithChildren) and a [list of available attestation types](https://openapi.globalid.net/index.html#/Attestations/AttestationsGetTypes) to assist in defining your ACRC. We will codify this configuration into an `acrc_id`. Please define your required attestation agencies and types, and send them to us via email in the following format:

#### Requirement

 * **Approved Agencies**: list of attestation agencies that you trust to attest your users’ information.
 * **Timestamp**: any requirements around recency of the attestation, formatted in seconds, if possible.
 * **Required attestation types**: a list of the attestation types that a user must obtain in order to access your service as well as their logic, that is, whether a user must obtain all the attestations (i.e. “AND” conditions) or just some of them (e.g. “OR” conditions)

#### Example

An online exchange requires its users to attest their legal first and last names, and address in order to fulfil its compliance obligations. The exchange determines that they have the most confidence in information deriving from government-issued identity documents, such as an identity card, driver’s license or passport. It also determines that this information must be recent, so the user must have requested the attestation within the last week.

After assessing the globaliD attestation agencies that attest to these documents, the exchange determines that Au10tix and Onfido best meet their needs.

Further, the exchange requires that each user maintains an email on file with globaliD so that it may, in future, use the globaliD notification system to contact user via email. It determines that the Mandrill attestation agency would be the best candidate to provide this attestation.

In this case, the exchange would send globaliD the following:

** Requirement 1**

 * Approved Agencies: Au10tix, Onfido
 * Timestamp: 604800
 * Required attestation types:
    * legal first name and legal last name and address
    * Identity card number or passport number

**Requirement 2**

 * Approved Agencies: Mandrill
 * Required attestation types:
   * email

# Specifications

globaliDConnect is an OAuth2 implementation for the globaliD platform and globaliD App that supports user authentication with conditional attestation requirements.

  

To use globaliDConnect, the globaliDConnect authentication client must be loaded via a [URL](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.la5tvbxyjmfa) with the correct [URI parameters](https://docs.google.com/document/d/1H3mJmgwgvGmzJZWCqZZvTkcH5pj96HkGwta6PLRNJHo/edit#heading=h.82jdz0hhxx8q). The client can be loaded in a browser window.

## URL format

  

https://auth.globalid.net

###### ?client_id=<client_id>

&response_type=<response_type>

&scope=<scope>

&redirect_uri=<redirect_uri>

&web=<true | null>

  

#### Example URL

[https://auth.globalid.net?client_id=9e54b4bd-eb2f-442b-b8da-666387c15b7c&response_type=code&scope=public&redirect_uri=https%3A%2F%2Fexample.com%2Flogin%2F](https://auth.globalid.net?client_id=9e54b4bd-eb2f-442b-b8da-666387c15b7c&response_type=code&scope=public&redirect_uri=https%3A%2F%2Fexample.com%2Flogin%2F)

## URl parameters

### Web View

Key: web=true

This parameter prevents the widget from displaying the mobile view, and is useful when loading globaliDConnect inside smaller windows.

### Response types

Key: response_type

2 response types are available for use:

-   Implicit token: token
    
-   Authorization code: code
    

#### Implicit Token

This response type contains the user’s access token, which can be used directly with our API. For security reasons, this response type is only available when globaliDConnect is initiated inside a window. The token is returned by redirecting to the redirect_uri, with the token attached to the URL.

##### Response format

<redirect_uri>#token=<token>

#### Authorization code

##### Response format

<redirect_uri>&grant_type=authorization_code&code=<code>

### Scope

Key: scope

Supported scopes:

-   public
    

### Redirect URL

Key: redirect_uri

This parameter is the callback URL set on your client, and serves as an additional check when initiating an authorization request.

### Attestation Consent Request Configuration

Key: acrc_id

A uuid representing an attestation consent request configuration. An attestation consent request configuration determines what set of attestations are required by the user to be able to authenticate with GlobaliD Connect.

## Response handling

### Success Response

Upon successful login, globaliDConnect both redirects back to the redirect URL saved on the app and appends relevant information to it. Depending on the response_type we have 2 URL formats:

1.  ##### Implicit token: `response_type=token`
    

<redirect_uri>#token=<token>

2.  ##### Authorization code: `response_type=code`
    

<redirect_uri>?grant_type=authorization_code&code=<code>

##### Examples for getting the access token with the authorization code

###### 

----------

###### BASH Example

  

curl

-d "client_id=<client_id>"

-d "client_secret=<client_secret>"

-d "redirect_uri=<redirect_uri>"

-d "code=<code>"

-d "grant_type=authorization_code"

-H "Content-Type: application/x-www-form-urlencoded"

-X POST https://api.globalid.net/v1/auth/token

###### NodeJS

axios.request({

url: '/auth/token',

baseURL: 'https://api.globalid.net',

headers: { 'Content-Type': 'application/x-www-form-urlencoded' },

data: {

client_id: <client_id>,

client_secret: <client_secret>,

redirect_uri: <redirect_uri>,

code: <code>,

grant_type: 'authorization_code'

}

})

----------

### Error Response

<redirect_uri>?error=<error_code>&error_description=<>

  

The error_description string is URI encoded.

  

Error Code

Error Description

access_denied

The resource owner denied the request
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg4MzM2MjU3LDE1NDE1OTAwLC0yMDg4Nz
Q2NjEyXX0=
-->