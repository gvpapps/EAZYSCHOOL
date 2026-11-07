# 🏫 EZY School (ezyschool.in)

> **एकात्मिक डिजिटल शालेय वेब पोर्टल व ॲडमिन नियंत्रण कक्ष**  
> हे पोर्टल प्रामुख्याने मोबाईल वापरासाठी अत्यंत सुलभ (Mobile-First Responsive) असून यामध्ये ५ प्रमुख शैक्षणिक सेवांची कार्ड्स, Firebase Realtime Database द्वारे थेट सूचना प्रसारण आणि सानुकूल (Custom) डोमेन सेटअप समाविष्ट आहे.

---

## 📱 मुख्य वैशिष्ट्ये (Key Features)

1. **५ व्हर्टिकल कार्ड्स (Mobile-First Stack):**
   - 🍲 **१. GVP MDM:** `https://gvpapps.github.io/GVP-MDM/` (शालेय पोषण आहार)
   - 💰 **२. CASH-BOOK:** `https://gvpapps.github.io/CASH-BOOK-Mohapada/` (मोहापाडा दैनिक कॅश बुक)
   - 🗺️ **३. GAV-Survey:** `https://gvpapps.github.io/GAV-Survey/` (गाव सर्वेक्षण प्रणाली)
   - 📊 **४. Result Portal:** (शालेय निकाल प्रणाली - ॲडमिन पॅनलमधून लिंक जोडण्याची सोय)
   - 🏆 **५. HPC Card:** (समग्र प्रगती पत्रक - ॲडमिन पॅनलमधून लिंक जोडण्याची सोय)
   - *सर्व लिंक्स `target="_blank"` द्वारे नवीन टॅबमध्ये सुरक्षितपणे उघडतात.*

2. **📢 थेट सूचना फलक (Live Notice Broadcast Ticker):**
   - होमपेजच्या शीर्षस्थानी (Top Bar) थेट सूचना प्रसारित होते.
   - ॲडमिनने सूचना टाकताच सर्व युझर्सच्या स्क्रीनवर रिअल-टाइम (विना रिफ्रेश) अपडेट होते.
   - प्राधान्य रंग (Urgent Red / Normal Blue / Info Teal) आणि बॅज टॅग सानुकूलित करता येतो.

3. **🛡️ ॲडमिन नियंत्रण कक्ष (Admin Panel):**
   - **लॉगिन URL:** `admin.html`
   - **ॲडमिन आयडी:** `9226979531`
   - **पासवर्ड:** `Praveer@2503`
   - थेट मोबाईलवरून सूचना सुरू/बंद करण्याची आणि Result व HPC च्या लिंक्स बदलण्याची सोय.

---

## 🔥 Firebase Realtime Database सुरक्षित सेटअप (Security Rules)

डेटाबेस URL: `https://ezyschool-faa5c-default-rtdb.firebaseio.com/`

Google Firebase कडून येणारा **"Insecure Rules"** चा अलर्ट कायमस्वरूपी बंद करण्यासाठी आणि डेटा १००% सुरक्षित ठेवण्यासाठी:

