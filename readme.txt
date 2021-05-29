Simple script to perform basic CA tasks

1. Create and select CA directory
   # mkdir my_ca_folder
   # cd my_ca_folder

2. Prepare Micro-CA directory
   # ../main/action prepare

   This will create:
   * openssl configuration - <path>/.openssl.cnf
   * MicroCA configuration - <path>/.config
   * openssl-compliant CA database - <path>/ca_dir/*

3. Change config ot configure your defaults
   Set CRL/cert lifetimes and default DN component values
   # vi .config 

4. Generate root certificate
   # ../main/action init

5. Generate request
   # ../main/action req username username@domain.com

6. Sign request for a default lifetime
   # ../main/action sign requests/username-*.csr
   
   or sign for 37 days
   # ../main/action sign requests/username-*.csr 37

7. Revoke cert
   # ../main/action revoke certificates/username-*.crt

8. Update CRL
   # ../main/action crl
   # cp crl.pem /some/path/where/you/need

Env wars:
CONF_DIR - specify path to CA directory
REQ_CERT_DAYS - set certificate lifetime while creating request

