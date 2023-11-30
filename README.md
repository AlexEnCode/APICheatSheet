# CheatSheet API & Base de Données

# La Base de Données
### Chiffrement et cryptage

###### Cryptographie
La cryptographie désigne la discipline qui consiste à « crypter » les fichiers c’est-à-dire à sécuriser les serveurs et données (aujourd’hui), mais historiquement les messages. Le plus souvent, la cryptographie fait appel à différents codes, secrets ou clés de chiffrement.

###### Chiffrement des données
Le chiffrement des données consiste en l’utilisation d’une technique de cryptographie pour rendre un message clair illisible à l’aide d’une clé de chiffrement. Le principe fondamental est que cette clé doit être connue par le destinataire pour permettre le déchiffrement du message. En réalité, le processus est souvent plus complexe. Par exemple, le logiciel PGP de cryptographie permet de chiffrer et de déchiffrer des messages et des emails. Il utilise en réalité deux clés, une clé dite publique et une clé dite privée, chaque utilisateur ayant son propre « jeu » de clés.

###### Clé de chiffrement
La clé de chiffrement est le cœur du processus de chiffrement des données. Elle permet justement de chiffrer un fichier ou de le déchiffrer dans le sens inverse. Il existe plusieurs types de clé, et chaque appareil ou chaque utilisateur dispose en général de sa propre clé. L’enjeu devient alors souvent de gérer de multiples clés de chiffrement, ainsi que les révocations ou autorisations de nouveaux utilisateurs après l’envoi du message ou l’upload du fichier sur un cloud.

### Hashage et salage

 le hachage est une technique qui transforme une chaîne à l'aide d'un algorithme mathématique. La chaîne ainsi transformée ne sera pas compréhensible. Et contrairement à une chaîne cryptée, une chaîne ayant subi un hachage ne pourra pas être décodée. 


 Saler un mot de passe consiste à lui concaténer une chaîne de caractères avant de lui appliquer un algorithme de hachage. Pour que la technique soit efficace, il faut que chaque usager ait sa propre clé de salage, que cette clé soit générée aléatoirement et qu'elle soit aussi longue que possible. 

La clé de salage sera généralement stockée dans la base de données.
MySQL offre la fonction UUID() qui peut être utilisée pour générer une clé de salage. La clé générée avec UUID() n'est pas complètement imprévisible. Elle est cependant suffisamment aléatoire pour offrir le niveau de sécurité espéré.


### L' UUID

L'Universally Unique Identifier, est un identifiant unique universel. Il s'agit d'une chaîne de caractères utilisée pour identifier de manière unique une ressource ou une entité dans un système informatique, sans risque de conflit avec d'autres identifiants.

Les UUID sont généralement représentés par une séquence de 32 caractères hexadécimaux, divisée en cinq groupes séparés par des tirets. Par exemple, un UUID peut ressembler à ceci : 550e8400-e29b-41d4-a716-446655440000.

Les UUID sont générés de manière à minimiser les chances de collision, c'est-à-dire la probabilité que deux UUID soient identiques. Ils sont couramment utilisés dans les bases de données, les systèmes de fichiers distribués, et d'autres contextes où l'unicité des identifiants est essentielle.

### le concept de migration 

Le concept de migration de base de données fait référence au processus de modification de la structure d'une base de données ou de ses données, généralement dans le cadre d'une évolution logicielle ou d'une mise à jour de l'application. Les migrations de bases de données sont utilisées pour gérer les changements de schéma, les modifications de types de données, les ajouts de tables, et d'autres transformations nécessaires à l'évolution d'une application au fil du temps.

Voici quelques aspects clés liés aux migrations de bases de données :

Les migrations de bases de données permettent d'apporter des modifications au schéma de la base de données, telles que l'ajout, la suppression ou la modification de colonnes dans une table, la création de nouvelles tables, etc.

 Elles sont souvent associées à un système de versionnement. Chaque modification apportée à la base de données est associée à une version, ce qui permet de suivre l'évolution de la base de données au fil du temps.

Lorsque des modifications structurelles sont apportées à une base de données, il est important de garantir la cohérence des données existantes. Les migrations peuvent inclure des scripts pour transformer les données existantes afin de les adapter à la nouvelle structure.

