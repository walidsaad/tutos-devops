|
 | GESTIONNAIRE DE PROJETS JAVA MAVEN |
| --- | --- |

![](RackMultipart20200624-4-ty3y20_html_abb65eda0db58048.png)

1.
# Introduction

Apache Maven est un outil permettant d&#39;automatiser la gestion d&#39;un projet Java. Il offre entre autres les fonctionnalités suivantes :

- Compilation et déploiement des applications Java (JAR, WAR)
- Gestion des librairies requises par l&#39;application en utilisant des dépôts (_repository_) local ou distant
- Exécution des tests unitaires
- Génération des documentations du projet (site web, pdf, Latex)
- Intégration dans différents IDE (Eclipse, NetBeans, etc.)

Ce tutoriel va vous apprendre à utiliser Maven dans tout projet de développement utilisant Java. Après avoir terminé ce tutoriel, vous vous retrouvez avec un niveau d&#39;expertise modéré dans l&#39;utilisation d&#39;Apache Maven.

Pour résumer, Maven simplifie et standardise le processus de construction d&#39;un projet Java. Il gère la compilation, la distribution, la documentation, la collaboration en équipe et d&#39;autres tâches de façon transparente. Maven augmente la réutilisabilité et prend en charge la plupart des tâches liées à la construction.

1.
# Prérequis

- Java : JDK 1.7 ou plus récent.
- RAM : Pas de minimum requis
- Espace disque :
  - Environ 10 Mo sont nécessaires pour l&#39;installation de Maven.
  - Un espace disque supplémentaire sera utilisé pour le dépôt local de Maven dont La taille varie en fonction de l&#39;utilisation, mais il faut prévoir au moins 500 Mo.
- Système d&#39;exploitation : Aucun prérequis.
  - Disponible sous Windows, Linux, MAC, etc…

1.
# Installation d&#39;Apache Maven

## Etape 1: Vérifier l&#39;installation de Java sur votre machine

![](RackMultipart20200624-4-ty3y20_html_b7e750f710bcb339.png)

## Si Java n&#39;est pas installé, téléchargez et installez le Kit de Développement Java (SDK) depuis le site officiel :

## [https://www.oracle.com/technetwork/java/javase/downloads/index.html.](https://www.oracle.com/technetwork/java/javase/downloads/index.html.)

## Etape 2: Définir l&#39;environnement JAVA

## Définissez la variable d&#39;environnement JAVA\_HOME pour qu&#39;elle pointe vers l&#39;emplacement du répertoire de base où Java est installée sur votre machine. Par exemple :

![](RackMultipart20200624-4-ty3y20_html_6014a68cfe80115b.png)

## Etape 3: Télécharger l&#39;Archive Maven

