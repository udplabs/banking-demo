# ecommerce-demo

An example ecommerce site showcasing Okta's new Financial Grade Identity (FGI)
functionality. It uses pushed authorization requests (PAR) to securely
transmit transaction details for appoval via a custom mobile push notification.

## Setup

**Local Environment**

Make a copy of `.env.sample` and save it as `.env` in the `app` folder.
Create a new regular web application in your CIC tenant. This will be the plant
store. Fill in the relevant details from your new app into your `.env` file.

```
# the ecommerce app
APP_URL=http://localhost:8080
ISSUER_BASE_URL=https://tenant1.us.auth0.com
CLIENT_ID=
CLIENT_SECRET=
AUDIENCE=https://my-audience-url
SCOPE=openid profile email offline_access read:balance
PVT_KEY="-----BEGIN RSA PRIVATE KEY-----\n   \n-----END RSA PRIVATE KEY-----\n"
```

The `PVT_KEY` value is available in the lab guide.

Next, create a new API service in your tenant with the following details:

* Name: Atko Green API Services
* Identifier: https://my-audience-url
* Create one scope called `read:balance`

**Bank Tenant Account**

Sign up for an account in the [Atko Bank Demo](https://bank.atko.rocks/).
Click on `Sign Up/Login` in the upper right hand corner. During the signup
process, you will be required to download and enroll the custom mobile app to
receive push notifications.

* iOS users, get the app via [TestFlight](https://testflight.apple.com/join/cKEZOvSC)
* Android users, download the [.apk file](http://localhost:8080) and side load it

### Install Dependencies

Install the dependencies by running:

```bash
cd app
npm install
```

### Running the Demo

To run the demo locally:

```bash
cd app
npm run dev
```

This will start a development server on `http://localhost:8080`.
