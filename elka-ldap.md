## Login
Before issuing a login request we need to execute a GET to any page ex. `https://studia3.elka.pw.edu.pl/pl/19Z/` to get the STUDIA_SID cookie
```http
POST /en/19Z/-/login-ldap HTTP/1.1
Host: https://studia3.elka.pw.edu.pl
Cookies: STUDIA_SID=$SESSION_ID$; STUDIA_COOKIES=YES;
Content-Type: application/x-www-form-urlencoded

studia_uri=&studia_login=$LOGIN$&studia_passwd=$PASSWORD$&zaloguj=Zaloguj
```
```http
HTTP/1.0 302 Found
Connection: Keep-Alive
Date: Tue, 29 Oct 2019 20:52:57 GMT
Keep-Alive: timeout=5, max=1000
Location: https://studia3.elka.pw.edu.pl/pl/19Z/
Server: Apache/2.4.25 (Debian)
Set-Cookie: STUDIA_SID=$SESSION_ID$; domain=studia3.elka.pw.edu.pl; path=/
Transfer-Encoding: chunked
```

After loggining in the STUDIA_SID cookie does not change, but the session is now flagged as logged in. We can make any request providing the session cookie an the server is going to register it as valid and serve the content, as long as the user has access to it. 

## Keeping the session alive
The session is valid for 15 minutes unless renewed using this endpoint
```http
GET /en/19Z/Time/login/ HTTP/1.1
Host: https://studia3.elka.pw.edu.pl
Cookies: STUDIA_SID=$SESSION_ID$; STUDIA_COOKIES=YES;
```

```http
HTTP/1.0 200 OK
Connection: Keep-Alive
Content-Type: application/json; charset=utf-8
Keep-Alive: timeout=5, max=992
Server: Apache/2.4.25 (Debian)
Transfer-Encoding: chunked

{
  "now": "1572382380",
  "time": "1572382380",
  "limit": "900",
  "end": "1572383280"
}

```
