<!-- loio6bdd6c29887f48f69940af679f520e45 -->

# Code Samples \(Java\)



The Java samples below use the *jose4j* library. For more information, see [Bitbucket wiki: jose4j](https://bitbucket.org/b_c/jose4j/wiki/Home).

> ### Restriction:  
> Make sure you have JDK version *9* or higher. Lower Java versions don't support encryption algorithm AES256 by default. In case of lower version, you should either configure your crypto policy, or use AES128.



<a name="loio6bdd6c29887f48f69940af679f520e45__section_bft_bqw_tgb"/>

## Encrypt Request

> ### Example:  
> ```
> 
> package jwe;
> 
> import java.security.KeyFactory;
> import java.security.interfaces.RSAPublicKey;
> import java.security.spec.X509EncodedKeySpec;
> import java.util.Base64;
> 
> import org.jose4j.jwe.ContentEncryptionAlgorithmIdentifiers;
> import org.jose4j.jwe.JsonWebEncryption;
> import org.jose4j.jwe.KeyManagementAlgorithmIdentifiers;
> 
> public class Encrypt {
> 	
>   private static String PUBLIC_KEY = "MIIBIjAN...";
> 
>   public static void main(String[] args) throws Exception {
>     KeyFactory keyFactory = KeyFactory.getInstance("RSA");
>     byte[] binaryKey = Base64.getDecoder().decode(PUBLIC_KEY);
>     RSAPublicKey publicKey = (RSAPublicKey)keyFactory.generatePublic(new X509EncodedKeySpec(binaryKey));  		
>     JsonWebEncryption jwe = new JsonWebEncryption();
>     jwe.setPayload("{\"name\":\"pass1\",\"value\":\"secret1\",\"username\":\"user1\"}");
>     jwe.setAlgorithmHeaderValue(KeyManagementAlgorithmIdentifiers.RSA_OAEP_256);
>     jwe.setEncryptionMethodHeaderParameter(ContentEncryptionAlgorithmIdentifiers.AES_256_GCM);
>     jwe.setKey(publicKey);
>     long iat = TimeUnit.MILLISECONDS.toSeconds(System.currentTimeMillis());
>     jwe.getHeaders().setObjectHeaderValue("iat", iat);
>     String jweCompact = jwe.getCompactSerialization();
>     System.out.println(jweCompact);
>   }
> }
> ```



<a name="loio6bdd6c29887f48f69940af679f520e45__section_jx5_cqw_tgb"/>

## Decrypt Response

> ### Example:  
> ```
> 
> package jwe;
> 
> import java.security.KeyFactory;
> import java.security.interfaces.RSAPrivateKey;
> import java.security.spec.PKCS8EncodedKeySpec;
> import java.util.Base64;
> 
> import org.jose4j.jwa.AlgorithmConstraints;
> import org.jose4j.jwa.AlgorithmConstraints.ConstraintType;
> import org.jose4j.jwe.ContentEncryptionAlgorithmIdentifiers;
> import org.jose4j.jwe.JsonWebEncryption;
> import org.jose4j.jwe.KeyManagementAlgorithmIdentifiers;
> 
> public class Decrypt {
> 
>   private static final AlgorithmConstraints CONTENT_ENCRYPTION_ALGORITHM_CONSTRAINTS = new AlgorithmConstraints(ConstraintType.WHITELIST, ContentEncryptionAlgorithmIdentifiers.AES_256_GCM);
>   private static final AlgorithmConstraints KEY_ENCRYPTION_ALGORITHM_CONSTRAINTS = new AlgorithmConstraints(ConstraintType.WHITELIST, KeyManagementAlgorithmIdentifiers.RSA_OAEP_256);
> 	
>   private static final String PRIVATE_KEY = "MIIEvgIB...";
> 	
>   public static void main(String[] args) throws Exception {
>     KeyFactory keyFactory = KeyFactory.getInstance("RSA");
>     byte[] binaryKey = Base64.getDecoder().decode(PRIVATE_KEY);
>     RSAPrivateKey privateKey = (RSAPrivateKey)keyFactory.generatePrivate(new PKCS8EncodedKeySpec(binaryKey));  		
>     JsonWebEncryption jwe = new JsonWebEncryption();
>     jwe.setAlgorithmConstraints(KEY_ENCRYPTION_ALGORITHM_CONSTRAINTS);
>     jwe.setContentEncryptionAlgorithmConstraints(CONTENT_ENCRYPTION_ALGORITHM_CONSTRAINTS);
>     jwe.setKey(privateKey);
>     jwe.setCompactSerialization("eyJhbGciOiJ...");
>     Long iat = jwe.getHeaders().getLongHeaderValue("iat");
>     System.out.println("iat:" + iat);
>     String payload = jwe.getPayload();
>     System.out.println(payload);
>   }
> }
> ```

**Related Information**  


[Encrypting Payloads](encrypting-payloads-7202e7a.md "SAP Credential Store provides payload encryption, which is enabled by default.")

