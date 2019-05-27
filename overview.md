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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTEwNjk1MzI5MSwtMTU0MDk0ODg0MSwtMT
k0MDczMTU4OV19
-->