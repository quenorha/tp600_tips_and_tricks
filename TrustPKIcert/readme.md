The TP600/WP400 Qt webbrowser is based on Chromium, which uses NSS Shared DB for certificate management.
https://chromium.googlesource.com/chromium/src/+/master/docs/linux/cert_management.md

certutil tool from the libnss3-tools must be used to manage certificates. 
This utility is not natively part of the standard FW, but it can be used within a docker container. 
quenorha/nsstools image can be used for this purpose, or you can build yourself using the provided Dockerfile.
Docker activation will be necessary just for the time to install the certificate.

1) Activate Docker (via WBM or via the command below)

```/etc/config-tools/config_docker activate```

3) Transfer the Root CA certificate (PEM format, .crt extension) to the screen file system, via SFTP for example.
To be placed in /root/root-ca.crt for the example

4) Install the certificate in the NSS database.

```docker run --rm -it -v /root/root-ca.crt:/root/root-ca.crt -v /root/.pki/nssdb:/root/.pki/nssdb quenorha/nsstools certutil -A -n "RootCA" -t "TC,," -d sql:/root/.pki/nssdb -i /root/root-ca.crt```

4) Verify certificate installation
   
```docker run --rm -it -v /root/.pki/nssdb:/root/.pki/nssdb quenorha/nsstools certutil -L -d /root/.pki/nssdb```

Expected result:

```Certificate Nickname Trust Attributes
SSL,S/MIME,JAR/XPI

RootCA CT,,
```
5) Connect with the browser. Proceed as usual. There should be no warning when connecting, even in Browser Security mode "High"
To check the certificate information, activate the developer tools (see dev-tools folder).
Once the developer tools are activated on the page to be tested, go to the Security tab (a refresh of the page may be necessary). The page should appear as secure (green padlock).

6) Disable Docker (via WBM or via command below)

```/etc/config-tools/config_docker remove```
