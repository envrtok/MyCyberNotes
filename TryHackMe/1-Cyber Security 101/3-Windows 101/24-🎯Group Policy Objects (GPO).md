#### **1. What are GPOs? 🤔**
*   **Purpose:** To deploy different configurations and security settings to users and computers.
*   **Structure:** A collection of settings applied to Organizational Units (OUs).
*   **Types:** Contains policies for **Users** 👤 or **Computers** 💻.

#### **2. How GPOs Work ⚙️**
*   **Tool:** Managed with the **Group Policy Management** tool.
*   **Process:**
    1.  Create a GPO.
    2.  **Link** it to a target OU.
*   **Inheritance:** A GPO applies to the linked OU **and all its child OUs**.

#### **3. Key GPO Components 🔑**
*   **Scope:** Defines where the GPO is linked.
*   **Security Filtering:** Limits the GPO to specific users/computers (default: **Authenticated Users**).
*   **Settings:** The actual configurations (Policies → Computer Configurations / User Configurations).
*   **Distribution:** Done via the **SYSVOL** network share on Domain Controllers.

#### **4. Practical Example: THM Inc. GPOs 🏢**
**🎯 Goal 1: Restrict Control Panel for non-IT users**
*   **GPO Name:** `Restrict Control Panel Access`
*   **Policy Path:** `User Configuration -> Administrative Templates -> Control Panel`
*   **Policy Setting:** `Prohibit Access to Control Panel and PC settings` → **Enabled**
*   **Linked To:** Marketing, Management, and Sales OUs.

**🎯 Goal 2: Auto-lock screens after 5 minutes**
*   **GPO Name:** `Auto Lock Screen`
*   **Policy Path:** `Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Local Policies -> Security Options`
*   **Policy Setting:** `Interactive logon: Machine inactivity limit` → **5 minutes**
*   **Linked To:** The root domain (applies to all computer OUs via inheritance).

#### **5. Important Notes & Commands 💡**
*   **Forcing a Update:** GPO changes can take up to 2 hours. To force an immediate update:
    ```powershell
    gpupdate /force
    ```
*   **Verification:** You can log in as a user (e.g., `THM\Mark`) to test if the GPOs are working correctly.