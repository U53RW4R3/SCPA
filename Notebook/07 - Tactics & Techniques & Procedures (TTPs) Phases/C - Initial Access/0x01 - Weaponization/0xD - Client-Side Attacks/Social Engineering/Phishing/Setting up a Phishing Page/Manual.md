# Manual

## Clone the website

```
$ wget --mirror --convert-links --adjust-extension --page-requisites --no-parent --user-agent="<user_agent>" <URL>

$ wget -mkEp -np -U "<user_agent>" <URL>
```

```
$ wget --directory-prefix=/root/Desktop/ --header="Accept: text/html" 
--user-agent="(Mozilla/5.0 (Windows; U; Windows NT 6.0;en-US; rv:1.9.2) Gecko/20100115 Firefox/3.6" 
--domains test.com -e robots=off --recursive --no-clobber --page-requisites --html-extension 
--convert-links -R gif,jpg,png,css,pdf,mp3,wmv <URL>
```

---
## References

- [[User Agents]]

- [Recipe for a Successful Phishing Campaign Part 1](https://infosecwriteups.com/recipe-for-a-successful-phishing-campaign-part-1-2-dc23d927ec55)

- [Recipe for a Successful Phishing Campaign Part 2](https://infosecwriteups.com/recipe-for-a-successful-phishing-campaign-part-2-2-68552806dcba)