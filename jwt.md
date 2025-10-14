# SHECA API uses JWT verification process

## 1. API interaction process

<img width="1054" height="830" alt="image" src="https://github.com/user-attachments/assets/ad3a3283-d845-408f-954c-bfba754a5f11" />


## 2. JWT Verification Principle (Using Public and Private Keys)

### 2.1 JWT Principle

The actual JWT might look like this.

![img](https://cdn.beekka.com/blogimg/asset/201807/bg2018072304.jpg)

It's a long string, `.`divided into three parts by periods ( ). Note that there are no line breaks within the JWT; it's simply written across multiple lines for ease of presentation.

The three parts of JWT are as follows.

> - Header
> - Payload
> - Signature

Written in one line, it looks like the following.

> ```javascript
> Header.Payload.Signature
> ```

![img](https://cdn.beekka.com/blogimg/asset/201807/bg2018072303.jpg)

The following introduces these three parts in turn.

#### 2.1.1 Header

The Header part is a JSON object that describes the metadata of the JWT, usually as follows.

> ```javascript
> {
>   "alg": "HS256",
>   "typ": "JWT"
> }
> ```

In the above code, `alg`the attribute represents the signature algorithm, which defaults to HMAC SHA256 (written as HS256); `typ`the attribute represents the type of this token, which is uniformly written as JWT token `JWT`.

Finally, convert the above JSON object into a string using the Base64URL algorithm (see below for details).

#### 2.1.2 Payload

The Payload section is also a JSON object that stores the actual data to be transmitted. JWT specifies seven official fields for selection.

> - iss (issuer): issuer
> - exp (expiration time): expiration time
> - sub (subject): subject
> - aud (audience): audience
> - nbf (Not Before): Effective time
> - iat (Issued At): Issue time
> - jti (JWT ID): ID

In addition to official fields, you can also define private fields in this section. Below is an example.

> ```javascript
> {
>   "sub": "1234567890",
>   "name": "John Doe",
>   "admin": true
> }
> ```

Note that JWT is unencrypted by default and can be read by anyone, so do not put secret information in this section.

This JSON object must also be converted into a string using the Base64URL algorithm.

#### 2.1.3 Signature

The Signature section is a signature of the previous two sections, preventing data tampering.

First, a public and private key pair must be generated. The private key should only be accessible to the user. Then, a signature is generated using the following formula.

```
// private key
    private static final String PRIVATE_KEY_PATH = "path/to/private_key.pem";
    // peivate key passowrd
    private static final String PRIVATE_KEY_PASSWORD = "your-private-key-password";
    // Token expiration time (example: 1 hour)
    private static final long EXPIRATION_TIME = 3600 * 1000;

    // Generate JWT
    public static String generateToken(String userId, String role) throws Exception {
        // load private key
        PrivateKey privateKey = RsaKeyUtil.loadPrivateKey(PRIVATE_KEY_PATH, PRIVATE_KEY_PASSWORD);

        // Constructing a JWT
        return Jwts.builder()
                .claim("userId", userId)
                .claim("role", role)
                .setExpiration(new Date(System.currentTimeMillis() + EXPIRATION_TIME))
                .setIssuedAt(new Date())
                .setIssuer("XXX") 
                .signWith(privateKey, SignatureAlgorithm.RS256)
                .compact();
    }
```

After calculating the signature, the header, payload, and signature are combined into a string, with each part separated by a dot (`.`), and then returned to the user.

## 3. How to Use JWT

After receiving the JWT from the server, the client can store it in a cookie or localStorage.

Thereafter, the client must include this JWT in every communication with the server. You can automatically send it in a cookie, but this won't work across domains. Therefore, it's better to include it in the Authorization header of the HTTP request.

> ```javascript
> Authorization: Bearer <token>
> ```

### 4. SHECA Implementation Steps

1. SHECA generates public and private keys in the order system. Partners download the private keys through the SHECA interface.

2. When requesting the SHECA openAPI, partners use their private key to sign the request header and include "Authorization: Bearer <token>" in the request header.

3. After receiving the request, SHECA obtains the user ID in the JWT and queries the associated public key. SHECA uses the public key to verify the JWT signature. If verification passes, the request is processed normally. If verification fails, the request is rejected.







**Note: These public and private keys are only used for permission verification between SHECA and its partners, mainly to prevent illegal requests. The scope of application of these public and private keys is very limited.**