- Télécharger Maven depuis son site web officiel [https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi)
- Pour Windows : [http://www-us.apache.org/dist/maven/maven-3/3.5.3/binaries/apache-maven-3.5.3-bin.zip](http://www-us.apache.org/dist/maven/maven-3/3.5.3/binaries/apache-maven-3.5.3-bin.zip)

![](RackMultipart20200624-4-ty3y20_html_f20410ba453138c8.png)

## Etape 4: Extraire l&#39;archive de Maven

Extraire l&#39;archive dans le répertoire dans lequel vous souhaitez installer Maven 3.5.3. Le sous-répertoire apache-maven-3.5.3 sera créé à partir de l&#39;archive. Par exemple : C:\Program Files (x86)\apache-maven-3.5.3

## Etape 5: Définir les variables d&#39;environnement Maven

- Ajoutez M2\_HOME, M2, MAVEN\_OPTS aux variables d&#39;environnement.

  - SET M2\_HOME C:\Program Files (x86)\apache-maven-3.5.3
  - SET M2 %M2\_HOME%\bin
  - SET MAVEN\_OPTS -Xms256m -Xmx512m

## Etape 6: Ajouter l&#39;emplacement du répertoire bin du Maven au chemin du système

- Ajoutez la variable M2 au chemin du système (à la variable PATH).

## Etape 7: Vérifier l&#39;installation

![](RackMultipart20200624-4-ty3y20_html_7ada3b2ef43a50a3.png)

  - Attendre la fin du démarrage du serveur qui sera signalée par l&#39;affichage de la ligne suivante:

1.
# Mon premier projet Maven

On veut créer notre premier projet Maven. Pour cela, nous allons utiliser le mécanisme d&#39;Archetype de Maven. Un Archetype est défini comme un modèle à partir duquel notre projet sera créé. Dans Maven, un Archetype pourrait être combiné avec une entrée de l&#39;utilisateur pour produire un projet adapté aux besoins de l&#39;utilisateur.

Pour créer un nouveau projet Maven, exécutez ce qui suit à partir de la ligne de commande:

$ mvn -B archetype:generate \

-DarchetypeGroupId=org.apache.maven.archetypes \

-DgroupId=com.mycompany.app \

- ![](RackMultipart20200624-4-ty3y20_html_6ba34f65938b4f94.png) DartifactId=training-app

U ![](RackMultipart20200624-4-ty3y20_html_8d2228cb96a5368c.png) ne fois que vous avez exécuté cette commande, vous remarquerez que certaines choses se sont produites. Tout d&#39;abord, vous remarquerez qu&#39;un répertoire nommé training-app a été créé pour le nouveau projet, et ce répertoire contient un fichier nommé pom.xml. La structure du projet devrait ressembler à ceci:

![](RackMultipart20200624-4-ty3y20_html_1f28827cbfb7947c.png)

Comme vous pouvez le voir, le projet créé à partir de l&#39; d&#39;Archetype a un dossier _main_ pour les sources de votre application et un dossier _test_ pour vos sources de test. C&#39;est la disposition standard pour les projets Maven (les sources d&#39;application résident dans _${basedir}/src /main/java_ et les sources de test résident dans _${basedir}/src/test/java_, où ${basedir} représente le répertoire contenant le fichier pom .xml).

Aussi, le projet créé possède un POM. Le fichier _ **pom.xml** _ contient le modèle d&#39;objet de projet (POM Project Object Model) pour ce projet. Maven est centré autour de la notion de projet, et le POM présente l&#39;unité de travail de base. En bref, le POM contient toutes les informations importantes sur votre projet.

Le fichier _ **pom.xml** _ s&#39;agit d&#39;un POM très simple, et qui affiche toujours les éléments clés de chaque POM. Parcourons chacun d&#39;entre eux pour vous familiariser avec les éléments essentiels de POM:

| **Eléments POM** | **Description** |
| --- | --- |
| **project**
 | C&#39;est l&#39;élément de premier niveau dans tous les fichiers pom.xml Maven. |
| **modelVersion** | Cet élément indique quelle version du modèle d&#39;objet utilise ce POM. La version du modèle elle-même change très rarement (4.0.0 est la version actuelle) |
| **groupId** | Cet élément indique l&#39;identifiant unique de l&#39;organisation ou du groupe qui a créé le projet. Le groupId est l&#39;un des identifiants de clé d&#39;un projet et est généralement basé sur le nom de domaine complet de votre organisation. Par exemple org.apache.maven.plugins est le groupId désigné pour tous les plugins Maven. |
| **artefactId** | Cet élément indique le nom de base unique de l&#39;artefact primaire généré par ce projet. L&#39;artefact principal d&#39;un projet est généralement un fichier JAR. Les artefacts secondaires tels que les bundles sources utilisent également l&#39;artifactId comme partie de leur nom final. Un artefact typique produit par Maven aurait la forme \&lt;artifactId\&gt; - \&lt;version\&gt;. \&lt;Extension\&gt; (par exemple, trainingapp-1.0.jar).

 |
| **packaging** | Cet élément indique le type de package à utiliser par cet artefact (par exemple, JAR, WAR, EAR, etc.). Cela ne signifie pas seulement que l&#39;artefact produit est JAR, WAR ou EAR mais peut également indiquer un cycle de vie spécifique à utiliser dans le cadre du processus de construction. La valeur par défaut de l&#39;élément de packaging est JAR. Vous n&#39;avez donc pas besoin de spécifier cela pour la plupart des projets.
 |
| **version** | Cet élément indique la version de l&#39;artefact généré par le projet. La gestion des versions dans Maven est basée sur le concept de SNAPSHOT. Dans une version, un SNAPSHOT indique qu&#39;un projet est en cours de développement. |
| **name** | Cet élément indique le nom d&#39;affichage utilisé pour le projet. Ceci est souvent utilisé dans la documentation générée par Maven. |
| **url** | Cet élément indique où le site du projet peut être trouvé. Ceci est souvent utilisé dans la documentation générée par Maven.
 |
| **description** | Cet élément fournit une description de base de votre projet. Ceci est souvent utilisé dans la documentation générée par Maven. |

1.
# Cycle de vie Maven (Build Life Cycle)

  1. **Cycle de vie (Définition)**

Maven est basé sur le concept de base d&#39;un cycle de vie de construction de projets. Cela signifie que le processus de construction, de distribution et de déploiement d&#39;un projet (artefact particulier) est clairement défini.

La construction d&#39;un projet est définit par un ensemble de commandes, et le POM s&#39;assurera d&#39;obtenir les résultats souhaités.

Il existe **trois cycles de vie** de construction intégrés: _default_, _clean_ et _site_.

  - Le cycle de vie _default_ (_Build_) gère le déploiement de votre projet
  - le cycle de vie _clean_ gère le nettoyage du projet
  - le cycle de vie du _site_ gère la création de la documentation du site de votre projet.

  1. **Les Phases**

Un cycle de vie de construction (Build Life Cycle) est **une séquence de phases** (appelées aussi stages) qui définit l&#39;ordre dans lequel les **objectifs** (_goals_) qui doivent être exécutés. Ici, la phase représente une étape du cycle de vie. À titre d&#39;exemple, un cycle de vie Maven Build typique (càd _default_) comprend la séquence de phases suivante :

- **Validate :**  Valide que le projet est correctement défini
- **Compile :**  Compile les sources
- **Test :**  Lance les tests unitaires
- **Package :**  Prépare la distribution du projet. (archives Jar, War, Ear...)
- **integration-test :**  Lance les tests d&#39;intégration
- **verify :**  Lance des tests de validation du package créé.
- **Install :**  Installe le package **en local** sur la machine pour pouvoir être réutilisé comme dépendance.
- **Deploy :**  Déploie le package **sur un serveur** pour qu&#39;il puisse être **réutilisé** par tout le monde.

  1. **Les Objectifs (Goals)**

On fournit à Maven 2 une liste de goals à exécuter. Un goal est **une tâche** précise que Maven est en mesure de réaliser à partir des informations qu&#39;il pourra trouver dans le fichier pom.xml.

- Tous les goals se trouvent dans **des plugins** Maven.
- Pour exécuter un goal, Maven va donc commencer par résoudre le nom du goal pour en déduire le plugin dans lequel il se trouve et le télécharger.
- Commande : mvn \&lt;nom du plugin\&gt;:\&lt;nom du goal\&gt; ou biendirectement mvn \&lt;nom du gaol\&gt;

  1. **Les plug-ins Maven**

Maven est en fait un framework d&#39;exécution de plugin où chaque tâche est en fait effectuée par des plugins. Les Plugins Maven sont généralement utilisés pour :

- **Jar**  : créer un fichier jar depuis le projet
- **War**  : créer un fichier war depuis le projet
- **Compiler**  : compiler les fichiers JAVA
- **surefire**  : lancer des tests unitaires avec JUnit et créer les rapports de test
- **javadoc**  : créer la documentation du projet
- **antrun**  : Exécute un ensemble de tâches ant à partir de n&#39;importe quelle phase mentionnée dans la construction (cad dans le fichier pom.xml).

1.
# Manipulations Maven

  1. **Construction ET Test (Build &amp; Test)**

Ce que nous avons appris dans la section précédente est comment créer une application Java avec Maven et la notion du cycle de vie. Nous verrons maintenant comment lancer les différentes phases d&#39;un cycle de vie afin de tester notre application créée dans la section 4.

    1. **Compilation (Build)**

L ![](RackMultipart20200624-4-ty3y20_html_36784a0b45563e9f.png) ancer la commande **mvn** avec l&#39;objectif _ **compile** _.

- Les classes compilées ont été placées dans ${basedir}/target/classes, ce qui est une autre convention standard de Maven.
- On remarque que Maven a exécuté dans l&#39;ordre la phase de validation (récupération des ressources et téléchargement des plugins nécessaires) et de compilation sans passer automatiquement aux phases suivantes (_test_, _package_, _install_, _deploy_, etc.) du cycle de vie.

On veut maintenant tester le fichier JAVA compilé :

![](RackMultipart20200624-4-ty3y20_html_e884e8b6be83eded.png)

    1. **Tests Unitaires (Unit Test)**

Dans le fichier pom.xml, Maven a déjà ajouté le plugin _Junit_ comme outil de test unitaire. Dans notre projet, Maven ajoute par défaut un fichier source _App.java_ et un fichier de test _AppTest.java_, comme indiqué dans la section 4.

On vous demande maintenant de la lancer la commande _ **mvn test** _ pour lancer les tests unitaires.

![](RackMultipart20200624-4-ty3y20_html_4f67666cc3a8b8fa.png)

A partir des traces d&#39;exécution, quelles étapes ont été exécutées par Maven ?

- Maven télécharge plus de dépendances cette fois-ci. Ce sont les dépendances et les plugins nécessaires à l&#39;exécution des tests (il a déjà les dépendances dont il a besoin pour la compilation et ne les téléchargera plus).
- Avant de compiler et d&#39;exécuter les tests, Maven compile le code principal (pas de changement ici).
- Le rapport de Test reports est disponible dans le dossier ${basedir}/target/surefire-reports
- Les fichiers de test compilés se trouve dans le dossier ${basedir}/target/test-classes
- Pour compiler uniquement les fichiers test unitaire et sans les exécuter, on lance _ **mvn test-compile** _

    1. **Génération du fichier JAR**

Dans le fichier POM pom.xml, le packaging par défaut est configuré à jar. C&#39;est ainsi que Maven sait produire un fichier JAR à partir de la commande _ **mvn package** _.

O ![](RackMultipart20200624-4-ty3y20_html_597f67eb5a4bd02b.png) n vous demande maintenant de la lancer la commande _ **mvn package** _ pour créer une archive jar du notre projet.

- Le fichier jar est généré dans le répertoire _${basedir}/target_
- On peut mettre le fichier jar dans un repository local (dans _${user.home}/.m2/repository_) ou bien dans un serveur distant.

Essayer d&#39;exécuter le fichier jar avec la commande suivante :

_**j ![](RackMultipart20200624-4-ty3y20_html_8a1c13272a9fd9.png) ava -jar target\training-app-1.0-SNAPSHOT.jar**_

On remarque ici que notre fichier jar n&#39;est pas exécutable. En effet, le fait de préciser \&lt;packaging\&gt;jar\&lt;/packaging\&gt; n&#39;indique pas que Maven va créer un jar exécutable avec toute ses dépendances. Ce jar ne contiendra que les classes compilées de notre projet et ne sera pas exécutable. Pour créer un fichier exécutable, on doit ajouter le plugin _ **maven-jar-plugin** _ à notre projet.

Ajouter la section suivante dans votre fichier POM :

\&lt;build\&gt;

\&lt;plugins\&gt;

\&lt;plugin\&gt;

\&lt;!-- Build an executable JAR --\&gt;

\&lt;groupId\&gt;org.apache.maven.plugins\&lt;/groupId\&gt;

\&lt;artifactId\&gt;maven-jar-plugin\&lt;/artifactId\&gt;

\&lt;version\&gt;3.0.2\&lt;/version\&gt;

\&lt;configuration\&gt;

\&lt;archive\&gt;

\&lt;manifest\&gt;

\&lt;addClasspath\&gt;true\&lt;/addClasspath\&gt;

\&lt;classpathPrefix\&gt;lib/\&lt;/classpathPrefix\&gt;

\&lt;mainClass\&gt;com.mycompany.app.App\&lt;/mainClass\&gt;

\&lt;/manifest\&gt;

\&lt;/archive\&gt;

\&lt;/configuration\&gt;

\&lt;/plugin\&gt;

\&lt;/plugins\&gt;

\&lt;/build\&gt;

On indique donc ici la classe main (\&lt;mainClass\&gt;), que notre jar sera créé lors de la phase « packaging » de Maven

E ![](RackMultipart20200624-4-ty3y20_html_fff0e227d15948ab.png) xécuter de nouveau la commande _ **mvn package** _ et lancer le fichier jar.

    1. **La commande Clean**

On veut maintenant supprimer la compilation actuelle. Exécuter la commande _ **mvn clean** _

![](RackMultipart20200624-4-ty3y20_html_3de6555d8f3544a6.png)

-

    1. **La commande Install**

Dans un environnement de développement, on utilise la commande _ **mvn install** _pour générer et installer les artefacts **dans le référentiel (repository) local**.

- Cette commande exécute chaque phase du cycle de vie par défaut dans l&#39;ordre (validation, compilation, package, etc.) avant d&#39;exécuter l&#39;installation.
- On aura besoin uniquement d&#39;appeler la dernière phase de construction à exécuter, dans ce cas, lancez:

![](RackMultipart20200624-4-ty3y20_html_6c28104ecfad9666.png)

Vérifier que le jar est bien installé dans votre local repository (_${user.home}/.m2/repository_).

    1. **La commande Deploy**

Dans un environnement de build (ou bien production), on utilise la commande _ **mvn deploy** _ pour créer et déployer proprement les artefacts du notre projet dans un référentiel partagé (shared repository). Ceci représente les cas usuel dans les entreprises.

Pour exécuter un la commande _ **mvn deploy** _ il faut configurer un serveur repository (voir plus tard).

    1. **Générer la documentation du projet**

La génération de site du projet est l&#39;une des fonctionnalités les plus prisées de Maven. Le POM a assez d&#39;informations pour générer un site web pour votre projet. On peut aussi personnaliser notre site Maven, sinon on peut se limiter à la version générée par défaut en utilisant la commande _ **mvn site** _.

![](RackMultipart20200624-4-ty3y20_html_5ee96bef2b929970.png)

    1. **Modification des fichiers sources**
  1.
# Gestion de dépendances du projet

Pour en revenir aux principes de Maven :

- Le répertoire _src_ ne doit contenir que des fichiers sources apportés au projet
- Les librairies externes (appelées dépendances) utilisées par le projet ne doivent être que des liens vers d&#39;autres artifacts Maven et surtout pas copiées dans le répertoire _src_ du projet.
- Un grand nombre d&#39;artifacts jars est disponible sur les entrepôts officiels de Maven : [http://www.mvnrepository.com/](http://www.mvnrepository.com/)

Maven propose de définir toutes les dépendances par configuration dans le fichier _pom.xml_. C&#39;est ensuite le plugin Maven de gestion de dépendances qui ira télécharger sur les repositories distants les fichiers jar indiqués comme dépendances, s&#39;ils ne se trouvent pas dans le repository local.

On veut maintenant modifier notre projet afin de gérer une liste des sessions de formations. Les informations qu&#39;on voudrait afficher sont stockées dans une base de données MYSQL (dans la table session). Pour cela, faites les modifications suivantes :

- Modifier la classe App.java (le remplacer par le contenu du fichier Training\_Data\_Service.java)
- Installer un serveur XAMP, accéder au portail PhpMyAdmin ([_http://localhost/phpmyadmin_](http://localhost/phpmyadmin)) et créer une nouvelle base données training
- Importer dans PhpMyAdmin le fichier training.sql qui permet de créer la table Session (contient deux enregistrements par défaut).
- Ajouter la dépendance _mysql-connector-java_ dans le fichier pom.xml

\&lt;dependency\&gt;

\&lt;groupId\&gt;mysql\&lt;/groupId\&gt;

\&lt;artifactId\&gt;mysql-connector-java\&lt;/artifactId\&gt;

\&lt;version\&gt;5.1.35\&lt;/version\&gt;

\&lt;/dependency\&gt;

- Compiler votre projet et tester le fichier jar _mvn clean install &amp;&amp; java -jar target\training-app-1.0-SNAPSHOT.jar_
- Faire les modifications nécessaires dans votre fichier POM afin de rendre le plugin _mysql-connector-java_ disponible à l&#39;exécution du fichier jar.

**Première méthode**  : copier la dépendance dans le dossier lib au moment de compilation du votre projet (dans la phase package cad lors de la génération du jar).

\&lt;plugin\&gt;

\&lt;groupId\&gt;org.apache.maven.plugins\&lt;/groupId\&gt;

**\&lt;artifactId\&gt;maven-dependency-plugin\&lt;/artifactId\&gt;**

\&lt;executions\&gt;

\&lt;execution\&gt;

\&lt;id\&gt;copy\&lt;/id\&gt;

**\&lt;phase\&gt;package\&lt;/phase\&gt;**

\&lt;goals\&gt;

**\&lt;goal\&gt;copy-dependencies\&lt;/goal\&gt;**

\&lt;/goals\&gt;

\&lt;configuration\&gt;

**\&lt;outputDirectory\&gt;**

**${project.build.directory}/lib**

**\&lt;/outputDirectory\&gt;**

\&lt;/configuration\&gt;

\&lt;/execution\&gt;

\&lt;/executions\&gt;

\&lt;/plugin\&gt;

![](RackMultipart20200624-4-ty3y20_html_a96053b49695a276.png)\&lt;plugin\&gt;

**Deuxième méthode**  : Assembler le fichier jar de la dépendance avec le fichier jar final de l&#39;application en utilsant le plugin _ **maven-assembly-plugin** _

\&lt;plugin\&gt;

**\&lt;artifactId\&gt;maven-assembly-plugin\&lt;/artifactId\&gt;**

\&lt;configuration\&gt;

\&lt;archive\&gt;

\&lt;manifest\&gt;

\&lt;mainClass\&gt;com.mycompany.app.App\&lt;/mainClass\&gt;

\&lt;/manifest\&gt;

\&lt;/archive\&gt;

\&lt;descriptorRefs\&gt;

\&lt;descriptorRef\&gt;jar-with-dependencies\&lt;/descriptorRef\&gt;

\&lt;/descriptorRefs\&gt;

\&lt;/configuration\&gt;

\&lt;executions\&gt;

\&lt;execution\&gt;

\&lt;id\&gt;make-assembly\&lt;/id\&gt; \&lt;!-- this is used for inheritance merges --\&gt;

\&lt;phase\&gt;package\&lt;/phase\&gt; \&lt;!-- bind to the packaging phase --\&gt;

\&lt;goals\&gt;

\&lt;goal\&gt;single\&lt;/goal\&gt;

\&lt;/goals\&gt;

\&lt;/execution\&gt;

\&lt;/executions\&gt;

\&lt;/plugin\&gt;

![](RackMultipart20200624-4-ty3y20_html_18e443f4335ffd4e.png)

#

1.
# Maven Eclipse IDE

![](RackMultipart20200624-4-ty3y20_html_52f7179f84edd4ed.png)

![](RackMultipart20200624-4-ty3y20_html_cd72a84c2810bc93.png)

![](RackMultipart20200624-4-ty3y20_html_abafcd7f5ecba4fe.png)

![](RackMultipart20200624-4-ty3y20_html_3d037e69e06d2229.png)

# ![](RackMultipart20200624-4-ty3y20_html_8e03a3923a815b03.png)

#

1.
# Application Web

Pour créer une application web java simple, nous allons utiliser le plugin _ **maven-archetype-webapp** _.

$ mvn -B archetype:generate \

-DarchetypeArtifactId=maven-archetype-webapp \

-DgroupId=com.mycompany.app \

-DartifactId=training-webapp

![](RackMultipart20200624-4-ty3y20_html_f2c63f89f1bc83db.png)

Compiler et déployer (_mvn install_) votre application en copiant le fichier _war_ dans le dossier _webapps_ du votre serveur web (le serveur Tomcat par exemple), démarrer le serveur Tomcat et lancer votre application.

![](RackMultipart20200624-4-ty3y20_html_3d7446ef2f2ee9d3.png)

![](RackMultipart20200624-4-ty3y20_html_c89365f43f025208.png)

![](RackMultipart20200624-4-ty3y20_html_8a5f55721eacbc2f.png)

1.
# Multi-Projects avec Maven

L&#39;une des principales caractéristiques de Maven est la gestion des dépendances. Gérer les dépendances est une tâche difficile une fois que nous avons affaire à des projets multi-modules (composés de centaines de modules / sous-projets). Maven fournit un haut degré de contrôle pour gérer de tels scénarios.

Maven utilise deux techniques clés pour gérer des projets multi-module: **la composition (le parent déclare ses modules) et l&#39;héritage (l&#39;enfant déclare son parent)**

On vous demande dans cette section de créer un nouveau projet Maven composé de 3 modules (voir les figures ci-dessous). Pour cele, on procede comme suit :

- Créer le projet parent
- Dans le projet parent, créer les 3 modules (frontend, Backend et Database-Service)
- Vérifier le fichier POM Parent et le fichier POM du chaque modules (comprenez les caractéristiques d&#39;héritage et de composition)

![](RackMultipart20200624-4-ty3y20_html_daf42e86a9daaa45.png)

![](RackMultipart20200624-4-ty3y20_html_cde8271b9afe0680.png)

##

- Créer les dépendances suivantes : es modules Frontend et Backend dépendent du module DataBase-Service (dans le fichier POM ajouter une nouvelle depandance database-service)

## \&lt;dependency\&gt;

## \&lt;groupId\&gt;com.mycompany.app\&lt;/groupId\&gt;

## \&lt;artifactId\&gt;database-service\&lt;/artifactId\&gt;

## \&lt;version\&gt;1.0-SNAPSHOT\&lt;/version\&gt;

## \&lt;/dependency\&gt;

##

- Compiler votre projet (lancer la commande _ **mvn package** _)

##

##

| 0 |
Cahier d&#39;exercices |
| --- | --- |