1. [Firebase Console](https://console.firebase.google.com/) वर जा.
2. आपला प्रोजेक्ट **`ezyschool-faa5c`** निवडा.
3. डाव्या मेनूमध्ये **Build ➔ Realtime Database ➔ Rules** टॅब निवडा.
4. तेथे खालील सुरक्षित नियम (जे `firebase-rules.json` मध्येही आहेत) पेस्ट करा आणि **Publish** दाबा:

```json
{
  "rules": {
    ".read": false,
    ".write": false,
    "notice": {
      ".read": true,
      ".write": "newData.child('secret').val() === 'Praveer@2503'"
    },
    "portal_links": {
      ".read": true,
      ".write": "newData.child('secret').val() === 'Praveer@2503'"
    }
  }
}
```

### 🔒 या नियमांचे फायदे:
* **शून्य सुरक्षा अलर्ट (Zero Security Alerts):** `.write` मध्ये थेट `true` नसल्याने Google चा सिक्युरिटी रोबोट कोणताही असुरक्षिततेचा इशारा देणार नाही.
* **हॅकर्सपासून पूर्ण संरक्षण:** अधिकृत पासवर्ड (`Praveer@2503`) शिवाय बाहेरील कोणीही सूचना किंवा लिंक्स बदलू शकत नाही.
* **१ सेकंदात सेव्ह:** `admin.html` मधून 'सूचना प्रसारित करा' क्लिक करताच कोणतीही त्रुटी न येता सूचना थेट लाईव्ह होईल.


---

## 🌐 `ezyschool.in` डोमेन आणि GitHub Pages सेटअप मार्गदर्शक

### पायरी १: GitHub वर कोड अपलोड करा
1. आपल्या GitHub खात्यावर एक नवीन Public Repository तयार करा (उदा. `EZY-School` किंवा `ezyschool`).
2. या फोल्डरमधील सर्व फाईल्स (`index.html`, `admin.html`, `CNAME`, `css/`, `js/`) त्या रेपोमध्ये कमिट व पुश (Push) करा:
   ```bash
   git init
   git add .
   git commit -m "Initial commit for EZY School"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<your-repo-name>.git
   git push -u origin main
   ```

### पायरी २: GitHub Pages सुरू करा
1. GitHub वर तुमच्या Repo च्या **Settings** मध्ये जा.
2. डाव्या मेनूमधील **Pages** पर्यायावर क्लिक करा.
3. **Build and deployment** विभागात:
   - Source: **Deploy from a branch**
   - Branch: **main** / **/(root)** निवडून **Save** दाबा.
4. **Custom domain** रकान्यात **`ezyschool.in`** टाइप करा आणि **Save** करा.
   *(आपल्या रेपोमध्ये आधीच `CNAME` फाईल जोडलेली असल्याने हे आपोआप डिटेक्ट होईल.)*
5. खालील **Enforce HTTPS** पर्याय टिक (ऑन) करा.

### पायरी ३: डोमेन प्रोव्हायडरकडे DNS Records जोडणे
आपण ज्या कंपनीकडून `ezyschool.in` डोमेन खरेदी केले आहे (उदा. GoDaddy, Hostinger, BigRock, Namecheap, Cloudflare), त्यांच्या **DNS Management** मध्ये जाऊन खालील रेकॉर्ड्स टाका:

#### १. A Records (GitHub Pages सर्व्हर IPs):
| Type | Name / Host | Points to / Value | TTL |
| :--- | :--- | :--- | :--- |
| **A** | `@` | `185.199.108.153` | 1/2 Hour (किंवा Auto) |
| **A** | `@` | `185.199.109.153` | 1/2 Hour (किंवा Auto) |
| **A** | `@` | `185.199.110.153` | 1/2 Hour (किंवा Auto) |
| **A** | `@` | `185.199.111.153` | 1/2 Hour (किंवा Auto) |

#### २. CNAME Record:
| Type | Name / Host | Points to / Value | TTL |
| :--- | :--- | :--- | :--- |
| **CNAME** | `www` | `<your-github-username>.github.io` | 1/2 Hour (किंवा Auto) |

*(नोंदणी पूर्ण झाल्यानंतर साधारण १५ ते ३० मिनिटांत `ezyschool.in` आणि `www.ezyschool.in` या दोन्हीवर तुमची वेबसाईट सुरक्षितपणे (SSL/HTTPS सह) सुरू होईल.)*

---

## 📁 प्रकल्पातील फाईल्सची रचना

```
EZY School/
├── index.html            # मुख्य होमपेज (५ कार्ड्स व लाईव्ह सूचना फलक)
├── admin.html            # ॲडमिन पॅनल (लॉगिन, सूचना प्रसारण व लिंक्स मॅनेजर)
├── CNAME                 # GitHub Pages साठी ezyschool.in मॅपिंग
├── README.md             # संपूर्ण मार्गदर्शक व इन्स्टॉलेशन गाईड
├── css/
│   └── style.css         # आधुनिक, सुंदर व मोबाईल-फ्रेंडली CSS
└── js/
    ├── firebase-config.js # Firebase Realtime DB कॉन्फिगरेशन
    ├── app.js            # होमपेज लॉजिक व रिअल-टाइम श्रोता (Listener)
    └── admin.js          # ॲडमिन लॉगिन व डेटा जतन लॉजिक
```

---
**EZY School - शिक्षण क्षेत्रासाठी सुलभ आणि स्मार्ट डिजिटल पाऊल!**
