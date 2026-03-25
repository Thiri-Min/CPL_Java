# Comprehensive Guide to Authentication

## 1. What is Authentication?
Authentication is the process of **verifying the identity** of a user, device, or system. It is the gatekeeper of your application, ensuring that the person claiming to be "User A" is actually "User A."

> **Note:** Do not confuse this with **Authorization**. 
> * **Authentication:** Who are you?
> * **Authorization:** What are you allowed to do?

---

## 2. Common Methods of Authentication
Modern security relies on three "factors" of identity:

* **Something you know:** Passwords, PINs, or answers to security questions.
* **Something you have:** A physical token, a smartphone (for SMS codes/OTP), or a hardware key.
* **Something you are:** Biometrics like fingerprints, facial recognition, or retina scans.



### Popular Implementation Methods:
1.  **Single-Factor (SFA):** Just a password (least secure).
2.  **Two-Factor (2FA/MFA):** Password + a code from an app like Google Authenticator.
3.  **Passwordless:** Magic links sent via email or SMS.
4.  **Social Auth (OAuth 2.0):** Logging in via Google, Facebook, or GitHub.
5.  **Biometric:** TouchID or FaceID.

---

## 3. Authentication with Google and Facebook
Using "Social Login" relies on **OAuth 2.0** and **OpenID Connect (OIDC)**. Instead of your app handling passwords, the user authenticates with a trusted provider (Google/Facebook), and the provider sends your app a "Token" confirming the user's identity.



---

## 4. How to Set Up Google OAuth
To use Google login, you must register your application in the **Google Cloud Console**.

### Step A: Get Google Client ID and Secret
1.  Go to the [Google Cloud Console](https://console.cloud.google.com/).
2.  Create a **New Project** (or select an existing one).
3.  Navigate to **APIs & Services > OAuth consent screen**. Complete the required app info.
4.  Go to the **Credentials** tab.
5.  Click **Create Credentials** > **OAuth client ID**.
6.  Select **Web Application** as the application type.
7.  **Crucial:** Add your "Authorized redirect URIs" (e.g., `https://yourdomain.com/auth/google/callback`).
8.  Click **Create**. A modal will appear showing your **Client ID** and **Client Secret**.

### Step B: Dependencies and Security
Once you have the ID and Secret, you typically use a library (dependency) to handle the logic:
* **Node.js:** `passport-google-oauth20`
* **Python:** `google-auth-oauthlib`
* **React:** `@react-oauth/google`

**Security Warning:** Never hardcode your **Client Secret** in your frontend code or push it to GitHub. Use an `.env` file:
```env
GOOGLE_CLIENT_ID=your_id_here
GOOGLE_CLIENT_SECRET=your_secret_here
```

## 5. Get Facebook App ID and Secret

To integrate Facebook Login, you must register your application through the **Meta for Developers** portal. This provides the unique identifiers needed for the OAuth handshake.

### Step-by-Step Configuration

1.  **Log in to Meta for Developers:**
    Go to [developers.facebook.com](https://developers.facebook.com/) and log in with your Facebook account.
2.  **Create a New App:**
    * Click on **My Apps** in the top navigation bar.
    * Click the **Create App** button.
    * Select an app type (e.g., "Consumer" or "Authenticate and request data from users with Facebook Login").
3.  **Access App Settings:**
    * In the left-hand sidebar, navigate to **App Settings** > **Basic**.
    * Here you will find your **App ID** (Public).
    * Click **Show** next to **App Secret**. You will be prompted to re-enter your Facebook password for security.
4.  **Configure Facebook Login:**
    * In the sidebar, click **Add Product** and find **Facebook Login**. Click **Set Up**.
    * Select **Web** (or your specific platform).
    * Go to **Facebook Login** > **Settings** in the sidebar.
    * Locate the **Valid OAuth Redirect URIs** field and enter your application's callback URL (e.g., `https://localhost:3000/auth/facebook/callback`).
5.  **Go Live:**
    * By default, your app is in "Development" mode. To allow public users to log in, toggle the switch at the top of the dashboard to **Live**.



### Security Checklist for Facebook Credentials

* **App Secret:** Never expose this in client-side code (JavaScript). It must stay on your server.
* **Enforce HTTPS:** Facebook requires redirect URIs to use HTTPS (except for `localhost`).
* **Permissions:** If you need more than the user's name and email (like `user_photos` or `user_friends`), you must submit your app for **App Review**.

---

### Comparison Summary

| Key Component | Description |
| :--- | :--- |
| **App ID** | Your application's unique public identifier. |
| **App Secret** | A private key used to sign requests to the Facebook API. |
| **Redirect URI** | The specific URL Facebook sends the user back to after login. |