# Fix for the PKIX path building failed error #

In some cases java isn't able to use a  specific certificate issue onto an https connection that you require.
This will eventually lead to the "PKIX path building failed" or "unable to find valid certification path to requested target"

One possible solution is to export the certificate from firefox as a crt file and then import it with the keytool in java.

```bash
keytool -import -alias examplename -keystore  /etc/pki/java/cacerts -file /tmp/exporter-cert.crt
```

the pwd of the default keystore is _changeit_
once imported be sure to restart the jvm