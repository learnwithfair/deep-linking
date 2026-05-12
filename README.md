# Deep Linking Guide (Simple & Clear for Everyone)

[![Youtube][youtube-shield]][youtube-url]
[![Facebook][facebook-shield]][facebook-url]
[![Instagram][instagram-shield]][instagram-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

Thanks for visiting my GitHub account!


## 🧩 1. What is Deep Linking?

Deep linking means:

👉 A URL can open a **specific screen inside your mobile app**.

**Example:**

```
https://yourdomain.com/product/123
```

* ✅ If app is installed → opens Product page in app
* ❌ If not installed → opens in browser

---

## ⚙️ 2. How It Works (Easy Flow)

```
User clicks link
        ↓
Mobile checks domain (.well-known files)
        ↓
If verified → Open App
Else → Open Browser
        ↓
App reads URL → Opens correct screen
```

---

## 👨‍💻 3. Backend Developer (Your Job)

### Step 1: Create Folder

```
public/.well-known/
 ├── apple-app-site-association   (iOS)
 └── assetlinks.json              (Android)
```

---

### Step 2: Set Proper Permissions (Recommended)
SSH into server and run:
```
ssh userName@yourServerIP
chmod -R 755 public/.well-known
```
### Step 3: Important Rules

* ✅ Must be inside `.well-known` folder
* ✅ Must be accessible via browser
* ✅ Must use HTTPS

Test:

```
https://yourdomain.com/.well-known/assetlinks.json
https://yourdomain.com/.well-known/apple-app-site-association
```

---

### Step 3: iOS File

⚠️ Important:

* No `.json` extension

```
apple-app-site-association
```

---

### Step 4: Android File

```
assetlinks.json
```

👉 Content will be provided by app developer

---

### ✅ Backend Summary

👉 Your job is ONLY:

* Create `.well-known` folder
* Add 2 files
* Make them accessible
* Ensure HTTPS

👉 Done ✅

---

## 📱 4. Flutter / App Developer Job

Flutter dev actually does ONLY 2 things:

### 1. Read the URL

Example:

```
https://yourdomain.com/product/1
```

### 2. Open the screen

```
/product/1 → ProductScreen(1)
```

---

### 🧠 Simple Logic

```
if (url contains 'product')
    open Product Page
```

👉 That’s it 😄

---

## 🧪 5. Testing

### Android

```
adb shell am start -a android.intent.action.VIEW -d "https://yourdomain.com/product/1"
```

### iOS

* Open link in Safari
* Or open from Notes app

---

## ❌ 6. Common Problems

* HTTPS not enabled ❌
* Wrong SHA256 ❌
* Wrong Bundle ID ❌
* Files not accessible ❌

---

## 📋 7. Production Checklist

* [ ] HTTPS enabled
* [ ] `.well-known` folder exists
* [ ] Both files accessible
* [ ] Android works
* [ ] iOS works
* [ ] App opens correct screen

---

## 🎯 8. Final Understanding

👉 Backend = verifies domain
👉 App = opens screen

---

## 😄 9. Simple Truth

Flutter dev may say it’s complex…

But actually:

```
URL আসে → ID নেয় → Screen open করে
```

👉 That’s all 🎉

---

## 🏁 Conclusion

If both backend and app are correctly configured:

✅ Deep linking will work perfectly

---


## 📝 Simple Note

Deep linking is actually very simple.

- Backend just verifies the domain using `.well-known` files  
- App just reads the URL and opens the correct screen  

That’s it.

No need to overcomplicate —  
finish the work quickly and enjoy your tea ☕😄

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
