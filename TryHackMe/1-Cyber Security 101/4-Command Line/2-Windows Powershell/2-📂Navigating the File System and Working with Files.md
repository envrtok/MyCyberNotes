## Basic Operations
### 📑 Listing & Navigation

- `Get-ChildItem` → for `dir` or `ls`
- `Set-Location` → for `cd`

---

### 📝 Creating & Removing

- `New-Item -Path "<path\new-file>" -ItemType "<file or directory(folder)">` → creates a file or folder
- `New-Item -Path "<path\new-file>"` → removes the given file or folder

---

### 📄 Copying & Reading

- `Copy-Item -Path "<copied-path>" -Destination "<pasted-this-path>"` → copies files or folders
- `Get-Content` → for `type` or `cat`
---
## Piping, Filtering, and Sorting Data
- Piping allows that make output a command for input of next command
	- command1 | command2
- Get-ChildItem | Sort-Object Length sorts by size