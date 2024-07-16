# Recon-ng

## Usage

### 01 - Setting up workspace

```
[recon-ng][default] > workspaces create <workspace_name>

[recon-ng][<workspace_name>] > db insert <table>

[recon-ng][<workspace_name>] > dashboard
```

### 02 - Database Schema

```
[recon-ng][default] > db schema

[recon-ng][default] > db query SELECT * FROM DOMAINS

[recon-ng][default] > db query SELECT * FROM COMPANIES

[recon-ng][default] > db query SELECT * FROM NETBLOCKS

[recon-ng][default] > db query SELECT * FROM LOCATIONS

[recon-ng][default] > db query SELECT * FROM VULNERABILITIES

[recon-ng][default] > db query SELECT * FROM PORTS

[recon-ng][default] > db query SELECT * FROM HOSTS

[recon-ng][default] > db query SELECT * FROM CONTACTS

[recon-ng][default] > db query SELECT * FROM CREDENTIALS

[recon-ng][default] > db query SELECT * FROM LEAKS

[recon-ng][default] > db query SELECT * FROM PUSHPINS

[recon-ng][default] > db query SELECT * FROM PROFILES

[recon-ng][default] > db query SELECT * FROM REPOSITORIES
```

---
## References

- [OSINT Part-2 Using Recon-ng to Find the Same Profile across Multiple Sites](https://www.hackers-arise.com/post/2019/05/16/OSINT-Part-2-Using-recon-ng-to-find-the-Same-Profile-across-Multiple-Sites)

- [Pentest Tools Recon-ng](https://chousensha.github.io/blog/2016/08/29/pentest-tools-recon-ng/)