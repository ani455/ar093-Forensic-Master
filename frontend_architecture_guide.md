# 🚀 Master Frontend Architecture & Forensic Guide: Project `ar093`

This comprehensive document serves as the absolute "Source of Truth" for the application's internal mechanics.

---

## 🏗️ 1. Core DNA & System Stack
- **Engine**: Vue 3 (Composition API) + Pinia State Management.
- **UI**: Vant UI (Optimized mobile components).
- **Network**: Axios Wrapper (with Auto-token injection).

---

## 🧠 2. JS CORE LOGIC ENGINE (THE "BRAIN")
The application logic is split into hashed modules for speed.

- **Main Entry (`/assets/js/index-74618ce8.js`)**: Handles bootstrapping, routing, and PWA Service Worker registration.
- **Logic Hub (`/assets/js/common.modules-5cfe2cf4.js`)**: This is the heart. It contains:
    - **Axios Interceptors**: Globally intercepts 401 (Logout) and 4001 (Recharge Lock).
    - **Auth Store**: Pinia store managing `token` and `userInfo`.
    - **Global Hooks**: Logic for opening sidebars and common modals.
- **Feature Chunks**: 
    - `page-wallet-*`: Finance logic.
    - `page-saasLottery-*`: Game engines.

---

## 🎨 3. CSS DESIGN SYSTEM & THEME OVERHAUL
Styles are non-hardcoded. They use a global token system located in `/assets/css/common-*.css`.

### **Cascading Priority:**
1.  **`:root` Variables**: Overriding these changes 100% of the UI.
2.  **Vant UI Overrides**: Custom `.van-button--primary` classes.
3.  **Scoped Components**: Micro-adjustments in JS-injected styles.

### **Key Theme Tokens:**
- `--van-primary-color`: The "Brand" color (Current: Purple).
- `--van-background-2`: Dark-mode surfaces.
- `--norm_green-color`: Positive balance/Win states.
- `--norm_red-color`: Loss/Alert states.

---

## 💎 4. SAV (STRONGBOX) VIRTUAL VAULT MECHANICS
The Strongbox is a "Balance Buffer" managed by the `page-main-StrongBox-*.js` module.

### **The Logic Flow:**
1.  **Transfer-In**: Calls `/api/Wallet/TransferToStrongbox`. It subtracts `availableBalance` and adds to `savBalance`.
2.  **Transfer-Out**: Calls `/api/Wallet/TransferFromStrongbox`.
3.  **Auto-Interest**: Some versions check the `sav_interest` flag in `GetUserInfo`.
4.  **Lock Mechanism**: Client-side validation prevents transfers if the user has an active withdrawal request pending.

---

## 🔐 5. API SECURITY & SIGNATURE LAYER
Every outgoing request is signed to prevent "Replay Attacks" and "Balance Injection".

- **The `Eo` Function**: `MD5(payload_sorted + internal_salt)`.
- **Headers**: 
    - `Authorization`: Bearer Token (Stored in LocalStorage).
    - `signature`: The hashed string.
    - `timestamp`: Server-synced Unix time.
- **Modification Rule**: If you change a parameter (e.g. `amount`) in the browser console, the server will reject it unless you re-sign the payload using the `Eo` function.
---

## 🖼️ 6. MASTER UI ASSET REGISTRY (VISUAL ROADMAP)
A guide to replacing branding elements without recompiling the entire JS bundle.

### **A. Branding & Core Identity (`/assets/images/`)**
- `logo-*.webp`: Main navigation bar logo.
- `avatar-*.png`: Default user profiles in Account Tab.
- `bg-account-*.png`: Profile header background.

### **B. Game & Activity Visuals**
- `/assets/js/page-activity-*.js`: Contains image URLs for "First Recharge" and "Bonus" banners.
- `/assets/images/games/`: Icons for JILI, PG, and Specialized SaaS platforms.

### **C. Iconography (SVG Sprite System)**
Located in `index.html` within the `<svg>` tag. 
- **`icon-91-gold`**: Coin/Balance icon.
- **`icon-91-recharge_btn`**: The primary deposit button.
- **`icon-91-turntable`**: Rewards wheel trigger.

---

## 🔐 7. API SECURITY & SIGNATURE LAYER
---

## 📡 6. MASTER API REGISTRY (PRODUCTION)

### **Identity & Wallet**
- `POST /api/User/Login` - Authentication.
- `GET /api/User/GetUserInfo` - The "Sync" call for balance/SAV data.
- `POST /api/Wallet/SubmitRecharge` - Gateway redirector.
- `POST /api/Wallet/Withdraw` - Cashout execution.

### **Game & Lottery**
- `POST /api/Game/GetGameUrl` - 3rd-party game launcher (Gatekeeper).
- `POST /api/Lottery/WinGoBet` - Betting engine submission.
- `GET /api/Lottery/GetTrend` - Chart rendering data.

---

## 🛠️ 7. PATCHING STRATEGY (QUICK REFERENCE)

1.  **Bypass Recharge**: Patch `common.modules` to ignore server `code 4001`.
2.  **Change Theme**: Edit CSS variables in `common.css`.
3.  **Modify Game History**: Intercept `GetRecordPage` and spoof results in the result parser function.
4.  **Auto-Betting**: Hook into the `WinHook` provider in the WinGo module.

---
**Status**: `Production Ready / Master Forensic Edition`
