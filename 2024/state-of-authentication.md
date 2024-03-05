# The State of Authentication: Are Passwords Dead Yet?

## Brief history

- The way of saying things was the first way of checking for access
- Tokens: physical tokens at first
- Personal identification numbers (pin numbers, cards, etc.)
- Username / password
- SSO / OpenID connect
- Multifactor authentication: SMS (great vector of attack). push notification, access code
- Invisible MFA: automated zero trust security model

## Fine-grained access control

- Role based access control
- Attributes access control: certain network, certain time of day
- Relationship based access

##  Zero trust security model
- Prove you have access
- Different type of access depending on the resource requested
- Never trust, always verify
- Complex to set up and manage

## OAuth2 authentication flows

- OpenID connect, layer on top of OAuth2
- Number of different flows depending on the scenario you have
- Device flow authentication: interact with physical devices
  - Request authentication server, start a device flow login
  - Login at the URL provided, complete the login flow
  - Fridge is pulling the auth server to check if there is a token yet
  - Scan the QR code, logs in
  - Session is done, user is logged in
  - Password is not seen at any moment

## Webauthn and passkeys

- Fishing proof
- Provide a secure and an easy way to log in without fishing attacks
- User uses a laptop, authentication server say "I don't know you"
- Generate a public/private key pair, signs it and returns it with the public key
  - Use any stuff able to do cryptographic and sign it (UB key, facial recognition, thumbs print, etc)
  - The public/private key is generated for a specific domain
- AuthN server stores the public key
- Next time, user send privates key, AuthN check with the public key it has stored
- You can synchronize the private keys between devices
- Passkeys: sharing private keys between devices
- Passkey can present themselves as QR code, phone has the private key so user can scan it and log in in another device (laptop) that does not have the private key.

## Personal devices authorisation services:

- Check site and playground on [Webauthn.io](https://webauthn.io/).