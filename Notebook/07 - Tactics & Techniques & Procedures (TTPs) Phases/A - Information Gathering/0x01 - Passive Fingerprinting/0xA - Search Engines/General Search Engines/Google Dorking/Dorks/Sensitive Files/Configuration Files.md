# Configuration Files

## File Extensions

```
ext:(xml | conf | cnf | reg | inf | rdp | cfg | txt | ora | ini | env)
```

## Firewall Rules

```
filetype:conf inurl:firewall -intitle:cvs
```

## Kerberos

```
krb.conf OR krb.realms intitle:"index of" -public -archive -packages -pub
```