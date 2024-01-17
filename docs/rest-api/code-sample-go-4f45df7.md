<!-- loio4f45df7f58a54b6eb2972325be941c81 -->

# Code Sample \(Go\)

The sample code below is based on the [Aut0 Go JWT](https://github.com/auth0/go-jwt-middleware) library.



<a name="loio4f45df7f58a54b6eb2972325be941c81__section_il3_gcn_btb"/>

## Sign JWT

> ### Example:  
> ```
> 
> package main
> 
> import (
> 	"crypto/rsa"
> 	"crypto/x509"
> 	"encoding/base64"
> 	"fmt"
> 	"github.com/dgrijalva/jwt-go"
> 	"github.com/satori/go.uuid"
> 	"time"
> )
> 
> type BindingCredentials struct {
> 	OAuthTokenUrl string
> 	Username      string
> 	PrivateKey    string
> }
> 
> func main() {
> 	
> 	credentials := BindingCredentials {
> 	    OAuthTokenUrl : "https://credstoreauth.cfapps.sap.hana.ondemand.com/api/v1/token",
> 	    Username : "4e89d33b-0283-5ff5-b9f8-9419eab5b70c.0.q19QcAT/qNjKC2YPrTdwpV+FwMLmZgiEI886PaUsnL8=",
> 	    PrivateKey : "MIIEv...",
> 	}
> 	
> 	jwtId, _ := uuid.NewV4()
> 	
> 	token := jwt.NewWithClaims(jwt.SigningMethodRS256, jwt.MapClaims{
> 		"iss": credentials.Username,	
> 		"aud": credentials.OAuthTokenUrl,
> 		"iat": time.Now().Unix(),
> 		"jti": jwtId,
> 		"nsp": "namespace1",
> 	})
> 	
> 	der, _ := base64.StdEncoding.DecodeString(credentials.PrivateKey)
> 	key, _ := x509.ParsePKCS8PrivateKey(der)
> 	privateKey, _ := key.(*rsa.PrivateKey)
> 	signedJWT, _ := token.SignedString(privateKey);
> 	
> 	fmt.Printf("%s", signedJWT)
> }
> ```

