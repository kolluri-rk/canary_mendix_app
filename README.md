# canary_mendix_app

This is a sample mendix app that runs on TAS. 

## employee-directory connecting to MySQL

Deployment steps:  

- Create mysql service `cf create-service p.mysql db-small employee-directory-mysql`
- Wait for service to finish provisioning
- Create a service key `cf create-service-key employee-directory-mysql creds`
- Get servive key info `cf service-key employee-directory-mysql creds`
- Replace mysql environment varibales in `manifest-mysql.yml`
- Push the app `cf push -f manifest-mysql.yml`


## employee-directory connecting to MySQL and load mendix variables from config sever

Deployment steps:  

- create mysql service `cf create-service p.mysql db-small employee-directory-mysql`
- Wait for service to finish provisioning
- Create a service key `cf create-service-key employee-directory-mysql creds`
- Get servive key info `cf service-key employee-directory-mysql creds`
- Replace mysql environment varibales in https://github.com/kolluri-rk/pcfapps-configrepo/blob/master/employee-directory-a1.yml
- create config server service `cf create-service p.config-server standard config-server -c gitconfig.json`
- Push the app `cf push -f manifest-mysql-configserver.yml`


## References:
- https://github.com/mendix/cf-mendix-buildpack
- https://github.com/macsux/config-server-buildpack
- https://github.com/Pivotal-Field-Engineering/mendix-examples
