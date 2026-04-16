

# 2, # 3 calcul des empreintes pour le fichiers , et le resultats de chacune : 
md5sum LICENSE_TP2.txt
fd2e43e60443506fec69587e5ff60dea 

sha1sum LICENSE_TP2.txt
1809a4a8351c8e958245a52a2c2818a11b290001


sha256sum LICENSE_TP2.txt
c87f53528453580ab5cc0ada9b2f1ff2f3a8e246481ea918abd18df5b084f876





# 4 ,calcul de taille 
on calcule la taille de chaque empreinte
puisque le resultat est en héxadécimal alors la taille est égale au nombre de caractères * 4

fd2e43e60443506fec69587e5ff60dea 
taille= 32*4= 128 bits 


taille= 40*4=160 bits 
1809a4a8351c8e958245a52a2c2818a11b290001

taille=64*4=256 bits 
c87f53528453580ab5cc0ada9b2f1ff2f3a8e246481ea918abd18df5b084f876

# 5 , fichier modifié , un caractère est ajouté


md5sum LICENSE_TP2.txt
6461bdb60b15f20e72f351c93bc7275b  
l'ancienne valuer :
fd2e43e60443506fec69587e5ff60dea 

sha1sum LICENSE_TP2.txt
3128d9986fea5eef9866959e16f12295383e1e02  
l'ancienne valeur:
1809a4a8351c8e958245a52a2c2818a11b290001


sha256sum LICENSE_TP2.txt
a853bfcad997f8c353f62de87ef0c558eb4afbf6f5b963123f551631bf6ad7a5  
l'ancienne valeur:
c87f53528453580ab5cc0ada9b2f1ff2f3a8e246481ea918abd18df5b084f876



# on constate que avec une différence d'un seul caractère les clées préceèdentes sont totalement diffirentes avec les nouvelles 

# c'est ici l'utilité des empreintes elle nous permet de verifier l'intégrité des données ou si elle ne sont pas modifié pendant leur chemin vers la destination 




# 6: 

parmi les 3 methodes MD5, SHA-1, SHA2 , la meilleure est  SHA2  car :

MD5: sa taille est petite et il a une faible cryptographique interne relativement ,  donc plus vulnérable aux collisions , c'est à dire  deux fichiers pourront avoir la meme empreinte


SHA-1: sa taille est aussi petite par raport à SHA-2, donc aussi vulnérable aux collision , en plus il existe des attaques qui le casse comme SHAttered attack , qui depuis sa découverte SHA-1 est abondonné


SHA-2:
sa taille est plus longue que les deux autres , collisions très difficile , et aucune attaque connue qui le casse jusqu'à aujourdhui 
donc SHA-2 résiste plus , et en plus c'est le standard actuel .
