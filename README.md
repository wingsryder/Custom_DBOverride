# Custom_DBOverride — Magento2 DB Version Bypass (MariaDB 10.5+)

---

**⚠️ Disclaimer:**  
**Use this module at your own risk in production.**  
This module only bypasses validation, it does not add guaranteed compatibility.

---

**Purpose:** Unblock Magento 2 stores that are stuck on older 2.4.x releases (e.g., 2.4.0–2.4.3-p3 / 2.4.2-p2) when the hosting provider runs **MariaDB 10.5+** and cannot be downgraded.

**Symptom it solves:**
```
Current version of RDBMS is not supported.
Used Version: 10.5.x-MariaDB
Supported versions: MySQL-8, MySQL-5.7, MariaDB-(10.2-10.4)
```

This module **bypasses Magento’s DB version gate** so you can install/upgrade and run the application on MariaDB 10.5+ where it is functionally compatible but blocked by version checks.

---


## Why this module exists

Older Magento 2.4.x releases hard-code a supported MariaDB range of 10.2–10.4. Many hosts default to 10.5/10.6+, which triggers the installer/CLI/runtime to refuse to proceed even though Magento’s SQL usage typically works on 10.5+.

When downgrading MariaDB isn’t possible, this module spoofs the detected DB version and short-circuits the installer validation so you can keep operating until you upgrade Magento to a version that officially supports 10.5/10.6.

**Use this module primarily for 2.4.0–2.4.3-p3 when stuck on MariaDB 10.5+.**

---

## What it does not do

It does not change your actual database or SQL behavior.

It does not add features or performance optimizations.

It does not make unsupported combinations magically safe—you must test your store.

It is not needed (and not recommended) on newer Magento that already support MariaDB 10.5/10.6.

---
## Installation

1. Copy the module into `app/code/Custom/DBOverride/` (look like this structure)
2. Run:
   ```bash
   bin/magento setup:upgrade
   bin/magento cache:flush
   ```

3. Confirm setup completes without the DB version error.

---

## Notes

- This is **not an official Magento patch**.
- Works around the installer/runtime validation only.
- Database-level compatibility is assumed safe for most cases, but Magento only **officially supports MariaDB up to 10.4**.

---

## Contribution

Feel free to open PRs, improve code, or share feedback in Issues.

---
