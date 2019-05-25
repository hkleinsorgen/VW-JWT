# VW-JWT

JSON Web Tokens implementation for VisualWorks

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
key := 'ofvxYwbzBtiTUlEmATlZKXWcBHvuvOiGKeMBUsPCR9UACNPuJ/H198HsjGGY+5iXATzovQ3ZB88X+aR6LJm/9UR4D/cMZhbd80cPRN5J2WpelcVAM4SUNedbdHLMIQXnWGqDpNeY0XNpiHUajBiP1RhP3IrFWssaTuMw44dhEYd6MYk5DA5oRsaIAnUeFbhhk3LLwmJK4KUEUqwH+q0I6sZTjRd5b4oxifRYZA7NZS8DSxPkf6RPBm3HH4lsaAmmSaUxq8gYfiCjPT377bp9gZd5rjeRniS3tkOlpO8O+0t8WVMKcDn4JjhyN9Ys6gFVKe0ZqY8RvGMsgflaOVIXmg=='.
encodedToken := 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.6zLGMHPTPIKE3sE20049SLp7AOiNWSK1_bDhTTxT4-A'.
token := JWT.Token fromEncodedToken: encodedToken.
" Raises an exception if invalid "
token verifyHS256: key
```
Note: When using the debugger at https://jwt.io keep in mind that the line indentation of the header and payload matter
