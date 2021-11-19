# TP numéro 9

## Objectif:

Utiliser un handler pour redémarrer un service que si le contenu d’un fichier a changé

## Besoin:

- Créer un folder *files*
- Copier le fichier `/etc/nginx/nginx.conf` depuis *server-0.scc-edu* dans files
- Editer le fichier `files/nginx.conf` pour y ajouter un commentaire
- Modifier le playbook *nginx.yaml* pour copier (module copy) le fichier *nginx.conf* sur les machines cible
- Ajouter un *handler* pour redémarrer le service *nginx* si le contenu du fichier *nginx.conf* a changé
- Jouer 2 fois le playbook *nginx.yaml*