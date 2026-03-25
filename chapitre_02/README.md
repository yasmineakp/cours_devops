**PIGIER Côte d'Ivoire**

Projet Informatique II -- LPRGL3

# AIDE-MÉMOIRE -- CHAPITRE 2

**Présentation de l'Écosystème Java**

# 1. GLOSSAIRE DES TERMES CLÉS

| **TERME**                   | **DÉFINITION**                                                                                                                                                              |
|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Bibliothèque (Library)**  | Collection de fonctions et de classes pré-écrites, regroupées pour faciliter leur utilisation. Fournie sous forme de fichier .jar.                                          |
| **Bytecode**                | Code intermédiaire entre le code source et le code machine, exécuté par la JVM. Même format quel que soit le matériel. Produit par javac à partir du code source. .class est l'extension des fichiers bytecode fournis à la JVM. |
| **Classe**                  | Modèle pour créer des objets, contenant des données (attributs) et des fonctions (méthodes).                                                                                |
| **Code machine**            | Langage binaire directement exécutable par le processeur.                                                                                                                   |
| **Code source**             | Texte écrit par un programmeur dans un langage de programmation (fichier .java).                                                                                            |
| **Compilateur**             | Programme qui effectue la compilation (javac en Java).                                                                                                                      |
| **Compilation**             | Processus de transformation du code source en code machine ou en bytecode.                                                                                                  |
| **Déboguer**                | Identifier et corriger les erreurs dans un programme.                                                                                                                       |
| **Dépendances**             | Liens entre modules d'un programme : un module a besoin d'un autre pour fonctionner. Bibliothèques externes requises par un projet.                                         |
| **Déployer / Déploiement**  | Installer et configurer une application sur un serveur ou un appareil.                                                                                                      |
| **Framework**               | Architecture logicielle préconçue qui fournit une structure, des outils, des modèles de conception et des conventions (ex. Spring).                                         |
| **IDE (EDI)**               | Integrated Development Environment --- environnement de développement intégré (éditeur + débogueur + compilateur).                                                          |
| **JDK**                     | Java Development Kit --- kit complet pour développer en Java (compilateur, interpréteur, bibliothèques, outils). Contient le JRE.                                           |
| **JIT**                     | Just-In-Time compilation --- technologie qui compile le bytecode en code machine natif AU MOMENT de l'exécution pour améliorer les performances.                            |
| **JRE**                     | Java Runtime Environment --- sous-ensemble du JDK pour EXÉCUTER (pas développer) des applications Java (JVM + bibliothèques).                                              |
| **JVM**                     | Java Virtual Machine --- programme qui fournit l'environnement d'exécution des programmes Java. Lit les fichiers .class.                                                    |
| **Maven**                   | Outil de construction utilisant des fichiers XML pour déclarer les dépendances.                                                                                             |
| **Oracle Corporation**      | Propriétaire actuel de Java après rachat de Sun Microsystems.                                                                                                               |
| **WORA**                    | Write Once, Run Anywhere --- les fichiers .class s'exécutent sans modification sur toute plateforme disposant d'une JVM.                                                    |

# 2. LE LANGAGE JAVA ET LA JVM

## 2.1 Historique et propriétaire

- Créé par **Sun Microsystems**, racheté par **Oracle Corporation** (propriétaire actuel)
- Existe depuis la fin des années **1990**, premières révisions depuis **1996**
- Implémentation de référence depuis Java 11 : **OpenJDK** (open source)
- Versions récentes : Java 21 (sept. 2023) → Java **25 LTS** (sept. 2025)

## 2.2 Caractéristiques du langage

- Langage **orienté objet**, strictement **basé sur les classes**
- Syntaxe inspirée de **C et C++** --- familière aux programmeurs de ces langages
- Vise une base **stable** pour développer des applications critiques d'entreprise
- Pas de refonte complète depuis sa création --- révisions progressives

## 2.3 Éditions de Java

| **ÉDITION**                        | **USAGE**                                         |
|------------------------------------|---------------------------------------------------|
| **Java ME (Micro Edition)**        | Appareils mobiles et embarqués                    |
| **Java SE (Standard Edition)**     | Applications de bureau, environnements standards  |
| **Java EE (Enterprise Edition)**   | Applications d'entreprise                         |

## 2.4 La JVM (Java Virtual Machine)

- Programme qui fournit l'**environnement d'exécution** (runtime) nécessaire à l'exécution des programmes Java
- Les programmes Java **ne peuvent pas fonctionner sans une JVM** adaptée au matériel et au système d'exploitation
- Portée sur un grand nombre d'environnements : Linux, macOS, Windows, mainframes...
- La JVM **démarre un interpréteur** qui traite les instructions bytecode une par une
- La JVM peut **surveiller et optimiser** un programme en cours d'exécution (collecte d'informations à l'exécution)

## 2.5 Objectifs de conception de la JVM

> **4 objectifs fondamentaux de la JVM :**
>
> - Fournir un conteneur pour l'exécution du code de l'application
> - Fournir un environnement d'exécution sécurisé et fiable (vs C/C++)
> - Soulager les développeurs de la gestion de la mémoire (garbage collector)
> - WORA : Write Once, Run Anywhere --- exécution multiplateforme sans modification

## 2.6 Cycle de vie d'un programme Java

