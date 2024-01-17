<!-- loio5e896985b6254c5095ad7202503eea24 -->

# Code Sample \(Java\)

The sample code below is based on the [Auth0 Java JWT](https://github.com/auth0/java-jwt) library.

You need to define the following Maven dependency in order to compile the code:

```

<dependency>
   <groupId>com.auth0</groupId>
   <artifactId>java-jwt</artifactId>
   <version>3.3.0</version>
</dependency>
```



<a name="loio5e896985b6254c5095ad7202503eea24__section_il3_gcn_btb"/>

## Sign JWT

> ### Example:  
> ```
> package jwt;
> 
> import java.security.KeyFactory;
> import java.security.NoSuchAlgorithmException;
> import java.security.interfaces.RSAPrivateKey;
> import java.security.spec.InvalidKeySpecException;
> import java.security.spec.PKCS8EncodedKeySpec;
> import java.util.Base64;
> import java.util.Date;
> import java.util.UUID;
> 
> import com.auth0.jwt.JWT;
> import com.auth0.jwt.JWTCreator.Builder;
> import com.auth0.jwt.algorithms.Algorithm;
> 
> public class SignedJWT {
>  
>   private static final String BINDING_ID = "4e89d33b-0283-5ff5-b9f8-9419eab5b70c.0.q19QcAT/qNjKC2YPrTdwpV+FwMLmZgiEI886PaUsnL8="; 	
>   private static final String BINDING_PRIVATE_KEY = "MIIEv...";
>   private static final String OAUTH_TOKEN_URL = "https://credstoreauth.cfapps.sap.hana.ondemand.com/api/v1/token";
> 
>   public static void main(String[] args) throws NoSuchAlgorithmException, InvalidKeySpecException {	
>     KeyFactory keyFactory = KeyFactory.getInstance("RSA");
>     byte[] binaryKey = Base64.getDecoder().decode(BINDING_PRIVATE_KEY);
>     RSAPrivateKey privateKey = (RSAPrivateKey)keyFactory.generatePrivate(new PKCS8EncodedKeySpec(binaryKey));  
>     Algorithm algorithm = Algorithm.RSA256(null, privateKey);
>     Builder jwtBuilder = JWT.create();
>     jwtBuilder.withIssuer(BINDING_ID);
>     jwtBuilder.withAudience(OAUTH_TOKEN_URL);
>     jwtBuilder.withIssuedAt(new Date());
>     jwtBuilder.withJWTId(UUID.randomUUID().toString());
>     jwtBuilder.withClaim("nsp", "namespace1");
>     String signedJWT = jwtBuilder.sign(algorithm);
>     System.out.println(signedJWT);
>   }
> 
> }
> ```

