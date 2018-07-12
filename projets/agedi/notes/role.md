# Role
### [AGD-1905](https://extranet.artal.fr/jira-ng/browse/AGD-1905) Role: Archivage du rôle
- Que reste il encore à faire sur cette tache exactement? déjà fait?

# ROLE METER

Sur l'écran des roles, on selectionne toujours des compteurs (Element de facturation) quelque soit le paramétrage du mode de facturation. La différence de traitement se fait lors du calcul.

En mode de facturation ABONNE, le role sera associé à des CaptureAbonné (qui auront elles même des CapteurElementDeFacturation).
```
	   /CE2F1
RA1-CA1-CE2F2
	   \CE2F3
```

En mode de facturation COMPTEUR, le role sera associé à des CaptureCompteur
```
   /CE2F1\
RC1-CE2F2-CA1
   \CE2F3/
```

# Echeancier
[Modèle UML](https://www.draw.io/#G1MaCw4H0lNZ37uV7A7qDZyhgezCoNXOBi)

## Tasks
### [AGD-1904](https://extranet.artal.fr/jira-ng/browse/AGD-1904) Echeancier: Calcul du rôle des mensualisés
calcul du rôle avec échéancier
Il faut bloquer la mise en attente.
précision à confirmer:
- ne concerne que les usagers en prélèvement auto => oui
- une fois les usagers selectionnés dans le premier rôle du cycle, les usagers peuvent quitter ce cycle mais plus le rejoindre. On ne peut plus réintégrer le cycle de l'échéancier, on doit attendre le prochain. => oui

Qs
- on ne gère qu'un seul échéancier par facturation? on ne peut pas avoir en parallèle un échéancier pour des localités différentes. => oui
- on pourrait avoir un bouton ou une checkbox pour déclencher la régul sur un rôle? ça ne serait pas plus cher et ça parait plus souple non ? impacts? => on prévoit la regul à l'avance comme dans le logiciel précedent

### [AGD-1491](https://extranet.artal.fr/jira-ng/browse/AGD-1491) Echeancier: Edition des échéanciers global
Exporter jasper des échéances pour chaque usager. Datagrid dans une modale dans le role des echeanciers.

### [AGD-1698](https://extranet.artal.fr/jira-ng/browse/AGD-1698) Echeancier: Détail échéancier [(maquette)](https://www.figma.com/file/L4SFjFKb7NOE4jqlZWGMGttH/Maquettes?node-id=7596%3A7135)
- Afficher le détail des échéances d'un usager: ok
- Possibilité d'éditer l'échéancier
    - on peut recalculer en prenant le courant comme base avec controle des article/code produit négatif
- Générer et éditer une facture de régularisation: ok
- Exclure un usager des prochaines échéances: à l'aide de FI uniquement ?
pas de FI, juste exclure des prochains cycles.

Questions:
- Par où accéder à cet écran? Nouvel onglet usagers?
=> nouvel onglet fiche usager
- Comment marquer les échéances déjà facturées?
en vert ou coché, trois état: facturé, en cours, à venir
- Export pdf toujours utile?
export dela datagrid si elle gère un état sand détail par défaut.
- Quand un usager change le mode de prelèvement (échéancier => échéance) comment on gère les échéances prévu ?
    on averti qu'il y a une écheance en cours et on propose trois choix:
        on ne fait rien (annulation)
        on le sort du cycle et on désactive
        on ne le sort pas du cycle mais on désactive
- a t on besoin d'afficher le détail des QPT? Si on afficher uniquement la somme est ce suffisant ? => oui (par article/code produit)
- Créer FI: prérempli avec les données courantes présencte dans le tableau ? si oui, comment ? pas de FI

### [AGD-1494](https://extranet.artal.fr/jira-ng/browse/AGD-1494) Echeancier: Liste des échéanciers
Besoin NG:
Ce formulaire permet d’éditer (export PDF) les échéanciers de certains usagers ou de tous les usagers.

dans le role on coche les usagers pour lesquel on veut imprimer les echéanciers.

### [AGD-1536](https://extranet.artal.fr/jira-ng/browse/AGD-1536) Echeancier: Etat de la mensualisation
Etat récapitulatif des échéances en cours.
Cet écran décrit toutes les échéances prévu suite au calcul des rôles de prélèvements à l'échéance.
Dans cet écran on doit pouvoir visualiser pour chaque échéances :
- numéro de l'échéance: ok
- date du prélèvement: ok (prévu lors de la création de l'échéancier)
- date de création du flux de liaison (ORMC ou PES Titre): porté par le rôle associé
- nombre de personnes prélevés: dans le rôle
- montant total prélevé: dans le rôle
- état de l'échéance (passée ou future): rôle présent ou pas + état du rôle
- pour les échéances passées mettre un lien vers le rôle archivé: ok
- Ces informations doivent pouvoir être exportées (PDF ou XLS) => xls natif de la datagrid suffisant

### [AGD-1533](https://extranet.artal.fr/jira-ng/browse/AGD-1533) Echeancier: Annuler le cycle de mensualisation
Supprimer les échéances prévisionnel ainsi que tous les rôles associé.
Le but est de pouvoir annuler un cylce complet de prélèvement avec échéancier.
Cette action est disponible uniquement pour l'opérateur AGEDI.
Cette action est enregistrée dans le journal des manipulations.
Un message de validation permet de valider et lancer l'action.
- efface tout l'échéancier? On revient dans l'état ou l'on recommence un nouveau cycle? ie on renseigne la date de première échéance?
=> oui
- peut on faire l'annulation si la première échéance a été traité?
=> oui

### [AGD-1695](https://extranet.artal.fr/jira-ng/browse/AGD-1695) Echeancier: Recalculer l'échéancier
- Recalculer l'échéancier d'un usager: à partir des nouvelles valeurs courantes de l'usagers on échelonne sur les échéances restantes? => oui
- Annuler une échéance: on reprend la base de calcul pour l'échelonner sur les échéance restante ? => oui
- Recalculer les échéanciers en fonction des tarifs appliqués aux usagers: quelle différence avec la première ligne ? pareil
- la différence se fait sur la gestion des code produit negatifs qui sont interdit pour l'export du flux

### []()
### []()
### []()
## Workflow
- création role 0
    - renseigner date de prélèvement
        prévoir les dates des autres rôles (nombre + période) => échéancier

    - associer les contrats
        - comment on gère les contrats non présent?
            - calculer les valeurs prévisionnelles de chaque échéances pour chaque contrat=> échéanciers
            - capturer les valeurs des index
        - facturer le role
            - création d'un acompte pour chaque contrat
                - acompte modifiable? annulable? (comme report?)
            - acomptes consultables?
- création rôle 1
    - détecter que l'on est sur le rôle 1 ()
        - date de prélèvement déjà fixé
        - selection des contrats déjà fixé ?
            - sauf exclusion des nouveaux en FI ?
            - ajout de nouveaux ?
        - montants déjà fixé?
            - recalcul possible ?
            - reporter modifier une échéance => chaque contrat doit porter son échéancier
            - annulé une échéance passé ? (qu'est ce que ça veut dire?)
- consulter échéancier global
    dates + nombre des rôles prévu
- consulter échéancier / contrat
    montant date et nombre de role prévu

# Role Meter Classique
## En mode "facturation par compteur":
L'élément à afficher dans la datagrid est l'element de facturation (EF). On crée une facture par EF (potentiellement plusieurs par abonné)

## En mode "facturation par abonné":
- UI
    - on affiche la datagrid avec du grouping par abonné
    - (si possible) on tweak la sélection pour que lors de la selection d'un élément de facturation, tous les éléments de facturation pour un même abonné se coche aussi
- Calcul
    - on ne crée qu'une facture de rôle par abonné

NUMEROTATION

dernier numéro de [facture/bordereau/titre/role]
compteur pour facture/role dans la facturation
pour facture/titre increment par facture (titre selon param)