## 📖 What is PowerShell

- PowerShell is powerful tool for task automation and configuration management.
- It combines command-line interface and scripting language.
- It works with objects and properties _(object-oriented programming)_.
- The commands are called **command-lets (cmdlets)**.
- Cmdlets follow a **verb-noun naming convention**:
    - **Verb** → An action _(eg: `Set-Location`: changes current directory)_
    - **Noun** → An object _(eg: `Get-Content`: gets the content of a file)_

---

## ⚙️ Basic Cmdlets

- `Get-Command` → shows all lists, scripts and aliases that can be executed
- `Get-Command -Commandtype "Function"` → gives only functions
- `Get-Command -Name remove*` → gives all commands which starts with remove word
- `Get-Help <cmdlet>` → provides detailed information about given cmdlet's usage, parameters
- `Get-Help <cmdlet> - examples` → provides detailed information about given cmdlet's usage, parameters and examples
- `Get-Alias` → shows all aliases
    - _(alias is command version of some basic cmdlets, eg: `cd` for `Set-Location`, `clear` for `Clear-Host`)_
- `Find-Module -Name "<words>"` → finds cmdlets called given words
- `Install-Module -Name "<module-name>"` → downloads the given module