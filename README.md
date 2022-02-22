# ---INSTRUCOES---
Instruções uteis referente as tecnologias utilizadas.

## Angular e Nodejs

Instalar [Angular CLI](https://cli.angular.io/)

Starter service: `ng serve` ou `npm start` <br/>
Navigate to `http://localhost:4200/`

Instalar [Json Server](https://www.npmjs.com/package/json-server)

Mocking backend: `json-server db.json` ou `node backend/server` <br/>
Navigate to `http://localhost:3000/`

### Generate JS from TS
Transpiling [TypeScript into JavaScript](https://code.visualstudio.com/docs/languages/typescript)
Command compiler `tsc -w`

### Generate Component

`ng generate component component-name` <br/>
`ng generate directive|pipe|service|class|guard|interface|enum|module` <br/>
`ng g c component-name --spec=false`

### Compilar e Testar

*1. Compilar (--extract-css=false evita erros de css)* <br/>
`ng build --prod --extract-css=false` 

*2. Testar Projeto Compilado* <br/>
`cd dist/` <br/>
`python -m SimpleHTTPServer 8080`

## Git e GitHub

*Após Instalar o Git:* <br/>
`git config --global user.name "Jean Alves"` <br/>
`git config --global user.email "jpralves10@gmail.com"` <br/>

*[Gerar SSH Key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)* <br/>
`ssh-keygen -t rsa -b 4096 -C "jpralves10@gmail.com"` <br/>
`Enter/Enter/Enter` <br/>
`cat id_rsa.pub`

*[Add SSH Key](https://github.com/settings/ssh/new)* <br/>
`Clicar no Botão "New SSH Key"` <br/>
`Add Título e a Chave`

*Push Repositório Existente* <br/>
`git init` <br/>
`git add .` <br/>
`git commit -m "first commit"` <br/>
`git remote add origin https://github.com/jpralves10/meat-app.git` <br/>
`git remote -v` <br/>
`git push origin master` <br/> 

*Git error: failed to push some refs to ...* <br/>
`git pull --rebase origin master` <br/>
`git push origin master`

*Status e Comitando:* <br/>
`git status` <br/>
`git commit -am "Arquivos comitados"` <br/>
`git log` <br/>
`git push origin master` ou `git push -f origin master`

*Comandos Uteis:* <br/>
`Entrar na Branch:` <br/>
`git checkout develop` <br/>
`Criar nova Branch:` <br/>
`git checkout -b feature-H6182-T7008-T7009` <br/>
`Atualizar Branch:` <br/>
`feature-H6182-T7008-T7009 >` <br/>
`git pull origin develop` <br/>

`Encontrar e Remover Artefato de Commit:` <br/>
`git reset --soft HEAD~[1..N] (exemplo)` <br/>
`git reset --soft HEAD~1` <br/>
`git rm -r src/main/resources/secure-credentials` <br/>

`git rm --cached -r .idea` <br/>

## Certificado OpenSSL

[Creating a SHA256 (SHA-1) self signed certificate for PingFederate](https://ping.force.com/Support/PingIdentityArticle?id=kA340000000GsWECA0) <br/>

*1. Generate certificate request using SHA256 (SHA-1)* <br/>
`openssl> req -nodes -sha256 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 3650` <br/>
    *`...`* <br/>
    *`A challenge password []:openssl`* <br/>
    *`An optional company name []:openssl`* <br/>
    
*2. Optional: Check to see if the CSR really has 256bit signatures* <br/>
`openssl> req -in cert.csr -text -noout` <br/>
    *`You should see “Signature Algorithm: sha256WithRSAEncryption”`* <br/>
    
*3. Create the certificate* <br/>
`openssl> req -x509 -days 365 -sha256 -in cert.pem -key key.pem -out my256.crt` <br/>

*4. Add my256.crt in GoogleChrome* <br/>
`Chrome Settings > Show advanced settings > HTTPS/SSL > Manage Certificates` <br/>

[Use a SHA-2 instead of SHA-1 certificate in PingFederate](https://ping.force.com/Support/PingIdentityArticle?id=kA340000000GsCdCAK) <br/>

## Certificado JDK

*Passo 1* <br/>
`openssl s_client -connect {Host}:443` <br/>

*Passo 2* <br/>
*Copiar e colar no certificado.cer <br/>
`do -----BEGIN CERTIFICATE-----` <br/>
`ate -----END CERTIFICATE-----`

*Passo 3* <br/>
`cd C:/Users/jpralves/kitdev/jdk1.8.0_111/bin >` <br/>
`./keytool.exe -keystore C:/Users/jpralves/kitdev/jdk1.8.0_111/jre/lib/security/cacerts` <br/>
`-import -alias DI4 -file C:/Users/jpralves/Desktop/Squad/cacerts/di4.cer` <br/>
<br/>
`Senha keystore: changeit`

*Passo 4* <br/>
`Confiar neste certificado? [n$o]: s`

*Passo 5* <br/>
*Listar os certificados adicionados: <br/>
`./keytool.exe -list -keystore C:/Users/jpralves/kitdev/jdk1.8.0_111/jre/lib/security/cacerts | grep DI4` <br/>
*ou <br/>
`./keytool.exe -list -keystore C:/Users/jpralves/kitdev/jdk1.8.0_111/jre/lib/security/cacerts`


## Spring-boot & Maven

Comandos Maven

*Instalar Dependências* <br/>
**`mvn clean install -U`**

*Executar Testes* <br/>
**`mvn test`**

*Build Project / Pasta target* <br/>
**`mvn package`**

*Build Project / Pasta target* <br/>
*>> no main manifest attribute, in app.jar* <br/>
**`mvn package spring-boot:repackage`**

*Executar App passando argumentos* <br/>
**`mvn spring-boot:run -Dspring-boot.run.arguments=--API_KEY=222`**

Aplication.properties <br/>
`api.key=${API_KEY:123}`

Link: `https://www.baeldung.com/spring-boot-command-line-arguments`

*Build Project Passando Variável* <br/>
**`mvn clean install package -Dlogging.starter=spring-boot-starter-logging`**

```
<exclusion>
  <groupId>org.springframework.boot</groupId>
  <artifactId>${logging.starter}</artifactId>
</exclusion>
```




































































