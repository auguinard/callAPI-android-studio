# SYMFONY 4 : LISTING DES LIGNES DE COMMANDES DE BASE

## Général ##

#### lister les commandes
```shell
php bin/console
```

#### avoir de l’aide sur une commande spécifique
```shell
php bin/console help (nom_commande)
```

## Cache ##

#### vider les caches
```shell
php bin/console cache:clear –env=prod
php bin/console cache:clear –env=dev
```

## Base de données ##

#### créer la base de données
```shell
php bin/console doctrine:database:create
```

#### mettre à jour / créer les tables
```shell
php bin/console doctrine:schema:update –force
```

## Entity ##

#### générer une entité
```shell
php bin/console make:entity Product
```

#### CRUD à partir d’une entité
```shell
php bin/console generate:doctrine:crud
```

## Controller ##

#### générer un contrôleur
```shell
php bin/console make:controller
```
ou
```shell
php bin/console make:controller –controller=BundleName:ControllerName
```

## Debug ##

#### déboger les routes
```shell
php bin/console router:debug
```

## Traduction ##

#### générer le fichier de traduction
```shell
php bin/console translation:update Locale BundleName –force
```

#### afficher les messages
```shell
php bin/console translation:update Locale BundleName –dump-messages
```

## Divers ##

#### installer composer
```shell
curl -s getcomposer.org/installer | php -d detect_unicode=Off
```

#### installer un composant via composer
```shell
php composer.phar update nom_du_composant
```

#### copier les fichiers publics des composants dans le dossier web
```shell
php bin/console assets:install –symlink web
```
