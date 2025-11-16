#### **1. Aligning AD with the Org Chart 📊**
*   **Goal:** Update Active Directory to match the current company organizational chart.
*   **Step 1: Delete Extra OUs 🗑️**
    *   OUs are **protected from accidental deletion** by default.
    *   **Solution:** Enable `Advanced Features` in the `View` menu.
    *   Then, uncheck "Protect object from accidental deletion" in the OU's **Properties** to delete it.

*   **Step 2: Sync Users 👤**
    *   Create or delete users as needed to make the AD users match the org chart.

#### **2. Delegating Control 🤝**
*   **What is it?** Granting specific users permissions to manage OUs without making them Domain Admins.
*   **Common Use Case:** Allowing IT support to **reset passwords**.

*   **Process:**
    1.  **Right-click** the target OU (e.g., Sales) → `Delegate Control`.
    2.  **Add the user** (e.g., `phillip`).
    3.  **Select the task** → Choose "Reset user passwords".

#### **3. Testing Delegation: Password Reset 🔐**
*   **User:** `THM\phillip`
*   **Tool:** Use **PowerShell** (as Phillip lacks permissions for the GUI tool).

*   **Command to Reset Password:**
    ```powershell
    Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password')
    ```

*   **Command to Force Change at Next Logon:**
    ```powershell
    Set-ADUser -ChangePasswordAtLogon $true -Identity sophie
    ```

*   **Final Goal:** Log in as `THM\sophie` with the new password to retrieve a flag from her desktop. 🚩