# cas-sample
Test CAS client webapp

Protocol URLs are linked to Shibboleth IDPv3 CAS protocol endpoints. See https://wiki.shibboleth.net/confluence/display/IDP30/CasProtocolConfiguration for additional details.

## Usage

- add parameters -Dcas.server.host=ce.gluu.info -Dcas.service.host=ce.gluu.info to webserver's JAVA_OPTS
- deploy

### HOWTO install cas-sample inside gluu-server:

Deploy cas-sample.war to /opt/gluu-server-2.4.4/

edit /opt/gluu-server-2.4.4/etc/apache2/sites-available/https_gluu.conf

add:

```
<Location /cas-sample>
        ProxyPass ajp://localhost:8009/cas-sample retry=5 disablereuse=On
        ProxyPassReverse ajp://localhost:8009/cas-sample
        Order allow,deny
        Allow from all
</Location>
```