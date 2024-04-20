Assuming base URL: api.port0.iiitk.in

## To initiate account creation, collect a valid IIITK email address from the user and send the follwing request to the server:

{{< hint type=important title="Rate Limits" >}}
This endpoint has strict rate limits.
{{< /hint >}}

```
POST JSON /auth/register
{
    "email": "<...>@iiitkottayam.ac.in"
}
```

## The server will send a verification OTP to the email address. Collect the OTP from the user and send the following request to the server:

{{< hint type=important title="Rate Limits" >}}
This endpoint has strict rate limits.
{{< /hint >}}

```
POST JSON /auth/verify
{
    "email": "<...>@iiitkottayam.ac.in",
    "otp": "<OTP>"
}

Response:
{
    "token": "<JWT>"
}
```

## Proceed to create a new account with the JWT token in the Authorization header:

For the key hash use the following algorithm:

1. Use salted PBKDF2 hashing with 1000 iterations to generate a 256 bit key from the password.

2. Store the the key as the encryption key locally.

3. Hash the password again using SHA-256 and use it as the key hash.

{{< hint type=important title="Rate Limits" >}}
This endpoint has strict rate limits.
{{< /hint >}}

```
POST JSON /auth/create
{
    "token": "<JWT>",
    "salt": "<PBKDF2 salt>",
    "keyHash": "<key hash>",
}
```
