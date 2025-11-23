# Decoupage_Reseau
Une société fictive a 4 pôles informatiques. Le réseau est en 172.16.1.0/24.
Découper ce réseau de 2 manières, symétrique et asymétrique, pour que chaque pôle ci-dessous puissent avoir assez d'adresse pour chaque équipement.
Le Pôle informatique (6 bureaux, environ 50 équipements au total)
Le Pôle développement (6 bureaux, environ 12 équipements au total)
Le Pôle Administratif (4 bureaux, environ 20 équipements au total)
Le Pôle Technicien (4 bureaux, environ 15 équipements au total)

RESULTAT

 **decoupage symetrique**     

- calcul
  
 - on divise le réseau en 4 sous réseaux egaux : 256 ÷ 4 = 64 adresses par sous réseau
 
 - 2 puissance n = 64 avec n qui est egale a  6 bits pour les hôtes
 
 - le  CIDR : 32 - 6 = /26 pour chaque sous réseau
 
 - Adresses utilisables : 64 - 2 = 62 adresses avec  (-2) pour l'adresse réseau et broadcast


| les pôles              | Plage_réseau    | cidr |  adresse_reseau | addresse_diffusion | total_addresse | adresses_utilisables | 
| ----------------- | --------------- | ---- | -------------- | ----------------- | ------------------ | ----------------------- | 
| **Informatique** 50  | 172.16.1.0/26   | /26  | 172.16.1.0     | 172.16.1.63       | 64                 | 62                      |             
| **Développement** 12  | 172.16.1.64/26  | /26  | 172.16.1.64    | 172.16.1.127      | 64                 | 62                      |             
| **Administratif** 20| 172.16.1.128/26 | /26  | 172.16.1.128   | 172.16.1.191      | 64                 | 62                      |          
| **Technicien**   15 | 172.16.1.192/26 | /26  | 172.16.1.192   | 172.16.1.255      | 64                 | 62                      |              

**decoupage asymetrique**

- calcul

 pôle informatique 50 équipements
- Besoin : 50 + 2 (réseau + broadcast) = 52 adresses minimum
- 2 puissance n ≥ 52 avec n = 6 et 2 puissance 6 = 64 adresses
- le cidr  : 32 - 6 = /26

 pôle administratif 20 équipements
- Besoin : 20 + 2 = 22 adresses minimum 
-  2puissance n ≥ 22 avec n = 5 et  2 puissance 5 = 32 adresses
- le cidr  : 32 - 5 = /27


| les pôles         | plage réseau    | cidr | masque          | adresse_reseau | adresse_diffusion | total_addresse | adresses_utilisables | 
| ----------------- | --------------- | ---- | --------------- | -------------- | ----------------- | ------------------- | ----------------------- | 
| **Informatique**  | 172.16.1.0/26   | /26  | 255.255.255.192 | 172.16.1.0     | 172.16.1.63       | 64                  | 62                      |
| **Administratif** | 172.16.1.64/27  | /27  | 255.255.255.224 | 172.16.1.64    | 172.16.1.95       | 32                  | 30                      |
| **Technicien**    | 172.16.1.96/27  | /27  | 255.255.255.224 | 172.16.1.96    | 172.16.1.127      | 32                  | 30                      | 
| **Développement** | 172.16.1.128/28 | /28  | 255.255.255.240 | 172.16.1.128   | 172.16.1.143      | 16                  | 14                      |            
