<!-- loio475dbb1f24894e1583b078d19acfdc86 -->

# Code Samples \(Go\)



The Go samples below are using *go-jose* library. For more information, see [GitHub: go-jose](https://github.com/go-jose/go-jose)



<a name="loio475dbb1f24894e1583b078d19acfdc86__section_jfz_ww2_5gb"/>

## Encrypt Request

```

package main

import (
	"crypto/x509"
	"encoding/base64"
	"fmt"
	"time"

	"github.com/go-jose/go-jose/v3"
)

const (
	serverPublicKey = "MIIBIj..."
	payload  = `{"name":"pass1","value":"secret1","username":"user1"}`
)

func main() {

	publicKeyBytes, err := base64.StdEncoding.DecodeString(serverPublicKey)
	if err != nil {
		panic(err)
	}

	pub, err := x509.ParsePKIXPublicKey(publicKeyBytes)
	if err != nil {
		panic(err)
	}

	opts := new(jose.EncrypterOptions)
	opts.WithHeader("iat", time.Now().Unix())

	encrypter, err := jose.NewEncrypter(jose.A256GCM, jose.Recipient{Algorithm: jose.RSA_OAEP_256, Key: pub}, opts)
	if err != nil {
		panic(err)
	}

	jwe, err := encrypter.Encrypt([]byte(payload))
	if err != nil {
		panic(err)
	}

	jweCompact, err := jwe.CompactSerialize()
	if err != nil {
		panic(err)
	}

	fmt.Println(jweCompact)

}

```



<a name="loio475dbb1f24894e1583b078d19acfdc86__section_aq1_xw2_5gb"/>

## Decrypt Response

```

package main

import (
	"crypto/x509"
	"encoding/base64"
	"fmt"

	"github.com/go-jose/go-jose/v3"
)

const (
	clientPrivateKey = "MIIEvQIBAD..."
	jwe  = "eyJhbGciOiJSU0EtT0FFUC0yNTYiLCJlbmMiOiJBMjU2R0NNIiwiaWF0IjoxNTUwMDYzMTczfQ.WRy07IjIkJ5a2f6Fl..."
)

func main() {

	privateKeyBytes, err := base64.StdEncoding.DecodeString(clientPrivateKey)
	if err != nil {
		panic(err)
	}

	privateKey, err := x509.ParsePKCS8PrivateKey(privateKeyBytes)
	if err != nil {
		panic(err)
	}

	encryptedJwe, err := jose.ParseEncrypted(jwe)
	if err != nil {
		panic(err)
	}

	decrypted, err := encryptedJwe.Decrypt(privateKey)

	fmt.Println("response: ", string(decrypted))
}

```

**Related Information**  


[Encrypting Payloads](encrypting-payloads-7202e7a.md "SAP Credential Store provides payload encryption, which is enabled by default.")

