# TP1

**Nom et Prénom :** ABDELLAOUI HAJAR

---

## Table des matières

1. [Exercice 1 — codePIN](#exercice-1---codepin)
2. [Exercice 2 — échange de deux variables](#exercice-2---echange-de-deux-variables)
3. [Exercice 3 — PGCD (itératif et récursif)](#exercice-3---pgcd-it%C3%A9ratif-et-r%C3%A9cursif)
4. [Exercice 4 — Diviseurs (méthode 1 et 2)](#exercice-4---diviseurs-m%C3%A9thode-1-et-2)
5. [Exercice 5 — Jeu (deviner un nombre)](#exercice-5---jeu-deviner-un-nombre)
6. [Exercice 6 — Triangle de Floyd](#exercice-6---triangle-de-floyd)
7. [Exercice 7 — Somme des entiers (itératif et récursif)](#exercice-7---somme-des-entiers-it%C3%A9rative-et-r%C3%A9cursive)
     
### Exercice 1 — codePIN
```pseudocode
 ALGORITHME codePIN
     
         CONST pi=0000:ENTIER
         VAR pin,c:ENTIER
 DEBUT 
        c <-- 0                                           1
       Repeter
               ecrire("Saisir le code PIN :")             1        donc le pire du cas on a T(n)=1+9*3+2 = 1+27+2 = 30
               lire(pin)                                  1
               c<--c+1                                    2
               Si(pin=pi)Alors                            1
                    ecrire("Succés")                      1
               Sinon
                    Si(c<3)Alors                          1
                         ecrire("Erreur")                 1
                    Sinon
                          ecrire("Blockage")              1
                    Fin Si
               Fin Si
       Jusqua(c=3 ou pin=pi)                              2
 FIN
 ```

### Exercice 2 — échange de deux variables
```pseudocode
 ALGORITHME chanementdedeuxvariable
         VAR a,b,c:REEL
 DEBUT
       ecrire("Entrer le premiére variable:")             1
       lire(a)                                            1
       ecrire("Entrer le deuxiéme variable:")             1         donv le pire du cas on a T(n)=1+1+1+1+1+1+1+1+1=9
       lire(b)                                            1            
            c<--a                                         1
            a<--b                                         1                                          
            b<--c                                         1
       ecrireln("le premiére variable est :",a)           1
       ecrire("le deuxiéme variable est :",b)             1
 FIN
```

### Exercice 3 — PGCD

#### 1) PGCD itératif
```pseudocode
 ALGORITHME PGCD
          VAR a,b,r:ENTIER
 DEBUT
       ecrire("Donner deux nombre")                       1
       lire(a,b)                                          1
     Tantque(b!=0)Faire                                   1
            r<--a mod b                                   2     donc le pire du cas on a T(n)=1+1+(1+2+1+1)*n+1 = 3+5n
            a<--b                                         1
            b<--r                                         1
     FinTantque
        ecrire("le PGCD est :",a)                         1
 FIN
 ```

 #### 2) PGCD récursif
 ```pseudocode
 ALGORITHME PGCDrecursive
          VAR a,b,r:ENTIER
          Fonction PGCD-recursif(a,b)
             Si (b=0)Alors                                1
                   retourne a                             1
             Sinon
                   retourne PGCD-recursif(b,a mod b)              donc le pire du cas on a T(n)=(1+1)*n+1+1+2 = 2n+4
             Fin Si
          FinFonction
  DEBUT
        ecrire("Entrer les 2 nombres":)                   1
        lire(a,b)                                         1
        ecrire("le PGCD est:,PGCD-recursif(a,b))          2
 FIN
```

### Exercice 4 — Diviseurs

#### Méthode 1 

```pseudocode
 ALGORITHME divmethode1
          VAR n:ENTIER
       Fonction donnerdiviseurs1(n:ENTIER):ENTIER        
                 VAR b:ENTIER                             
         Pour b de 1 á n pas 1 Faire 
                Si(n mod b=0)Alors                        2          donc le pire du ces on a T(n)=(2+1)*n+1+1+2 = 3n+4
                    ecrireln(b)                           1
                Fin Si
         FinPour
       FinFonction
 DEBUT
       ecrire("Entrer votre chifre":)                     1
       lire(n)                                            1
       ecrire("les diviseurs de",n,"est:",donnerdiviseurs1(n))  2
 FIN
 ```

#### Méthode 2 — parcourir jusqu'à racine(n)
```pseudocode
 ALGORITHME divmethode2
         VAR n:ENTIER
     Fonction donnerdiviseure2(n:ENTIER);ENTIER
             VAR b:ENTIER
             n<--racineCarree(n)                          1
       Pour b de 1 á n pas 1 Faire
             Si(n mod b =0)Alors                          2
                 ecrireln(b)                              1
                 ecrire(n/b)                              1       donc le pire du cas on aT(n)=1+(2+1+1)*n+1+1+2 = 5+4n
             Fin Si
       FinPour
     FinFoction
 DEBUT
       ecrire("Entrer votre chifre":)                     1
       lire(n)                                            1
       ecrire("les diviseurs de",n,"est:",donnerdiviseurs2(n))  2
 FIN
```

### Exercice 5 — Jeu (deviner un nombre)

```pseudocode
 ALGORITHME Game
          VAR b:ENTIER
             choix:CHAINE
          CONST n=aléatoire(1,100):ENTIER
      Procedure jeux(n:ENTIER,b:ENTIER)
                 VAR tentative:ENTIER
              tentative<--0                                             1
            Repeter
               tentative<--tentative + 1                                2                               
                   Si(n=b)Alors                                         1
                      ecrire("Félicitation")                            1
                   Sinon
                      Si(b<n)Alors                                      1
                          ecrire("Trop petite")                         1
                      Sinon
                         Si(n<b)Alors                                   1
                             ecrire("Trop grand")                       1
                         Sinon
                            Si(tentative=5)Alors                        1        donc le pire du cas on a T(n)=1+(2+1+1+1+1+1+1+1+1+2)*n+(1+1+1+1+1+1)*n
                                 ecrire("La réponse est:",n)            1                                     =1+12n+6n = 18n+1
                            Fin Si
                         Fin Si
                      Fin Si
                   Fin Si
            jusqua(tentative=5 ou n=b)                                  2
      FinProcedure
 DEBUT 
       Repeter
          ecrire("Entere un nombre:")                                   1
          lire(b)                                                       1
          jeux(n,b)                                                     1
          ecrire("Rejouer oui/non ?")                                   1
          lire(choix)                                                   1
       Jusqua(choix=non)                                                1
 FIN
```

### Exercice 6 — Triangle de Floyd

```pseudocode
 ALGORITHME triangledeFloyed
         VAR n,i,j:ENTIER
      Procedure triangle-Floyed(n:ENTIER)
         VAR nb:ENTIER
           nb<--0                                                       1
        Pour i de 1 á n pas 1 Faire
               Pour j de 1 á i pas 1 Faire                                      donc lr pire du cas on a T(n)= 1+((1+2)n)n+1+1+1
                      nb<--nb + 1                                       2                                    = 1+(3n)n+3
                      ecrire(nb)                                        1                                    = 4+4n^2
               FinPour
                      ecrireln                                          1
        FinPour
 DEBUT
         ecrire("Entrer le nombre de ligne")                            1
         lire(n)                                                        1
         triangle-Floyed                                                1
 FIN
```

### Exercice 7 — Somme des entiers

#### 1) Itératif

```pseudocode
 ALGORITHME Sommedesentiers
          VAR n,s,i:ENTIER 
 DEBUT 
         S<--0                                                          1                                                        
     Pour i de 1 á n pas 1 Faire
        S<--S + 1                                                       2      donc le pire du cas on a T(n)= 1+2*n+1+1+1
     FinPour                                                                                                = 4+2n
         ecrire("Entrer un nombre")                                     1
         lire(n)                                                        1
         ecrire("La somme des entiers de 1 á",n,"est:",S)               1
 FIN
```

#### 2) Récursif

```pseudocode
 ALGORITHME Sommedesentiers
         VAR n:ENTIER
     Fonvtion Somme(n:ENTIER)
         Si(n=1)Alors                                                   1
             retourne 1                                                 1
         Sinon                                                                 donc le pire du cas on a T(n)=(1+1+2)*n+1+1+2
             retourne n + Somme(n-1)                                    2                                   =4n+4
 DEBUT
        ecrire("Entrer un nombre :")                                    1
        lire(n)                                                         1
        ecrire("la somme es entiers de 1 á",n,"est:",Somme(n))          2
 FIN
 ```