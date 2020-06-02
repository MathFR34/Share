# Math - Partages pêle-mêle

Cet espace est prévu pour mettre à dispo des fichiers sur lesquels je réalise des tests
  - Graylog
  - OpenDistro (ELK)
  - ...

# OpenDistro + LDAP

Le docker-compose;yml contient la stack elk et le container LDAP.

```sh
$ docker-compose up
```

Si on souhaite simplement lancer le container LDAP sans docker-compose il suffit de faire :

```sh
$ docker run -p 389:389 --name ldap-service --hostname ldap-service --env LDAP_ORGANISATION="math" --env LDAP_DOMAIN="math.lab" --env LDAP_ADMIN_PASSWORD="admin" --env LDAP_TLS=false --env LDAP_CONFIG_PASSWORD="config" --env LDAP_BASE_DN="dc=math,dc=lab" --detach osixia/openldap:1.3.0
```

### Test du LDAP
Pour test
```sh
$ docker exec ldap-service ldapsearch -x -H ldap://localhost -b dc=math,dc=lab -D  "cn=admin,dc=math,dc=lab" -w admin
```
# Share
 
