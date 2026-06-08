# Deep Linking Guide

[![Youtube][youtube-shield]][youtube-url]
[![Facebook][facebook-shield]][facebook-url]
[![Instagram][instagram-shield]][instagram-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

Thanks for visiting my GitHub account!

---

## 1. What is Deep Linking?

Deep linking allows a URL to open a specific screen inside a mobile application, rather than simply launching the app's home screen or falling back to a browser.

**Example:**

```
https://yourdomain.com/product/123
```

- If the app is installed — opens the Product screen directly inside the app
- If not installed — opens the URL in the browser

---

## 2. How It Works

```
User clicks link
        |
Mobile OS checks domain verification files (.well-known)
        |
If verified --> Open App
Else        --> Open Browser
        |
App reads the URL and navigates to the correct screen
```

---

## 3. Backend Developer Responsibilities

### Step 1: Create the Folder Structure

```
public/.well-known/
 ├── apple-app-site-association   (iOS)
 └── assetlinks.json              (Android)
```

---

### Step 2: Set Proper Permissions

SSH into the server and run:

```bash
ssh userName@yourServerIP
chmod -R 755 public/.well-known
```

---

### Step 3: Verify Accessibility

Both files must meet the following requirements:

- Must reside inside the `.well-known` folder
- Must be accessible via browser (no authentication walls)
- Must be served over HTTPS

Test the URLs:

```
https://yourdomain.com/.well-known/assetlinks.json
https://yourdomain.com/.well-known/apple-app-site-association
```

---

### Step 4: iOS File

Note the file for iOS has **no `.json` extension**:

```
apple-app-site-association
```

---

### Step 5: Android File

```
assetlinks.json
```

The content for this file will be provided by the app developer, as it contains the app's SHA256 certificate fingerprint and package name.

---

### Backend Summary

The backend developer's responsibility is limited to:

- Creating the `.well-known` folder
- Adding the two verification files
- Ensuring both files are publicly accessible
- Confirming the domain uses HTTPS

---

## 4. Flutter / App Developer Responsibilities

The app developer's job is straightforward and involves two tasks:

### 1. Read the incoming URL

```
https://yourdomain.com/product/1
```

### 2. Navigate to the appropriate screen

```
/product/1  -->  ProductScreen(id: 1)
```

**Core logic:**

```dart
if (url.contains('product')) {
    openProductPage();
}
```

---

## 5. Testing

### Android

```bash
adb shell am start -a android.intent.action.VIEW -d "https://yourdomain.com/product/1"
```

### iOS

- Open the link in Safari
- Or open it from the Notes app

---

## 6. Common Issues

- HTTPS not enabled on the server
- Incorrect SHA256 fingerprint in `assetlinks.json`
- Wrong Bundle ID or App ID
- Verification files not publicly accessible

---

## 7. Production Checklist

- [ ] HTTPS enabled on the domain
- [ ] `.well-known` folder exists and is accessible
- [ ] Both `assetlinks.json` and `apple-app-site-association` are reachable via browser
- [ ] Android deep linking tested and working
- [ ] iOS deep linking tested and working
- [ ] App navigates to the correct screen upon link click

---

## 8. Summary

- **Backend** — Verifies domain ownership using `.well-known` files
- **App** — Reads the URL and navigates to the correct screen

When both sides are correctly configured, deep linking works reliably and seamlessly.

---

## A Note on Complexity

Deep linking is often perceived as complicated, but the underlying concept is simple. The backend verifies the domain; the app reads the URL and opens the right screen. Following the steps in this guide, the entire setup can be completed quickly and without any ambiguity.

---

## Author

Developed and maintained by [MD. Rahatul Rabbi](https://github.com/learnwithfair).

---

## Follow

[<img src='https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/github.svg' alt='github' height='30'>](https://github.com/learnwithfair)
[<img src='https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/facebook.svg' alt='facebook' height='30'>](https://www.facebook.com/learnwithfair/)
[<img src='https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/instagram.svg' alt='instagram' height='30'>](https://www.instagram.com/learnwithfair/)
[<img src='https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/youtube.svg' alt='YouTube' height='30'>](https://www.youtube.com/@learnwithfair)

---

<!-- MARKDOWN LINKS -->
[youtube-shield]: https://img.shields.io/badge/-Youtube-black.svg?style=flat-square&logo=youtube&color=555&logoColor=white
[youtube-url]: https://youtube.com/@learnwithfair
[facebook-shield]: https://img.shields.io/badge/-Facebook-black.svg?style=flat-square&logo=facebook&color=555&logoColor=white
[facebook-url]: https://facebook.com/learnwithfair
[instagram-shield]: https://img.shields.io/badge/-Instagram-black.svg?style=flat-square&logo=instagram&color=555&logoColor=white
[instagram-url]: https://instagram.com/learnwithfair
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/company/learnwithfair

#learnwithfair #rahtulrabbi #rahatul-rabbi #learn-with-fair
