# openssl-encryption-assignment
Encryption (OPENSSL)
C:\Users\HP>openssl version
OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)

C:\Users\HP>echo "This is a secret recipe, I'll love to revisit later" > message.txt

C:\Users\HP>openssl enc -aes-256-cbc -salt -in message.txt -out message.enc
enter AES-256-CBC encryption password:

Verifying - enter AES-256-CBC encryption password:

*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.

C:\Users\HP>openssl enc -aes-256-cbc -d -in message.enc -out decrypted.txt
enter AES-256-CBC decryption password:

*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.

C:\Users\HP>openssl genrsa -out private.pem 2048

C:\Users\HP>openssl rsa -in private.pem -pubout -out public.pem
writing RSA key

C:\Users\HP>openssl rsautl -encrypt -inkey public.pem -pubin -in message.txt -out message.rsa
The command rsautl was deprecated in version 3.0. Use 'pkeyutl' instead.

C:\Users\HP>openssl pkeyutl -encrypt -inkey public.pem -pubin -in message.txt -out message.rsa

C:\Users\HP>openssl pkeyutl -decrypt -inkey private.pem -in message.rsa -out decrypted_rsa.txt
