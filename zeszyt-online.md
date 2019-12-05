# Login
In order to login issue an HTTP request
```http
POST /api/login HTTP/1.1
Host: zeszyt.online
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
j_username=$USERNAME$&j_password=$PASSWORD$&authLoginForm=true

```

Login response:
```http
HTTP/1.0 200 OK
Connection: Keep-Alive
Server: Apache/2.4.18 (Ubuntu)
Set-Cookie: JSESSIONID=$SESSION_ID$
Set-Cookie: remember-me=$REMEMBER_ME$
```

When we receive the cookies request homework data:
```http
POST /api//uczen/pracedomowe/
Host: zeszyt.online
Accept: application/json, text/plain, */*
Cookie: $COOKIES$
```

Homework response:
```http
HTTP/1.0 200 OK
Server: Apache/2.4.18 (Ubuntu)
Content-Type: application/json;charset=UTF-8

```
```json
[
  {
    "rozpoczeta": "2019-12-05T22:02:25.578175+01:00",
    "zakonczona": null,
    "deadline": "2019-12-01T23:59:59+01:00",
    "archiwalna": false,
    "swiezoZarchiwizowana": false,
    "ileZadan": 5,
    "id": 143211,
    "nazwa": "Praca domowa nr 6",
    "filmWprowadzajacyUrl": null,
    "filmPodsumowujacyUrl": null,
    "rozszerzenie": null
  }
]
```
