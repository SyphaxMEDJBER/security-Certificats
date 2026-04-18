# Exercice 2 - Certificats et GPG

## Objectif

Cet exercice présente une mise en pratique de **GnuPG (GPG)** dans un contexte d'échange sécurisé entre deux utilisateurs, **Alice** et **Bob**.

Les manipulations réalisées couvrent :

- la génération de paires de clés ;
- l'export et l'import de clés publiques et privées ;
- le transfert de clés entre deux machines ;
- le chiffrement d'un fichier pour un destinataire ;
- la signature numérique d'un message ;
- la combinaison **signature + chiffrement**.

## Contenu du dossier

Le dossier est organisé par questions avec les traces de commandes, les fichiers générés et plusieurs captures d'écran.



## Outils utilisés

- `gpg` / `gpg2`
- `scp`
- deux machines virtuelles ou postes simulant **Alice** et **Bob**

## Résumé des manipulations

###  Génération des clés

Une paire de clés RSA 2048 bits est créée pour Alice, puis une autre pour Bob.


###  Export des clés

Les clés sont exportées afin de pouvoir être échangées entre les deux utilisateurs.

```bash
gpg --export -a "alice" > AlicePubKey.gpg
gpg --export-secret-keys -a "alice" > AlicePrivKey.gpg
```

Même principe pour Bob.

### . Transfert des clés

Les clés publiques sont transférées avec `scp` d'une machine à l'autre, puis importées dans le trousseau local.


###  Chiffrement

Alice chiffre un fichier pour Bob à l'aide de la **clé publique de Bob**. Bob peut ensuite le déchiffrer avec sa **clé privée**.



###  Signature numérique

Alice signe un message afin que Bob puisse vérifier son authenticité et son intégrité.



### . Signature et chiffrement

Enfin, le fichier est à la fois signé par Alice et chiffré pour Bob.



## Résultats attendus

À la fin de l'exercice, on montre que :

- Bob peut lire uniquement les fichiers chiffrés pour lui ;
- Bob peut vérifier qu'un message signé provient bien d'Alice ;
- la signature garantit l'authenticité et l'intégrité ;
- le chiffrement garantit la confidentialité.