| **ÉTAPE**                          | **DÉTAIL**                                                                            |
|------------------------------------|---------------------------------------------------------------------------------------|
| **1. Code source (.java)**         | Écrit par le programmeur dans le langage Java                                         |
| **2. Compilation (javac)**         | javac convertit le .java en bytecode → fichier .class                                 |
| **3. Chargement (classloading)**   | La JVM charge le fichier .class                                                       |
| **4. Interprétation + JIT**        | La JVM interprète le bytecode ; le compilateur JIT compile les parties fréquentes en code machine natif |

> **⚠️ Points critiques à retenir :**
>
> - javac produit du BYTECODE (pas du code machine) → fichiers .class
> - La JVM exécute le bytecode --- elle n'exécute PAS le code source directement
> - C'est le compilateur JIT qui produit réellement le code machine
> - Le format du bytecode est TOUJOURS le même quel que soit la machine sur laquelle il a été créé
> - Java est à la fois compilé (javac) ET interprété (JVM) → ni purement l'un ni l'autre
> - La JVM peut exécuter d'autres langages : Kotlin, Scala, Groovy, JRuby...

# 3. JDK ET JRE

## 3.1 Composants du JDK

| **COMPOSANT**                      | **RÔLE**                                                      |
|------------------------------------|---------------------------------------------------------------|
| **Compilateur Java (javac)**       | Convertit le code source .java en bytecode .class             |
| **Interpréteur Java (java)**       | Exécute le bytecode .class via la JVM                         |
| **Bibliothèques Java (API)**       | Fonctionnalités prêtes à l'emploi (E/S, chaînes, réseau...)   |
| **Outils de développement**        | Éditeur de code, débogueur, générateur de documentation       |
| **JRE (inclus)**                   | JVM + bibliothèques --- sous-ensemble du JDK                  |

## 3.2 JDK vs JRE --- Différence clé

> **JDK vs JRE --- à retenir :**
>
> - JDK = développer + exécuter (contient le JRE en son sein)
> - JRE = exécuter seulement (JVM + bibliothèques, sans le compilateur)
> - Le JRE est un SOUS-ENSEMBLE du JDK
> - Téléchargement : site web Oracle ou OpenJDK (disponible pour Linux, macOS, Windows)

# 4. BIBLIOTHÈQUES ET FRAMEWORKS

## 4.1 Bibliothèques Java

- Collections de **classes et de fonctions** offrant des fonctionnalités prêtes à l'emploi
- Fournies sous forme de **fichiers .jar** (Java Archive) inclus dans le projet
- Exemples : bibliothèque standard (java.lang, java.util...)

## 4.2 Frameworks Java

- **Architectures logicielles préconçues** fournissant structure et outils
- Définissent des **modèles de conception** et des **conventions de codage**
- S'articulent autour de classes et d'interfaces à utiliser et étendre
- Exemple : **Spring Framework**

| **CRITÈRE**         | **BIBLIOTHÈQUE vs FRAMEWORK**                                                    |
|---------------------|----------------------------------------------------------------------------------|
| **Bibliothèque**    | Vous appelez le code de la bibliothèque quand vous en avez besoin                |
| **Framework**       | Le framework appelle votre code (Inversion de contrôle) --- impose une structure |

# 5. L'IDE --- INTELLIJ IDEA / ECLIPSE

## 5.1 Qu'est-ce qu'un IDE ?

Un IDE (Integrated Development Environment / Environnement de Développement Intégré) regroupe dans un seul outil : éditeur de code, compilateur, débogueur et autres fonctionnalités.

## 5.2 IntelliJ IDEA Community Edition

- IDE recommandé dans le cours --- version gratuite (Community Edition)
- Installation via **Toolbox App** de JetBrains

## 5.3 Composants de l'interface IntelliJ

| **ÉLÉMENT**               | **RÔLE**                                          |
|---------------------------|---------------------------------------------------|
| **Barre de navigation**   | Navigation rapide dans le projet                  |
| **Éditeur**               | Interagir avec le code source                     |
| **Barre d'état**          | Messages d'événements et progression des tâches   |
| **Fenêtres d'outils**     | Fonctionnalités supplémentaires                   |
| **Menus contextuels**     | Actions contextuelles                             |
| **Gouttière**             | Icônes d'action et numéros de ligne               |

# 6. OUTILS DE CONSTRUCTION ET DE GESTION DES DÉPENDANCES

## 6.1 Rôle de ces outils

- Automatisent les tâches répétitives du développement logiciel
- Tâches couvertes : **compiler**, générer la documentation, exécuter les tests unitaires, **intégrer** le code, **déployer** l'application
- Gèrent les **dépendances** (bibliothèques externes) entre modules du projet

## 6.2 Les 3 outils principaux

| **OUTIL**        | **CARACTÉRISTIQUES**                                                                               |
|------------------|----------------------------------------------------------------------------------------------------|
| **Ant (ancien)** | Outil de construction (build) simple, sans gestion de dépendances native                          |
| **Maven**        | Outil open source --- fichiers XML (pom.xml) pour déclarer dépendances et configuration de build  |
| **Gradle**       | Plus moderne que Maven, syntaxe plus concise et flexible --- fichiers Groovy pour déclarer dépendances |

> **⚠️ Points critiques à retenir :**
>
> - Maven et Gradle = outils de gestion de dépendances ET de construction (pas des IDE, pas des frameworks !)
> - Maven → fichiers XML | Gradle → fichiers Groovy
> - Avantage gestion de dépendances : facilite la recherche, gère les versions ET évite les conflits
> - Rôle global des outils build : automatiser + gérer versions + déployer
