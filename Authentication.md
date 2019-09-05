Ketting supports the following authentication schemes:

* HTTP Basic auth
* OAuth2 flows
  * `password` grant
  * `implicit` grant

When using Ketting across multiple domains, it optionally supports per-domain authentication.

Basic Auth
----------

```typescript
const ketting = new Ketting(
  'api.example.org',
  {
    auth: {
      type: 'basic',
      userName: 'foo',
      password: 'bar'
    }
  }
);
```
    
OAuth2
------

The following section details setting up OAuth2 authentication for
various flows.

For each of these the 'scopes' parameter is always optional.

If the client gets a refresh token back from an OAuth2 server, it will
use it to refresh the access token.

If the client gets back the expiry time for the access token from the OAuth2
server, it will preemptively do a refresh.

### OAuth2 "password" grant

```typescript
const ketting = new Ketting(
  'api.example.org',
  {
    auth: {
      type: 'oauth2',
      grantType: 'password',
      clientId: 'fooClient',
      clientSecret: 'barSecret',
      tokenEndpointUri: 'https://api.example.org/oauth/token',
      scopes: ['test']
      userName: 'fooOwner',
      password: 'barPassword'
    }
  }
);
```


### OAuth2 "client_credentials" grant type

```typescript
const ketting = new Ketting(
  'api.example.org',
  {
    auth: {
      type: 'oauth2',
      grantType: 'client_credentials',
      clientId: 'fooClient',
      clientSecret: 'barSecret',
      tokenEndpointUri: 'https://api.example.org/oauth/token',
      scopes: ['test']
    }
  }
};
```

### OAuth2 "authorization_code" grant type

```typescript
const ketting = new Ketting(
  'api.example.org',
  {
    auth: {
      type: 'oauth2',
      grant_type: 'authorization_code',
      clientId: 'fooClient',
      code: '...',
      tokenEndpointUri: 'https://api.example.org/oauth/token',
    }
  }
};
```

'authorization_code' flow is a multi-step process. The first step is to
redirect a user to a 'authorize' url on an Auth2 server, let the user log
in and get redirected back to a URL the developer controls with a "code"
parameter.

The 'authorization_code' flow in Ketting assumes that step has already
happened and the user of the Ketting object simply passes the "code".

The reason this is not implemented in Ketting, is because taking over
navigation in a browser is considered out of scope. Ketting is just
responsible for communicating with the API.

### OAuth2: setting up auth with an accesstoken and/or refresh token

If an access token was obtained via other means (with or without a refresh
token), this is how the client can be set up:

```typescript
const ketting = new Ketting(
  'api.example.org',
  {
    auth: {
      type: 'oauth2',
      clientId: 'fooClient',
      clientSecret: '...', // Sometimes optional
      accessToken: '...',
      refreshToken: '...', // Optional.
      tokenEndpointUri: 'https://api.example.org/oauth/token',
    }
  }
};
```

This is also how the client might be setup after an `implicit` flow.

Multi-domain authentication
---------------------------

When using Ketting to hop from domain-to-domain, it might be important for
authentication information to not get passed to every domain.

By default Ketting *does* assume that authentication will be sent to every
domain. To avoid this, use the per-domain auth syntax:

```typescript
const ketting = new Ketting(
  'api.example.org',
  {
    match: {
      '*.example.org': {
         auth: {
           type: 'oauth2',
           clientId: 'fooClient',
           clientSecret: '...', // Sometimes optional
           accessToken: '...',
          refreshToken: '...', // Optional.
          tokenEndpointUri: 'https://api.example.org/oauth/token',
        }
     },
     'api.github.com': {
       auth: {
         type: 'basic',
         userName: 'foo',
         password: 'bar'
       }
     }
   }
};
```