# Question pour Mikaël
## Role
## Facture Individuelle
### [AGD-1713](https://extranet.artal.fr/jira-ng/browse/AGD-1713) Rapport détaillé sur les factures individuelles
rapport de stats
- Que fait exactement cet export ? A quoi il sert ? Peut on le remplacer par l'export xlsx?
- A ajouter au dashboard ?
## Report
### [AGD-1620](https://extranet.artal.fr/jira-ng/browse/AGD-1620) Lister les montants archivés non facturés
- comment gère t on les reports crées dans le cadre d'un rôle que l'on désarchive? on doit le réintégrer (débrancher de l'usager...)?
=> on peut bloquer le désarchivage si report crée + ajout d'une modale de warning
- groupage par report ou par usager? => démo
## Echeancier
## Facture
On peut ajouter deux bouttons:
    - un bouton pour charger le paramétrage par défaut (de la facturation)
    - un bouton pour sauver en tant que paramétrage par défaut (de la facturation)
De la même façon on peut ajouter un bouton pour générer une valeur dynamique à l'aide de la date de payement
TIP SEPA sur la facture moderne uniquement ?
## Ligne optique
code période: c'est un Int compris entre 0 et 9 ? 
Toujours à 1 non modifiable pour TIPSEPA?
dans les autres cas modifiable dans la modale de param.

RETOURS
facture
    zone TIP SEPA
        le texte du bloc "Montant prélèvement sepa..." doit être justifié (aligné droite et gauche)
        l'étoile parait pas au bon endroit
        l'ajustement de la zone TIP ne doit apparait que si TIP actif
    pleins d'erreurs dés que je change le param
    hauteur TIP SEPA 9 chez nous contre 8
    ### trop haut
    METER
        pas de template classique
param flux ORMC
    si tip sepa => code période à un non éditable
    sinon champs modifiable classique
FI
    modèle de facture simplifié par rapport à celui de la facture normale
tarif
    scenario de mika
        on change le prix d'un tarif la valuer doit être modifié partout sans que la quantité soit modif

daily
