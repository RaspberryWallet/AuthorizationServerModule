#### This module is going to authorize wallet decryption as trusted third party service.

### Initialization of module sequence diagram:

![](https://www.websequencediagrams.com/cgi-bin/cdraw?lz=dGl0bGUgQXV0aG9yaXphdGlvbiBTZXJ2ZXIgTW9kdWxlOiBpbml0aWFsABcHCgpNYW5hZ2VyLT5SUEkAJQYAIghTZW5kIHNpbmdsZSBwYXJ0IG9mIGEgd2FsbGV0IHNlY3JldCBrZXkKACoPADcTRW5jcnlwACkMIHdpdGggcmFuZG9tIHBhc3N3b3JkADgSAIE9DQCBQwY6IFJlZ2lzdGVyIGEgbmV3AIEKBwAVJ0F1dGhlbnRpY2F0ZSBvbiBzAIIXBmFuZCBzZW5kIGUAgSQGZWQAgVUMAHMTLT5SZWRpczogU3RvcmUAgg4HJ3MAKxUAgjgF&s=default)

<details><summary>Sequence diagram code</summary>
<p>

```html
title Authorization Server Module: initialization

Manager->RPIServerModule: Send single part of a wallet secret key
RPIServerModule->RPIServerModule: Encrypt secret key with random password
RPIServerModule->AuthorizationServer: Register a new wallet
RPIServerModule->AuthorizationServer: Authenticate on server and send encrypted secret key
AuthorizationServer->Redis: Store wallet's encrypted secret key part
```

</p>
</details>

### Unclock module sequence diagram:

![](https://www.websequencediagrams.com/cgi-bin/cdraw?lz=dGl0bGUgQXV0aG9yaXphdGlvbiBTZXJ2ZXIgTW9kdWxlOiB1bmxvY2tpbmcgbQANBQoKTWFuYWdlci0-UlBJACcGACQIVQAnBQAhCAAQDy0-AFsNAGEGOiBMb2dpbiB3aXRoIHNlY3JldCBwYXNzd29yZAoAHRMALhdWYWxpZGF0ZQAzCQBLBlNwcmluZyBTZWN1cml0eQCBOggAQxVSZWRpczogR2V0IHdhbGxldCdzIGVuY3J5cHRlZACBEwhrZXkAJxcAgXsQUmV0dXJuACwfAIIREQCCQRFEZQB9BQB1CwCCJQZyYW5kb20AgiEKAIJbEQCDHgcAgQAJZABDBmVkIHBhcnQgb2YAgUcMCg&s=default)

<details><summary>Sequence diagram code</summary>
<p>

```html
title Authorization Server Module: unlocking module

Manager->RPIServerModule: Unlock module
RPIServerModule->AuthorizationServer: Login with secret password
AuthorizationServer->AuthorizationServer: Validate password with Spring Security module
AuthorizationServer->Redis: Get wallet's encrypted secret key
AuthorizationServer->RPIServerModule: Return wallet's encrypted secret key
RPIServerModule->RPIServerModule: Decrypt secret key with random password
RPIServerModule->Manager: Return decrypted part of secret key


```

</p>
</details>
