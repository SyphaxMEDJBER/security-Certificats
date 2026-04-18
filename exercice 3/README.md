# Exercice 3 - Création et signature de certificats avec OpenSSL

## Objectif

Cet exercice porte sur la création d'une infrastructure simple autour de **OpenSSL** :

- génération d'une paire de clés RSA ;
- extraction de la clé publique ;
- création d'une **CSR** (Certificate Signing Request) ;
- création d'une **autorité de certification locale (CA)** ;
- signature d'un certificat par cette CA ;
- lecture et analyse du certificat généré.

L'objectif est de comprendre le cycle de base d'un certificat X.509 et le rôle d'une autorité de certification.


## Outils utilisés

- `openssl genrsa`
- `openssl rsa`
- `openssl req`
- `openssl x509`

## Déroulement

### 1. Génération de la clé privée

Une clé privée RSA protégée par mot de passe est créée :

```bash
openssl genrsa -des3 -out myKey.pem 2048
```

Cette clé privée servira à créer la demande de certificat.

### 2. Extraction de la clé publique

La clé publique est ensuite extraite depuis la clé privée :

```bash
openssl rsa -in myKey.pem -pubout -out myPubKey.pem
```

### 3. Création de la demande de certificat

Une CSR est générée à partir de la clé privée :

```bash
openssl req -new -key myKey.pem -out myRequest.pem
openssl req -in myRequest.pem -text -noout
```

Cette demande contient notamment :

- l'identité du demandeur ;
- la clé publique ;
- une signature prouvant l'intégrité de la demande.

### 4. Création de l'autorité de certification

Une clé privée est créée pour la CA, puis un certificat autosigné est généré.

```bash
openssl genrsa -des3 -out CA.key 1024
openssl req -new -x509 -days 365 -key CA.key -out CA.crt
```

La CA joue ici le rôle d'entité de confiance qui signe le certificat du demandeur.

### 5. Génération de la CSR finale

Une demande de certificat au format `.csr` est créée :

```bash
openssl req -new -key myKey.pem -out myPubKey.csr
```

Le fichier `Q7 erreur.png` montre aussi une erreur utile : une **clé publique** ne peut pas être utilisée à la place d'une **clé privée** pour générer une CSR.

### 6. Signature du certificat par la CA

La CSR est ensuite signée par l'autorité de certification locale 

On obtient ainsi un certificat signé.

### 7. Vérification et lecture du certificat

Le certificat final est affiché et interprété avec :

```bash
openssl x509 -in myPubKey.crt -text -noout
```

Les éléments importants observés dans le certificat sont :

- `Issuer` : l'autorité qui a signé le certificat ;
- `Subject` : l'identité certifiée ;
- `Validity` : la période de validité ;
- `Subject Public Key Info` : la clé publique du sujet ;
- `Signature Algorithm` : l'algorithme utilisé pour la signature.



