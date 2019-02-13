# Ansible, docker, docker-compose
### Recherche et etat de l'art

---

## Objectifs

- push-to-deploy / automatisation en CI |
- notifications durant les phases deploy, |
- backups pre-deploy, |
- rollback automatique |
- chiffrement de variables secretes |

---

## Principes generaux

- ansible: automatisation au travers de ssh, |
- docker: ecosysteme complet de gestion de containers, |
- docker-compose: gestion de grappes de containers via fichier de conf |

---

## Example docker-compose

---?code=docker-compose.yml&lang=yaml&title=Docker-compose.yml example

@[1](Declaration de la version de docker-compose)
@[2](Declaration d'un dictionnaire de services)
@[3](Declaration du service web)
@[4](L'image se construit a partir du Dockerfile du dossier)
@[5-6](Le container web doit demarrer apres db)
@[7-8](Le container web expose un port)
@[9](Declaration du service db)
@[10](Le container db utilisera une image specifique)

---

## docker-compose.yml

- avantage: definition de multiples services au sein du repo, ala k8s |
- avantage: prevu pour un usage manuel, sans CI, en SSH |
- inconvenient: prevu pour un usage manuel, sans CI, en SSH |
- inconvenient: ne sait rien faire d'autre que des containers |
- inconvenient: il faut modifier le fichier pour faire des trucs sympas |

---

## Et les trucs sympas ?

- deport du build de l'image en CI |
- afin de tester celle-ci avant le deploiement |
- de pouvoir la deployer sur differents environnements avant la prod |
- automatiser le rollback |

---

## Ansible et le module docker

---?code=ansible.yml&lang=yaml&title=Ansible tasks example

---

## Ansible

- inconvenient: plus rigide en terme d'infra |
- avantage: automatisable en ssh |
- avantage: chiffrement de variables d'inventaire |
- avantage: des centaines de modules sympas ie. pour les notifs slacks |
- avantage: permet toute sorte d'introspection sur l'image |
- inconvenient: plus complexe |

---

## Ansible peut aussi bien automatiser du compose
