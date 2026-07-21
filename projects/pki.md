# Mini PKI Implementation

## Objective
Create, validate, and revoke certificates using OpenSSL.

## Tools
OpenSSL, PKI utilities

## Procedure
- Generate a openssl.cnf file with the necessary configuration for a CA and generate another one for intermediate CA.
- Generate a folder structure for a demo CA and intermediate CA, and add index.txt for root and intermediate manually.
```
mkdir demoCA
cd demoCA
mkdir certs
mkdir crl
mkdir newcerts
mkdir private
mkdir intermediate
Set-Content serial "1000"
Set-Content crlnumber "1000"
Set-Content ./intermediate/serial "1000"
Set-Content ./intermediate/crlnumber "1000"
cd ..
```
- Generate a root CA, key and certificate with extensions for CA usage, so we can use it to sign certificates for other CAs.
```
openssl req -new -x509 -config openssl.cnf -extensions v3_ca -keyout demoCA/private/rootCA.key -out demoCA/cacert.pem -days 3650
```
- Generate an intermediate CA, sign it with the root CA, and generate a certificate for it with extensions for CA usage.
```
openssl genrsa -out demoCA/intermediate/private/intermediate.key 4096
openssl req -new -key demoCA/intermediate/private/intermediate.key -out demoCA/intermediate/intermediate.csr -subj "/C=CA/ST=AB/L=Calgary/O=MyOrg/OU=Security/CN=Intermediate CA"
openssl x509 -req -in demoCA/intermediate/intermediate.csr -CA demoCA/cacert.pem -CAkey demoCA/private/rootCA.key -CAcreateserial -out demoCA/intermediate/intermediate.crt -days 1825 -extfile openssl.cnf -extensions v3_ca
```
- Generate server certificate, then sign it with the intermediate CA
```
openssl genrsa -out server.key 2048
openssl req -new -key server.key -out server.csr -subj "/CN=server.local"
openssl x509 -req -in server.csr -CA demoCA/intermediate/intermediate.crt -CAkey demoCA/intermediate/private/intermediate.key -CAcreateserial -out server.crt -days 825
openssl verify -CAfile demoCA/cacert.pem -untrusted demoCA/intermediate/intermediate.crt server.crt
```
- Generate a CRL for the root CA and intermediate CA, then revoke the server certificate and check the CRL.
```
openssl ca -config openssl.cnf -gencrl -out demoCA/crl/rootCA.crl
openssl ca -config openssl.cnf -gencrl -out demoCA/intermediate/crl/intermediate.crl
openssl crl -in demoCA/crl/rootCA.crl -noout -text
```
- Revoke the server certificate and generate a new CRL for the intermediate CA.
```
openssl ca -config openssl.cnf -revoke server.crt
```


## Findings
- Using an structure and configuration .cnf makes it way easier creating certificates.
- If your are on Windows, Set-Content is better than echo to create the files.
- OpenSSL does not include v3_ca by default, you must add -extensions
- Certificate chain validated correctly
- Revoked certificates rejected as expected

## Conclusion
Demonstrates understanding of PKI, CRL, OCSP and certificate trust.
