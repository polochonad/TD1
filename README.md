# ![](ressources/logo.jpeg) Conception et Programmation Objet Avancées 
### IUT Montpellier-Sète – Département Informatique
* **Cours:** [M3105](http://cache.media.enseignementsup-recherche.gouv.fr/file/25/09/7/PPN_INFORMATIQUE_256097.pdf) - support [ici](https://github.com/IUTInfoMontp-M3105/Ressources)
* **Enseignants:** [Sébastien Gagné](mailto:sebastien.gagne@umontpellier.fr), [Petru Valicov](mailto:petru.valicov@umontpellier.fr), [Sophie Nabitz](mailto:sophie.nabitz@univ-avignon.fr) 
* Le [forum Piazza](https://piazza.com/class/jzs4o7je7zm1a0) de ce cours pour poser vos questions
* [Email](mailto:petru.valicov@umontpellier.fr) pour une question d'ordre privée concernant le cours.
* Le [sujet du TP](https://gitprint.com/IUTInfoMontp-M3105/TD1) en format .pdf téléchargeable et imprimable.


## TD1 - Comptes Bancaires
#### _Thème : Rappels des notions d'objet, Java et UML_

* Gardez à l’esprit les différents principes de conception et programmation objet vues l’an
dernier (encapsulation, polymorphisme, DRY, KISS etc.)
* Pensez à respecter les conventions de nommage *Java* :
    * celles d’Oracle : https://www.oracle.com/technetwork/java/codeconventions-150003.pdf
    * une autre convention, par ex. https://google.github.io/styleguide/javaguide.html

Vous trouverez le regroupement de la documentation concernant Git, ainsi que les transparents
du cours, dans [ce dépôt](https://github.com/IUTInfoMontp-M3105/Ressources).

Il est vivement recommandé d’utiliser au maximum les fonctionnalités de l’IDE pour réaliser les
tâches courantes (renommage d’attributs/méthodes, génération des différentes méthodes : construc-
teurs, setters, getters, etc.).

**Conseil :** Afin de garder une trace de la progression de votre application, on vous conseille de
travailler dans un package différent pour chaque exercice. Cela vous permettra de mieux comparer
votre travail pour chaque exercice et vous permettra également de mieux réviser plus tard.

Cliquez sur le lien ci-dessous pour faire votre fork privé du TP :

LIEN CLASSROOM À METTRE ICI

Date limite de rendu de votre code sur le dépôt GitHub : **Dimanche 15 Septembre, 23h00**

### Exercice 1
Dans la banque *BronzeManCrooks* un client souhaitant avoir un *compte* doit choisir parmi les différents types : *compte courant*, *livret*, *compte pro* etc. Il y a plusieurs types de livrets : *livret A*, *livret d'épargne PlusPlus*, *livret de spéculation*, etc.

Tous les comptes ont un solde (`double`), un IBAN (une donnée de type `String`), un nom de client et une adresse (des données de type `String`). Toutes ces données sont initialisées avec le constructeur. Le nom peut être modifié avec une méthode *modifieur* (*setter*). Une méthode *accesseur* `public double getSolde()` doit retourner le solde de chaque compte. Un compte pro possède en plus un numéro SIREN, alors que le compte courant enregistre le NoINSEE de la personne physique détenteur du compte.

Chaque livret possède un *taux d'intérêts* de type `double`. Vous pouvez supposer que cette valeur réelle est entre 0 et 1. Ainsi, la méthode `public double getSolde()` doit retourner le solde de compte + les intérêts (dans la vraie vie, ça serait trop beau, mais on va supposer pour le fun que c'est comme ça...). De plus le livret A a un *plafond* de dépôt maximum, le livre d’épargne a un *taux d'imposition* (valeur réelle entre 0 et 1) et le livret de spéculation a deux données : une *taxe* fixe qui s'appliquera à chaque transaction réalisé avec ce livret et le *nombre de transactions*.

**Remarque :** Dans ce qui suit il ne vous est pas demandé de modéliser le client, la seule information le concernant étant l'attribut `nom` évoqué ci-dessus.

**Remarque :** La plupart de questions sont assez simples en revanche on attend de votre part d'écrire du code propre respectant les différents principes objets : encapsulation, non-duplication de code, etc.


1. Proposez un diagramme de classes en y indiquant les relations entre les classes, les attributs, les méthodes, ainsi que leur visibilité. Votre solution doit permettre l'ajout facile d'autres types de comptes. Vous pouvez utiliser un logiciel de modélisation que vous souhaitez où bien le faire sur papier.

    **Remarque :** un compte ou un livret ne peuvent pas exister en tant que tels, ils doivent forcément être d'un type spécifique (compte courant ou livret A par exemple).
  
2. Écrivez le code `Java` correspondant et implémentez également la méthode `toString()` pour permettre l'affichage de l'intégralité des informations du compte. Vérifiez le bon fonctionnement de votre programme en implémentant la méthode principe `public static void main(String args[])` de la classe `App`. Vous allez créer au moins un compte pour chacun des 5 types de comptes mentionnés ci-dessus et les initialiser avec des valeurs d'attributs **distinctes**.

3. On vous demande maintenant d'ajouter un plafond de découverte pour tous les comptes, qui est à initialiser avec un méthode *setter*. Combien d'ajout et de modifications devez-vous faire dans votre code ?
   \question On vient vers vous avec une nouvelle précision : avec la mise en place du prélèvement à la source par le gouvernement, il faut que le solde de chaque type de livret tienne compte des différentes taxes. Ajoutez cette fonctionnalité **sans modifier** le programme précédemment écrit.
   
4. Moyennant un *prix* fixé par l'utilisateur (donnée de type `double`), il est possible de détenir un *compte groupé* : un regroupement de plusieurs comptes différents. Le nombre de "sous-comptes" autorisés dans un tel compte groupé est potentiellement illimité et il est toujours possible d'en ajouter (à travers une méthode). De plus, il est possible d'avoir plusieurs comptes groupés dans un compte groupé (pour chaque membre de sa famille par exemple, ou pour son entreprise...). Dans tous les cas, chaque compte groupé aura son propre prix.
   
   Complétez votre diagramme de classes et proposez une implémentation en *Java*. Assurez-vous que la méthode `public double getSolde()}` retourne la somme des soldes de tous les "sous-comptes" du compte groupé correspondant.
   
   **NB :** à la création vous pouvez supposer que le solde d'un compte groupé est 0.
   
5. On souhaite pouvoir afficher l'ensemble des informations de chacun des comptes d'un compte groupé. En vous inspirant de l'exemple précédent, redéfinissez la méthode `toString()` dans les classes qui vous semblent appropriées afin que cette méthode retourne une chaîne de caractères contenant l'intégralité des informations du compte correspondant.

6. Dans la méthode principale `public static void main(String args[])` de la classe cliente (`App`) effectuez les actions suivantes dans l'ordre :

    *  créer un compte groupé pour le client "Tintin Duchmolle" et lui ajouter un compte groupé contenant un compte courant *A* et un compte groupé *B*. Le compte groupé *B* devra contenir un *livret A*, un *livret PlusPlus* et un *livret de spéculation*.
    * afficher le solde total de tous les comptes
    * afficher l'ensemble des informations concernant chacun des comptes.