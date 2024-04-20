---
---

{{<hint type=note title="Note" >}}
This section is for developers and administrators of Port0 itself and documents interals. If you are a developer who wants to integrate your applications with Port0, please refer to the [developer documentation]({{<ref "/Port0 (For developers)">}}).
{{< /hint >}}

Assuming base URL: api.port0.iiitk.in

## Getting a Refresh Token

The user can only get one refresh token at a time. The refresh token is used to get a new access token.

{{< hint type=important title="Rate Limits" >}}
This endpoint has strict rate limits.
{{< /hint >}}

```
POST JSON /auth/refresh
{
    "email": "<...>@iiitkottayam.ac.in",
    "keyHash": "<key>"
}
```

#### Response:

```
{
    "reftoken": "<JWT>"
}
```

## Getting a new Access Token

Access tokens expire every 15 minutes.

```
POST JSON /auth/access
{
    "reftoken": "<JWT>"
}
```

#### Response

```
{
    "acctoken": "<JWT>"
}
```

## Get the vault:

```
POST JSON /getVault
{
    "acctoken": "<JWT>"
}
```

#### Response

```
{
    "salt": "<PBKDF2 salt>",
    "vault": "<encrypted vault>"
}
```

## Update the vault:

```

POST JSON /updateVault
{
    "acctoken": "<JWT>",
    "vault": "<encrypted vault>",
    (optional) "salt": "<PBKDF2 salt>"
}

```
