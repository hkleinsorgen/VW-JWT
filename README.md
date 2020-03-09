# VW-JWT

JSON Web Tokens implementation for VisualWorks 8.3

See https://jwt.io/

Encode:

```
| payload key |
payload := '{"sub":"smalltalk-user"}'.
key := Xtreams.SecureRandom reading read: 512.
( JWT.Token payload: payload ) signWithKey: key algorithm:  'HS512'
```

Decode:
```
| key token encodedToken |
key := 'VmlzdWFsV29ya3MgaXMgYSBjcm9zcy1wbGF0Zm9ybSBpbXBsZW1lbnRhdGlvbiBvZiB0aGUgU21hbGx0YWxrIGxhbmd1YWdl'.
encodedToken := 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9leCIsImlhdCI6MTUxNjIzOTAyMn0.C_Ukg83YeVx6w5vk2jciPmROqEuGcAPUoTVLShsyQQI'.
token := JWT.Token fromEncodedToken: encodedToken.
" Raises an exception if invalid "
token verifyHS256: key
```

## Debugging
When using the debugger at https://jwt.io keep in mind that the whitespaces of the header and payload matter

