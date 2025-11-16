#### **1. The Default "Computers" Container 📦**
*   When a machine joins a domain, it is automatically placed in the default **"Computers"** container.
*   This is **not ideal** for applying different policies to different types of machines.

#### **2. Recommended Computer Categories 🗂️**
It's best practice to organize computers into separate Organizational Units (OUs) based on their use:

*   **Workstations 💼**
    *   **Purpose:** Daily-use machines for regular users.
    *   **Rule:** Privileged users should **never** log into these.

*   **Servers 🗄️**
    *   **Purpose:** Provide services to users and other servers.

*   **Domain Controllers 🌐**
    *   **Purpose:** Manage the Active Directory domain.
    *   **Note:** These are the **most sensitive** devices and are already in a dedicated OU by default.

#### **3. Organizing the Structure 🏗️**
*   **Goal:** Create a clean OU structure for better policy management.
*   **Action:** Create two new OUs under the root domain:
    1.  **Workstations**
    2.  **Servers**
*   **Final Step:** Move computers from the default "Computers" container into their correct OUs:
    *   User PCs/Laptops → **Workstations** OU
    *   Servers → **Servers** OU

This organization allows you to apply specific Group Policies to each computer type later on! ⚙️