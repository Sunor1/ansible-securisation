# ansible-securisation

Playbook Ansible de durcissement SSH et d'installation de bind.

## Ce que fait le playbook

- limite la connexion SSH au seul utilisateur `ansible` venant de `srv-ansible` (10.81.50.62)
- verrouille le mot de passe de l'utilisateur `ansible` (connexion par clé uniquement)
- installe et active le service `bind` (`named`)

## Prérequis

- Oracle Linux 10, ansible-core 2.16
- inventaire configuré (`/etc/ansible/hosts`) avec les postes cibles
- utilisateur `ansible` avec sudo sans mot de passe et clé SSH déployée

## Utilisation

    ansible-playbook securisation.yml --syntax-check
    ansible-playbook securisation.yml --check --diff
    ansible-playbook securisation.yml --limit staging
    ansible-playbook securisation.yml

## Attention

Testez toujours sur un seul poste (`--limit`) avant de généraliser : une erreur dans la
restriction SSH peut vous verrouiller hors de la machine.

## Licence

MIT, voir le fichier `LICENSE`.
