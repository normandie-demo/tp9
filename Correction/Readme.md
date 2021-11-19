# Correction TP 8


## Créer un folder *files*

```Shell
mkdir files
```

## Copier le fichier `/etc/nginx/nginx.conf` depuis *server-0.scc-edu* dans files

```Shell
scp server-0.scc-edu:/etc/nginx/nginx.conf files/nginx.conf
```

## Editer le fichier `files/nginx.conf` pour y ajouter un commentaire

Rajouter un commentaire sur la première ligne

## Modifier le playbook *nginx.yaml* pour copier (module copy) le fichier *nginx.conf* sur les machines cible

```yaml
  - name: Copy config
    ansible.builtin.copy:
      src: nginx.conf
      dest: /etc/nginx/nginx.conf
    notify: "Restart NGINX"
```

## Ajouter un *handler* pour redémarrer le service *nginx* si le contenu du fichier *nginx.conf* a changé

```yaml
  handlers:
  - name: Restart NGINX
    ansible.builtin.systemd:
      name: "{{ main_service }}"
      state: restarted
```
## Jouer 2 fois le playbook *nginx.yaml*

```Shell
ansible-playbook -i inventory nginx.yaml
```
