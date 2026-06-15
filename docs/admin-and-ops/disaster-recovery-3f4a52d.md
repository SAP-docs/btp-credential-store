<!-- loio3f4a52dd01eb47098110a10d6a200ccd -->

# Disaster Recovery

SAP Credential Store service provides the possibility to recover credentials from a remote backup in another region. This can be requested when SAP has officially declared a disaster event for a certain region.

To trigger the recovery process, open an incident \(ticket\) to component `BC-CP-CF-SEC-CPG` and provide the following information:

-   Source service instance and region
-   Target service instance and region

-   List of credentials, which must include full credential parameters: namespace, credential type \(password, key, keyring\), credential name.

