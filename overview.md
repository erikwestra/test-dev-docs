![globaliD Logo](images/giD_logo.png)

# Welcome to globaliD

globaliD is a San Francisco-based portable digital identity platform that is revolutionizing how we transact online. Our platform delivers a convenient onboarding and single sign-on experience, while empowering users to build digital reputations and to maintain consent-based control over their personal data. Our solution frees our partners from the burden of data storage and security, while still allowing them confidence in the validity of their users’ data and maintaining their compliance.

At this time, our product offerings include [globaliDConnect](FIXME), a secure user authentication and verification OAuth2 implementation, and [localiD](FIXME), a web-based identity management SDK.

# globaliDConnect

globaliDConnect is an OAuth2 protocol that mediates between your application and a user’s identity. It securely communicates your requirements for access, ensures that the user fulfils such requirements before permitting access, and allows users to explicitly consent to share personal data with you. Using globaliDConnect, users experience smooth, near-instant onboard or log in to your service by scanning a web QR code or by tapping a button on mobile.

globaliDConnect is a lightweight solution with heavyweight benefits, including:

 *   A complete onboarding solution that allows you to focus your on building your product instead of on data collection and compliance

 *   Fortifying your solution against hackers by doing away with usernames and passwords, thereby eliminating a common point of entry

 *   Protecting against fraud by permitting entry only to users who have successfully obtained the required attestations from the attesting agencies you trust

 *   A secure and seamless one-touch login experience that delights users and reduces friction to access

OpenID Connect support is coming soon.

## Learn more about globaliDConnect

 * [Demo](https://about.globalid.net/demo/sign-in/)
 * [globaliDConnect Documentation](https://openapi.globalid.net/docs/connect.html)
 * [API Documentation](https://openapi.globalid.net/index.html)
 * [NPM Package](https://www.npmjs.com/package/globalid-connect)

# localiD

localiD is a suite of software development kits (“SDKs”) that can serve as your identity stack, allowing you to focus your time and resources on your product, rather than on authentication. localiD users are not required to download the globaliD app. As a web alternative to the globaliD mobile app, it offers a white-labelled sign-in and onboarding* flow that can be embedded within your desktop website or mobile app. localiD allows your users to reserve globaliD names, to request required attestations*, and to consent to sharing personal data with you.

localiD users will not enjoy the full benefits of the globaliD solution—such as one-tap single sign-on, access to additional attestations* or use of the globaliD Wallet*—until they download the globaliD app.

The localiD solution offers:

 * Seamless user onboarding and login that slots effortlessly into your existing flow
    
 * An additional layer of security, as globaliD will have custody of the authentication credentials
    
 * Savings on your time and resources by taking care of your data security and storage needs with all user personal data retained securely in the globaliD Vault
    
 * Enhanced fraud protection, collecting user data validated by trusted third parties*

\* Feature coming soon

## Learn more about localiD

 * While this product is still in development, a [staging demo is available](https://localid-demo-staging.gidstaging.net/).
    
 * localiD Documentation.

# Attestations

globaliD Attestations are public statements, issued by an independent third party, that describe something about a user without revealing any personal information. This allows you to manage your fraud risk and to maintain compliance without having to worry about storing and protecting your users’ personal data. We encrypt all user personal data and store it in globaliD Vault, a secure store accessible only by the user or with the user’s explicit consent using a cryptographic process of symmetric and asymmetric encryption. Both globaliDConnect and localiD support required attestations for user onboarding or login.

For example, if your users must be older than the age of 18, you may require that a user have an 18+ age attestation in order to access your product or service. Through the globaliD platform, the user will be able to provide evidence of his or her age--such as a photo of the user’s government ID--to a third party, which will evaluate the evidence and determine whether the user complies with your requirements. If so, the third party will issue an 18+ attestation to the user, indicating that the user is older than 18 years and may safely access your product. The users’ data--in this case, the image of the user’s government ID--is encrypted and stored in the globaliDVault. If you need to access this image for compliance purposes, we will request the user’s consent to share it with you; if granted, you may retrieve it through an API and decrypt it using a pair of secret keys.

When users onboard through globaliDConnect or localiD*, they are guided them through the process of requesting any required attestations that they do not yet have attached to their globaliD Names, as shown in the first image below. If they already have attestations that conform to your requirements, the user will simply be asked to consent to share their attestations with you, as shown in the second image below.

**User does not yet have the required attestations:**
![Missing Attestations](images/attestations_1.png)

**User already has the required attestations:**
![Has Attestations](images/attestations_2.png)

\* localiD attestation flow coming soon

## Configuring Attestations

You may specify a set of required attestations for your users by creating an Attestation Claims Requirement Configuration (ACRC). This configuration defines the set of attestations that users are required to have in order to access your service. You may call our APIs to retrieve a [list of available attestation agencies](https://openapi.globalid.net/index.html#/Attestations/AttestationsGetAgenciesWithChildren) and a [list of available attestation types](https://openapi.globalid.net/index.html#/Attestations/AttestationsGetTypes) to assist in defining your ACRC. We will codify this configuration into an acrc_id. Please define your required attestation agencies and types, and send them to us via email in the following format:

  

### Requirement

 * **Approved Agencies**: list of attestation agencies that you trust to attest your users’ information.
 * **Timestamp**: any requirements around recency of the attestation, formatted in seconds, if possible.
 * **Required attestation types**: a list of the attestation types that a user must obtain in order to access your service as well as their logic, that is, whether a user must obtain all the attestations (i.e. “AND” conditions) or just some of them (e.g. “OR” conditions).
    

  

###### Example

An online exchange requires its users to attest their legal first and last names, and address in order to fulfil its compliance obligations. The exchange determines that they have the most confidence in information deriving from government-issued identity documents, such as an identity card, driver’s license or passport. It also determines that this information must be recent, so the user must have requested the attestation within the last week.

  

After assessing the globaliD attestation agencies that attest to these documents, the exchange determines that Au10tix and Onfido best meet their needs.

  

Further, the exchange requires that each user maintains an email on file with globaliD so that it may, in future, use the globaliD notification system to contact user via email. It determines that the Mandrill attestation agency would be the best candidate to provide this attestation.

In this case, the exchange would send globaliD the following:

  

Requirement 1

-   Approved Agencies: Au10tix, Onfido
    
-   Timestamp: 604800
    
-   Required attestation types:
    

-   legal first name and legal last name and address
    
-   Identity card number or passport number
    

  

Requirement 2

-   Approved Agencies: Mandrill
    
-   Required attestation types:
    

-   email
    

  

Once we receive these requirements, we will translate them into a simple DSL object. Using the example above:

  
  

requirements:

requirement1:

agency_app_uuid:  ["83d06855-037e-4b94-9909-ed2a1136d63d",  "0b66efb6-7ca2-4c0f-8554-c0c127f303c2"]  //  UUIDs  of  agencies  you  approved

created_at_lte:  604800  //  Seconds  in  a  week

allOf:  ["legal_first_name",  "legal_last_name",  "address"]

oneOf:  ["identity_card_number",  "passport_number"]`

  

requirement2:

agency_app_uuid:  ["c4ecd19d-a6c5-488c-904b-0e508ab221ec"]  //  UUID  of  mandril

allOf:  ["email"]
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNzg2MjI5NDcsLTE1NDA5NDg4NDEsLT
E5NDA3MzE1ODldfQ==
-->