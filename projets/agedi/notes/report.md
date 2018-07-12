# Report
## [AGD-1620](https://extranet.artal.fr/jira-ng/browse/AGD-1620) Lister les montants archivés non facturés
- on affiche les objets reports de la base
- en cours
    - d'ajout: capture en attente d'ajout dans un role en cours (sera ajouter à l'archivage du rôle)
        - ne pas les afficher dans cette liste, les éléments d'un rôle qui n'est pas encoré archivé de va pas impacter l'état du système
    - de cloture: report en attente de cloture dans un role en cours (sera cloturer à l'archivage du rôle)
- bill: modèle déjà prêt
- meter: travailler sur le portage par le compteur (element de facturation?)
        - le report est une liste de capture de compteur (E2F) dans le cas de la factu par compteur et une capture d'abonné si factu par abonné
        - dans le cas où on bascule d'un type de factu à l'autre dans le param on aura un comptenu mixte (cas limite à pas forcement traiter en prio)
- questions:
    - on ne montre pas les report en cours d'ajout (encore dans un rôle non archivé)
## [AGD-1617](https://extranet.artal.fr/jira-ng/browse/AGD-1617) Modifier un montant archivé
- bill: modification de la QPT capturé
## Calcul des role avec minimum de facturation
- dans le paramétrage du rôle, on a un seuil montant et un seuil tva:
    - à quoi sert le seuil tva dans le paramétrage? à fixer le taux de tva pour le min à facturer
    - le seuil montant qu'on utilise est uniquement le TTC ? oui
    - qu'est qu'on fait si on désactive les minimums de facturation avec des reports en attente sur des usagers? 
    on prend en compte les reports existant sans en créer de nouveaux
- comment on gère les reports avec le recalcul/reinitialisation
    - quand est ce qu'on doit réellement ajouter/cloturer les reports? à l'archivage du rôle qui les contient/traite