Les migrations sont parfois conçues de manière réversible, ce qui signifie qu'il est possible de revenir à une version antérieure de la base de données si nécessaire. Cela est particulièrement important pour garantir la robustesse du processus.

 Il existe des outils dédiés qui facilitent la gestion des migrations de bases de données. Ces outils peuvent automatiser une partie du processus, réduisant ainsi le risque d'erreurs humaines et simplifiant le déploiement.

Les migrations de bases de données sont une pratique courante dans le développement logiciel, en particulier dans les applications qui évoluent rapidement. Elles permettent de mettre à jour la base de données de manière contrôlée et cohérente tout en préservant les données existantes.

# API

## Qu'est ce qu'une API

(interface de programmation d'application)
Les API sont des mécanismes qui permettent à deux composants logiciels de communiquer entre eux à l'aide d'un ensemble de définitions et de protocoles. Par exemple, le système logiciel du bureau météorologique contient les données météorologiques quotidiennes.

### l'Architecture `Client-Server`

L'architecture client-serveur est un modèle informatique qui divise les fonctions d'une application ou d'un service en deux parties distinctes : le client et le serveur. Ces deux parties communiquent entre elles pour fournir des services aux utilisateurs finaux. Voici une explication des concepts clés de l'architecture client-serveur :

Client :

Le client est l'interface utilisateur ou l'application qui interagit directement avec l'utilisateur final.
Il est responsable de la présentation des informations à l'utilisateur et de la collecte des entrées utilisateur.
Le client envoie des demandes au serveur pour obtenir des données, effectuer des opérations, ou recevoir des services.
Serveur :

Le serveur est une entité informatique qui détient les ressources et les données nécessaires pour fournir des services aux clients.
Il écoute les demandes des clients, traite ces demandes, effectue les opérations nécessaires, et renvoie les résultats aux clients.
Les serveurs peuvent gérer différentes tâches telles que le stockage de données, le traitement des requêtes, la gestion des connexions, etc.
Communication :

La communication entre le client et le serveur se fait généralement à l'aide de protocoles standardisés, tels que le protocole HTTP pour les applications web, le protocole SMTP pour les emails, etc.
Les clients envoient des requêtes au serveur, qui répond ensuite avec les données ou les résultats demandés.
Avantages de l'Architecture Client-Serveur :

La séparation des fonctions entre le client et le serveur permet une gestion plus efficace des ressources et des tâches.
Évolutivité : L'architecture client-serveur permet de mettre à l'échelle les ressources du serveur pour faire face à un nombre croissant de clients.
Réutilisation des Ressources : Les ressources serveur peuvent être partagées entre plusieurs clients, ce qui favorise la réutilisation et l'efficacité.


Client-Serveur Classique : Le client est généralement une application sur l'ordinateur de l'utilisateur, et le serveur est un système distant.
Client Léger / Serveur Lourd : Le serveur effectue la plupart des opérations de traitement, tandis que le client est responsable de la présentation et de la collecte des entrées utilisateur.
Client Lourd / Serveur Léger : Une application client plus complexe effectue une partie du traitement, tandis que le serveur fournit des services et des données.
L'architecture client-serveur est largement utilisée dans les systèmes informatiques modernes, des applications web aux réseaux d'entreprise et aux services cloud. Elle offre une structure flexible et évolutive pour répondre aux besoins variés des applications informatiques.


### la notion de consommation d'`API`

La consommation d'une API (Interface de Programmation Applicative) se réfère au fait d'utiliser les fonctionnalités fournies par cette API dans votre propre application ou système. Cela implique généralement d'envoyer des requêtes à l'API pour demander des données ou effectuer des actions, puis de traiter les réponses obtenues.

En termes simples, c'est comme si vous utilisiez un service ou un outil externe dans votre propre programme. Par exemple, si vous utilisez une API météo, vous pouvez consommer cette API en envoyant une requête pour obtenir les prévisions météorologiques, puis en utilisant ces données dans votre application pour afficher la météo à l'utilisateur.

La consommation d'API repose souvent sur des protocoles standard tels que HTTP, où vous envoyez des requêtes à une URL spécifique avec des paramètres, et l'API renvoie des données au format convenu, souvent en JSON.

En résumé, consommer une API signifie utiliser les fonctionnalités offertes par cette interface pour enrichir votre propre application avec des données ou des services provenant d'une source externe.

### les verbes HTTP

Les verbes HTTP sont des méthodes standardisées utilisées pour spécifier l'action que l'on souhaite effectuer sur une ressource identifiée. Voici une définition simple de chacun des verbes HTTP mentionnés :

`GET` Le verbe GET est utilisé pour récupérer des données depuis un serveur.
Il ne doit pas avoir d'effet secondaire et est considéré comme une opération "sans effet".

`POST` Le verbe POST est utilisé pour envoyer des données au serveur afin de créer une nouvelle ressource.
Il peut également être utilisé pour effectuer d'autres types d'actions côté serveur en fonction de la logique définie par l'API.

`PUT` Le verbe PUT est utilisé pour mettre à jour une ressource existante sur le serveur ou pour créer une ressource si elle n'existe pas.
Lorsqu'il est utilisé pour mettre à jour, il remplace entièrement la ressource existante par la nouvelle version fournie.

`PATCH` Le verbe PATCH est utilisé pour appliquer des modifications partielles à une ressource.
Contrairement à PUT, il n'est pas nécessaire de fournir une ressource entière. Vous pouvez envoyer uniquement les champs que vous souhaitez mettre à jour.

`DELETE` Le verbe DELETE est utilisé pour demander la suppression d'une ressource sur le serveur.
Après une requête DELETE, la ressource n'est normalement plus accessible.

En résumé, chaque verbe HTTP a une signification spécifique dans le contexte d'une requête HTTP, déterminant l'action à effectuer sur la ressource spécifiée. Ces verbes forment la base du protocole HTTP (Hypertext Transfer Protocol) utilisé pour la communication entre les clients et les serveurs sur le web.


## Les codes Status
Les codes de statut HTTP sont des indications fournies dans les réponses HTTP pour indiquer le résultat d'une requête. Les codes de statut sont regroupés en plusieurs catégories, comme les codes 2xx pour les succès, les codes 4xx pour les erreurs côté client, et les codes 5xx pour les erreurs côté serveur.

Le code de statut 418 est souvent utilisé comme une blague dans le contexte du protocole HTTP. Il est défini dans la spécification RFC 2324 (Hyper Text Coffee Pot Control Protocol) comme "I'm a teapot" (Je suis une théière). Cela a été fait de manière humoristique et n'a pas d'application pratique réelle.

Le code de statut 420 n'est pas défini dans les spécifications HTTP standard. Cependant, il est parfois utilisé pour indiquer une erreur liée à la consommation de substances illicites. Encore une fois, cela n'a pas de signification officielle dans le protocole HTTP et n'est pas recommandé pour une utilisation sérieuse.




##  Le Payload dans les requêtes HTTP


Le terme "payload" dans le contexte des requêtes HTTP se réfère aux données transportées dans le corps (body) d'une requête. Plus précisément, le payload contient les informations que le client envoie au serveur lorsqu'il effectue une requête HTTP. Le type et la structure du payload dépendent du type de requête HTTP et de l'application spécifique.

## Le modèle `MVC` (Model-Vue-Controller)

Le modèle MVC (Model-Vue-Controller) est un modèle architectural utilisé dans le développement logiciel pour organiser le code d'une application. Voici une définition simple de chaque composant du modèle MVC :

Modèle (Model) :

Le modèle représente la structure des données de l'application et la logique métier.
Il gère la manipulation et la gestion des données, ainsi que les règles métier associées.
En résumé, le modèle représente la "connaissance" de l'application.
Vue (View) :

La vue est responsable de l'affichage des données au sein de l'interface utilisateur.
Elle présente les données du modèle à l'utilisateur et peut également écouter les actions de l'utilisateur.
La vue ne manipule généralement pas directement les données, mais communique avec le contrôleur pour effectuer des actions.
Contrôleur (Controller) :

Le contrôleur agit comme un intermédiaire entre le modèle et la vue.
Il reçoit les actions de l'utilisateur depuis la vue, traite ces actions, met à jour le modèle en conséquence, puis informe la vue des changements.
En résumé, le contrôleur gère le flux de données entre le modèle et la vue.
L'idée principale derrière le modèle MVC est de séparer clairement les préoccupations liées aux données, à l'affichage et à la logique de contrôle. Cela rend l'application plus modulaire, plus facile à maintenir et à développer, car les modifications apportées à l'un des composants n'impactent pas nécessairement les autres.

## L'architecture `REST`

L'architecture REST (Representational State Transfer) est un style d'architecture utilisé dans le développement des services web. 

Dans l'architecture REST, tout est considéré comme une ressource, telle qu'une entité (comme un utilisateur, un article, etc.) ou un service.
Chaque ressource est identifiée de manière unique par une URI (Uniform Resource Identifier).


Les ressources peuvent avoir différentes représentations, souvent en utilisant des formats tels que JSON (JavaScript Object Notation) ou XML.
Par exemple, un utilisateur peut être représenté en JSON avec des attributs tels que le nom, l'âge, etc.


Les actions sur les ressources sont effectuées en utilisant les méthodes HTTP standard : GET pour récupérer des données, POST pour créer une nouvelle ressource, PUT pour mettre à jour une ressource, DELETE pour supprimer une ressource, etc.


Chaque requête du client au serveur doit contenir toutes les informations nécessaires pour comprendre et traiter la requête.
Le serveur ne garde pas d'état de session entre les requêtes, ce qui signifie que chaque requête est indépendante des précédentes.


L'interface entre le client et le serveur est uniforme et simplifiée. Elle suit des conventions bien définies, telles que l'utilisation d'URIs pour identifier les ressources et l'utilisation des méthodes HTTP standard.
L'architecture REST est souvent utilisée dans le développement d'API (Interfaces de Programmation Applicative) pour les services web, fournissant une manière simple et efficace d'accéder et de manipuler des ressources à travers le protocole HTTP. Elle est largement utilisée dans le développement web en raison de sa simplicité, de sa flexibilité et de sa scalabilité.

## "Statefull" et "Stateless"

Les termes "stateful" (avec état) et "stateless" (sans état) font référence à la manière dont un système traite l'information relative à l'état des interactions avec les clients. Voici les principales différences entre ces deux concepts :

Stateful (Avec État) :

Un système stateful garde la trace de l'état des interactions avec un client au fil du temps.
Les informations sur l'état du client sont stockées côté serveur, ce qui signifie que le serveur conserve la mémoire de l'état actuel du client entre les différentes requêtes.
Ceci permet au système de fournir une expérience plus contextuelle et personnalisée, car il se souvient de l'historique des actions du client.
Stateless (Sans État) :

Un système stateless ne conserve pas l'état du client entre les requêtes. Chaque requête du client est traitée de manière indépendante, sans connaissance de l'état précédent.
Toutes les informations nécessaires pour comprendre et traiter une requête doivent être incluses dans cette requête elle-même.
Les systèmes stateless sont souvent plus simples, plus évolutifs et plus faciles à gérer, car ils n'ont pas besoin de stocker et de gérer l'état du client.
Exemple concret :

Stateful : Un exemple courant d'application stateful est une session utilisateur dans une application web où l'utilisateur doit s'authentifier. Le serveur garde la trace de l'état de la session (connecté ou non) entre les différentes requêtes.

Stateless : Un exemple courant d'application stateless est le protocole HTTP lui-même. Chaque requête HTTP est traitée indépendamment, sans que le serveur ne conserve l'état du client entre les requêtes. Les cookies peuvent être utilisés pour introduire un semblant d'état dans les transactions HTTP, mais le protocole lui-même est fondamentalement stateless.

En résumé, la principale différence entre stateful et stateless réside dans la gestion de l'état du client. Stateless ne garde pas l'état entre les requêtes, tandis que stateful le fait en stockant les informations sur l'état côté serveur.

## `URL` et `URI`

En bref, la principale différence entre un URI et une URL est que le premier peut être un nom, un emplacement ou les deux, tandis que le second ne fournit que l’emplacement d’une ressource.

Dans cet article, nous expliquerons plus en détail les différences entre un URI et une URL et leur structure.

Qu’est-ce qu’un URI
L’URI est une chaîne de caractères qui identifie une ressource sur Internet en utilisant l’emplacement, le nom ou les deux. Il permet une identification uniforme des ressources. Un URI est en outre regroupé comme un localisateur, un nom ou les deux, ce qui signifie qu’il peut décrire une URL, un URN ou les deux. Le terme identificateur dans l’URI fait référence à la distinction des ressources, malgré la technique utilisée pour effectuer l’opération que ce soit l’emplacement, le nom ou le contexte.


L’URL contient des informations sur la manière d’extraire une ressource de son emplacement. Par exemple:

http://exemple.com/mapage.html

## "Chemin relatif" et "Chemin absolu"

Les termes "chemin relatif" et "chemin absolu" sont utilisés pour spécifier l'emplacement d'un fichier ou d'un répertoire par rapport à un point de référence, généralement le répertoire actuel. Voici les différences entre les deux concepts :

Chemin Relatif :

Un chemin relatif indique le chemin vers un fichier ou un répertoire par rapport au répertoire actuel ou à un autre point de référence.
Il n'inclut pas nécessairement l'ensemble du chemin depuis la racine du système de fichiers, mais plutôt la relation entre le répertoire courant et la cible.
Un exemple de chemin relatif pourrait être "./images/photo.jpg", où "." représente le répertoire actuel.
Chemin Absolu :

Un chemin absolu spécifie le chemin complet vers un fichier ou un répertoire depuis la racine du système de fichiers.
Il fournit l'emplacement complet, indépendamment du répertoire actuel. Par exemple, "/home/utilisateur/images/photo.jpg" est un chemin absolu sous un système de fichiers UNIX.

##  La route dans une `API`

Une Route est une règle définissant comment les messages sont déplacés d'un service (ou endpoint) à un autre. C'est un processus graphique, contenant deux composants ou plus reliés ensemble, qui vous permet de configurer et de tester facilement vos règles de routage et de médiation.


Dans l'API web, chaque itinéraire a un nom. Les noms de routes sont utiles pour générer des liens, de sorte que vous pouvez inclure un lien dans une réponse HTTP

## `ORM` et `ODM` 

ORM (Object-Relational Mapping) : Utilisé avec des bases de données relationnelles, il mappe les objets du code sur des tables de base de données relationnelles.

ODM (Object-Document Mapping) : Utilisé avec des bases de données NoSQL de type document, il mappe les objets du code sur des documents stockés dans la base de données.

Un ORM cartes entre un Modèle d'Objet et une Base de données Relationnelle. Une ODM cartes entre un Modèle d'Objet et un Document de la Base de données. MySQL n'est pas un ORM, c'est une Base de données Relationnelle, plus précisément, une Base de données SQL. MongoDB est pas un ODM, c'est un Document de la Base de données.


## le Middleware


Le middleware est un logiciel qui agit comme un intermédiaire entre différentes applications, systèmes ou composants logiciels pour faciliter la communication et la gestion des données. Il se situe entre l'application cliente et le serveur, ou entre différents composants logiciels, et joue le rôle de support pour faciliter diverses tâches. 

Le middleware facilite la communication entre des composants logiciels ou des systèmes qui peuvent utiliser différents protocoles ou formats de données. Il agit comme une couche d'abstraction pour rendre la communication plus transparente.

Il facilite l'intégration de systèmes hétérogènes en fournissant des mécanismes standardisés pour la gestion des données, la synchronisation et la coordination entre les différentes parties.

Certains middleware offrent des services communs, tels que la gestion des transactions, la sécurité, la gestion des erreurs, etc., pour simplifier le développement d'applications et garantir la cohérence et la fiabilité des opérations.

Le middleware peut faciliter la répartition des charges de travail sur plusieurs serveurs, contribuant ainsi à améliorer la performance et l'évolutivité des systèmes.

Il permet l'adaptabilité en facilitant l'évolution des systèmes sans perturber les composants existants. Cela permet de mettre à jour ou de remplacer des parties du système sans impacter l'ensemble.

Des exemples de middleware incluent les serveurs d'applications, les brokers de messages, les middleware de base de données distribuée, les frameworks de middleware orienté message, etc.

En résumé, le middleware est un composant logiciel qui facilite l'interaction et la communication entre différents éléments d'un système, simplifiant ainsi le développement, l'intégration et la maintenance des applications.