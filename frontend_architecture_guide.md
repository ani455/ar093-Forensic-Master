# 🏆 Master Frontend Forensic Architecture: Project `ar093` (Ultra High-End Edition)

This is the definitive "Blueprint of Power" for Project `ar093`. It decodes every hashed chunk, CSS variable, and API protocol for total programmatic control.

---

## 🏗️ 1. ARCHITECTURAL DNA
- **Engine**: Vue 3 (Reactive Composition API).
- **State**: Pinia (Centralized Store for Balance, Auth, and Game State).
- **Styling**: Atomic CSS Variables (Van UI & Custom Hybrid).
- **Sync**: WebSocket Publish/Subscribe (For real-time results).

---

## 🧠 2. JS LOGIC CHUNK REGISTRY (THE BRAIN MAP)
Logical behavior is strictly siloed. Use this table to find the "Kill Switch" for any feature.

| Subsystem | Primary JS Chunk | Purpose & Critical Logic |
| :--- | :--- | :--- |
| **Global Core** | `common.modules-5cfe2cf4.js` | **The Master Brain**. Interceptors (4001, 401), Global Stores, and API Wrappers. |
| **Identity** | `page-login-index.*.js` | Handles Session Tokens & Login flow. |
| **Wallet Hub** | `page-wallet-Recharge-*.js` | Payment Gateway mapping and Amount validation. |
| **Cashout** | `page-wallet-Withdraw-*.js` | Binding checks (Bank/Phone) and Withdrawal triggers. |
| **WinGo Engine**| `page-saasLottery-VideoWinGo-*.js` | Real-time betting logic, websocket result parser. |
| **SAV Controller**| `page-main-StrongBox-*.js` | Balance transfer logic (Wallet <-> Strongbox). |
| **Activity** | `page-activity-ActivityDetail-*.js`| Banner image rendering and reward redemption. |
| **VIP Loyalty** | `page-vip-index.*.js` | VIP progression and level-based reward tiers. |

---

## 🎨 3. CSS DESIGN TOKENS (UI OVERHAUL ENGINE)
Modification of branding starts and ends here. Primary file: `/assets/css/common-05d2aa17.css`.

### **Variable Overrides for Instant Branding Upgrade:**
| Variable | Default Hex | Impact |
| :--- | :--- | :--- |
| `--van-primary-color` | `Purple/Violet`| **Dominant Brand Color** (Buttons, Tabs, Active States). |
| `--norm_green-color` | `#47ba7c` | "Profit" indicators and Win messages. |
| `--norm_red-color` | `#fc5050` | "Loss" indicators, Alerts, and Insufficient Balance wall. |
| `--van-background-2` | `Dark/Neutral` | Primary surface background of the app. |

---

## 💎 4. SAV (STRONGBOX) FORENSIC DEEP-DIVE
The Strongbox is a "Virtual Vault" mechanism that handles interest and balance locking.

- **Component Path**: `page-main-StrongBox-992d5c5b.js`
- **Core Functions**:
    1.  `TransferToStrongbox`: Moves funds from `UserAccount` to `VirtualSAV`.
    2.  `TransferFromStrongbox`: Unlocks funds for betting or withdrawal.
- **Modification Note**: The UI check for "Minimum Transfer" can be bypasses by patching the `vt()` function within this JS chunk.

---

## 📡 5. MASTER API REGISTRY (PRODUCTION ENDPOINTS)

### **A. Identity & Security**
- `POST /api/User/Login`: Access token generator.
- `GET /api/User/GetUserInfo`: Returns `balance`, `sav_balance`, and `vip_level`.

### **B. Financial Gateways**
- `POST /api/Wallet/SubmitRecharge`: Generates the redirect URL for UPI/Bank apps.
- `POST /api/Wallet/Withdraw`: Triggers the bank payout request.

### **C. SaaS Game Launcher (THE RECHARGE LOCK)**
- `POST /api/Game/GetGameUrl`: **CRITICAL**. Checks user balance before returning iframe link. Returns `code 4001` if balance is low.

---

## 🛠️ 6. UI MODIFICATION PLAYBOOK (STEP-BY-STEP)

### **Task: Changing the Logo**
1. Navigate to `/assets/images/`.
2. Locate `logo-*.webp`.
3. Replace with your brand logo using the **exact same filename** (or update the hash reference in `index.js`).

### **Task: Bypassing the Recharge Wall**
1. Open `common.modules-5cfe2cf4.js`.
2. Search for the string `4001`.
3. Locate the condition that triggers `Dialog.confirm` (The recharge popup).
4. Comment out the redirect and replace with `return Promise.resolve()`.

---

## ⚠️ Integrity & Security
- **Digital Fingerprint**: Files use MD5 hashing for anti-cheat.
- **Service Worker**: PWA logic resides in `ar-sw.js`. If you patch files, increment the version in the sw-config to force browser refresh.

---
**Status**: `Archived / Final Revision`
**Repository**: `git@github.com:ani455/ar093-Forensic-Master.git`
