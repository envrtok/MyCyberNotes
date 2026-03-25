```shell
ffuf -w /usr/share/wordlists/SecLists/Usernames/Names/names.txt -X POST -d "username=FUZZ&email=x&password=x&cpassword=x" -H "Content-Type: application/x-www-form-urlencoded" -u http://10.65.162.184/customers/signup -mr "username already exists" -o results.txt -of csv
```
- -w: Wordlist of usernames
- -x: Request method
- -d: Sent data, FUZZ signifies contents from wordlist
- -H: Additional headers
- -u: URL
- -mr: Text in our screen about username existance validation
- -o: Output file
- -of: Output file format
