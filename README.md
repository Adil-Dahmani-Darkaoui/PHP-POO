# PHP-POO

#Qu’est-ce que la programmation orientée objet (POO) ?

La programmation orientée objet (ou POO en abrégé) correspond à une autre manière d’imaginer, de construire et d’organiser son code.

Jusqu’à présent, nous avons codé de manière procédurale, c’est-à-dire en écrivant une suite de procédures et de fonctions dont le rôle était d’effectuer différentes opérations sur des données généralement contenues dans des variables et ceci dans leur ordre d’écriture dans le script.


 
La programmation orientée objet est une façon différente d’écrire et d’arranger son code autour de ce qu’on appelle des objets. Un objet est une entité qui va pouvoir contenir un ensemble de fonctions et de variables.

L’idée de la programmation orientée objet va donc être de grouper des parties de code qui servent à effectuer une tâche précise ensemble au sein d’objets afin d’obtenir une nouvelle organisation du code.

Les intérêts principaux de la programmation orientée objet vont être une structure générale du code plus claire, plus modulable et plus facile à maintenir et à déboguer.

#Classes, objets et instance : première approche

La programmation orientée objet se base sur un concept fondamental qui est que tout élément dans un script est un objet ou va pouvoir être considéré comme un objet. Pour comprendre ce qu’est précisément un objet, il faut avant tout comprendre ce qu’est une classe.

Une classe est un ensemble cohérent de code qui contient généralement à la fois des variables et des fonctions et qui va nous servir de plan pour créer des objets. Une classe est donc un bloc de code qui va contenir différentes variables, fonctions et éventuellement constantes et qui va servir de plan de création pour différents objets. Chaque objet créé à partir d’une même classe dispose des mêmes variables, fonctions et constantes définies dans la classe mais va pouvoir les implémenter différemment.
Le but d’une classe va donc être de créer des objets que nous allons ensuite pouvoir manipuler.

#Classes et objets : exemple de création

En PHP, on crée une nouvelle classe avec le mot clef class. On peut donner n’importe quel nom à une nouvelle classe du moment qu’on n’utilise pas un mot réservé du PHP et que le premier caractère du nom de notre classe soit une lettre ou un underscore.

Par convention, on placera généralement chaque nouvelle classe créée dans un fichier à part et on placera également tous nos fichiers de classe dans un dossier qu’on pourra appeler classes par exemple pour plus de simplicité.

On n’aura ensuite qu’à inclure les fichiers de classes nécessaires à l’exécution de notre script principal dans celui-ci grâce à une instruction require par exemple.

Une instance correspond à la « copie » d’une classe. Le grand intérêt ici est qu’on va pouvoir effectuer des opérations sur chaque instance d’une classe sans affecter les autres instances.

A chaque fois qu’on instancie une classe, un objet est également automatiquement créé. Les termes « instance de classe » et « objet » ne désignent pas fondamentalement la même chose mais dans le cadre d’une utilisation pratique on pourra très souvent les confondre et c’est ce que nous allons faire dans ce cours.

Pour information, la grande différence est que chaque instance de classe est unique et peut donc être identifiée de manière unique ce qui n’est pas le cas pour les objets d’une même classe.

Lorsqu’on instancie une classe, un objet est donc créé. Nous allons devoir capturer cet objet pour l’utiliser. Pour cela, nous allons généralement utiliser une variable qui deviendra alors une « variable objet » ou plus simplement un « objet ».

Pour être tout à fait précis, notre variable en question ne va pas exactement contenir l’objet en soi mais plutôt une référence à l’objet.

#Classes, instances et objets : l’essentiel à retenir

Une classe est un « plan d’architecte » qui va nous permettre de créer des objets qui vont partager ses variables et ses fonctions. Chaque objet créé à partir d’une classe va disposer des mêmes variables et fonctions définies dans la classe mais va pouvoir implémenter ses propres valeurs (impostant : une classe peut implémenter plusieurs interfaces, mais ne peut hériter que d’une seule classe).

Pour créer un objet, il faut instancier la classe en utilisant le mot clef new. Une instance est une « copie » de classe. On va stocker notre instance ou notre objet dans une variable pour pouvoir l’utiliser.

Pour donner un parallèle avec la vie de tous les jours, imaginons le plan de création de base d’un modèle de voiture. Ce plan va définir les différents éléments des voitures, c’est-à-dire de quoi va être composée chaque voiture (un moteur, des portes, des roues, une peinture, etc.) ainsi que les actions de chaque voiture, c’est-à-dire ce que peut faire chaque voiture (accélérer, allumer les phares, etc.).

Nous allons pouvoir créer des voitures à partir de ce plan qui va être l’équivalent d’une classe et chaque voiture créée à partir de celui-ci va posséder les éléments (= variables) et actions (= fonctions) définies dans le plan. Les voitures créées sont ici nos objets.

Cependant, les éléments vont pouvoir avoir des apparences différentes : chaque voiture va posséder un moteur mais le moteur va pouvoir être différent pour chaque voiture (plus ou moins puissant). De même, chaque voiture va posséder une couleur mais la couleur de chaque voiture va pouvoir être différente.

Chaque voiture créée à partir du plan va avoir accès au même nombre d’actions mais les différentes actions des voitures vont être différentes en fonction des éléments de chaque voiture : chaque voiture va pouvoir accélérer mais une voiture avec un moteur plus puissant va accélérer plus vite qu’une autre qui possède un moteur plus petit.

Petit résumé sur les classes:
```
[abstract ]class MaClasse [extends AutreClasse implements Interface]
{
    public|protected|private [static] $maVariable [= valeur];
    public static $etat = 1;
     
    /**
     * Constructeur
    */
    public|protected|private function MaClass|__construct()
    {
        // Déclaration des variables et autres
    }
     
    /**
     * Fonction classique
    */
    public|protected|private [static final abstract] function maMethode()
    {
        // Action de la fonction maMethode
        $this--->maVariable = 'test';
        self::$etat = 0;
        $this-&gt;autreMethode();
        [parent::autreMethode();]
    }
    public function $autreMethode()
    {
        echo 'Hello world!';
    }
}
```

Petit résumé sur les interfaces:
```
interface Interface [extends AutreInterface]
{
    /**
     * Fonction classique
    */
    public function $maMethode();
    /**
     * Autre fonction classique
    */
    public function $autreMethode();
}
```

Petit résumé sur les singletons:

```
class Singleton
{
    /**
     * Variable static valant null si la classe n'est pas encore instanciée
     * ou contenant l'instance si la classe est instanciée.
     * On y accède avec self::$_instance
    */
    private static $_instance = null;
     
    /**
     * Constructeur private inaccessible en dehors de la classe
    */
    private function __construct()
    {
        // On instancie ce qu'il faut
    }
     
    /**
     * Accessor static, donc accessible sans être instancié, renvoyant 
     * l'instance, en la créant si besoin
    */
    public static function getInstance()
    {
        if (self::$_instance == null) {
            self::$_instance = new Singleton();
        }
        return self::$_instance;
    }
}
```
#Méthodes
Il s'agit des fonctions utilisées pour une même classe. Elle est précédée du mot-clé ``function`` et de la visibilité de la méthode. Les types de visibilité des méthodes sont les mêmes que les attributs. Les méthodes n'ont en général pas besoin d'être masquées à l'utilisateur, le plus souvent elles seront en ``public`` (à moins qu'on tienne absolument à ce que l'utilisateur ne puisse pas appeler cette méthode, par exemple s'il s'agit d'une fonction qui simplifie certaines tâches sur l'objet mais qui ne doit pas être appelée n'importe comment).
````
class Personnage
{
  private $_force;        
  private $_localisation; 
        
  public function deplacer() // Une méthode qui déplacera le personnage (modifiera sa localisation).
  {

  }
}
````
Pour appeler une méthode d'un objet, il va falloir utiliser un opérateur : il s'agit de l'opérateur ```->``` (une flèche composée d'un tiret suivi d'un chevron fermant). À gauche de cet opérateur, on place l'objet que l'on veut utiliser. À droite de l'opérateur, on spécifie le nom de la méthode que l'on veut invoquer.
````
class Personnage {
private $_force;
private $_localisation;

// Nous déclarons une méthode dont le seul but est d'afficher un texte.
public fonction parler() {

echo 'Je suis un personnage!';
    }
}
$perso = new Personnage; 
$perso->parler();
````
La dernière ligne signifie donc « va chercher l'objet ```$perso```, et invoque la méthode ``parler()`` sur cet objet ».

Cet opérateur peut également servir à atteindre un attribut.
* La pseudo-variable ``$this``
Elle permet au sein d'une méthode d'attribuer implicitement un paramètre. Comme on ne peut pas accéder à une méthode ou attibut privé(e) en dehors de la classe, $this permet de représenter l'objet au sein de la classe et d'obtenir le résultat en dehors:
````
class Personnage
{
  private $_experience = 50;

  public function afficherExperience()
  {
    echo $this->_experience;
  }
}

$perso = new Personnage;
$perso->afficherExperience();
````
En résumé, ```$this``` est une variable représentant l'objet à partir duquel on a appelé la méthode.

Il est possible de passer un argument à une méthode:
````
// On crée deux personnages
$perso1 = new Personnage;
$perso2 = new Personnage;
    
public function frapper($persoAFrapper)
 {
   $persoAFrapper->_degats += $this->_force;
 }

// Ensuite, on veut que le personnage n°1 frappe le personnage n°2.
$perso1->frapper($perso2);
````
Pour s'assurer que l'on passe bien en paramètre un objet et éviter ainsi les erreurs, il suffit de préciser dans les parenthèses le nom de la classe:
````
class Personnage
{
  //...

  public function frapper(Personnage $persoAFrapper)
  {
    // …
  }
}
````
Grâce à ça, on est sûrs que la méthode ``frapper()`` ne sera exécutée que si le paramètre passé est de type Personnage, sinon PHP interrompt tout le script. On peut donc appeler les méthodes de l'objet sans crainte qu'un autre type de variable soit passé en paramètre.
* <b>Les méthodes statiques</b>
Les méthodes statiques sont des méthodes qui sont faites pour agir sur une classe et non sur un objet.

Pour déclarer une méthode statique, il faut faire précéder le mot-clé function du mot-clé static après le type de visibilité.
````
  public static function parler()
  {
    echo 'Je vais tous vous tuer !';
  }
````
Et dans le code:
````
Personnage::parler();
````

#Public / Private
Si un attribut ou une méthode est ``public``, alors on pourra y avoir accès depuis n'importe où, depuis l'intérieur de l'objet (dans les méthodes qu'on a créées), comme depuis l'extérieur.

S'il est ``private``, il y a quelques restrictions. On aura accès aux attributs et méthodes seulement depuis l'intérieur de la classe, c'est-à-dire que seul le code voulant accéder à un attribut privé ou une méthode privée écrit(e) à l'intérieur de la classe fonctionnera.
````
class Personnage {
private $_force;        //On définit les attributs qui ne seront utilisables qu'à l'intérieur de la classe
private $_localisation;
}
````
Les attributs respectent la notation PEAR, qui dit que chaque nom d'élément privé (attributs ou méthodes) doit être précédé d'un underscore.

#Accesseurs (ou getters)
C'est une méthode dont le rôle est de renvoyer l'attribut qu'on lui demande. Par convention, ces méthodes portent le même nom que l'attribut dont elles renvoient la valeur.
````
class Personnage
{
  private $_force;
  private $_experience;
  private $_degats;
        
  // Ceci est la méthode degats() : elle se charge de renvoyer le contenu de l'attribut $_degats.
  public function degats()
  {
    return $this->_degats;
  }
        
  // Ceci est la méthode force() : elle se charge de renvoyer le contenu de l'attribut $_force.
  public function force()
  {
    return $this->_force;
  }
        
  // Ceci est la méthode experience() : elle se charge de renvoyer le contenu de l'attribut $_experience.
  public function experience()
  {
    return $this->_experience;
  }
}
````
#Mutateurs (ou setters)
Méthode permettant de modifier un attribut. Ces méthodes sont de la forme ``setNomDeLAttribut()``:
````
// Mutateur chargé de modifier l'attribut $_force.
  public function setForce($force)
  {
    if (!is_int($force)) // S'il ne s'agit pas d'un nombre entier.
    {
      trigger_error('La force d\'un personnage doit être un nombre entier', E_USER_WARNING);
      return;
    }
    
    if ($force > 100) // On vérifie bien qu'on ne souhaite pas assigner une valeur supérieure à 100.
    {
      trigger_error('La force d\'un personnage ne peut dépasser 100', E_USER_WARNING);
      return;
    }
    
    $this->_force = $force;
  }
  
  // Mutateur chargé de modifier l'attribut $_experience.
  public function setExperience($experience)
  {
    if (!is_int($experience)) // S'il ne s'agit pas d'un nombre entier.
    {
      trigger_error('L\'expérience d\'un personnage doit être un nombre entier', E_USER_WARNING);
      return;
    }
    
    if ($experience > 100) // On vérifie bien qu'on ne souhaite pas assigner une valeur supérieure à 100.
    {
      trigger_error('L\'expérience d\'un personnage ne peut dépasser 100', E_USER_WARNING);
      return;
    }
    
    $this->_experience = $experience;
  }
````

#Scope Resolution Operator ``::``
Il est utilisé pour appeler des éléments appartenant à telle classe et non à tel objet. En effet, nous pouvons définir des attributs et méthodes appartenant à la classe : ce sont des éléments statiques.

Parmi les éléments appartenant à la classe, il y a aussi les constantes de classe, sortes d'attributs dont la valeur est constante, c'est-à-dire qu'elle ne change pas.
* Les constantes de classe Une constante est une sorte d'attribut appartenant à la classe dont la valeur ne change jamais.

Pour déclarer une constante, il faut faire précéder son nom du mot-clé ``const``.
````
class Personnage
{
  // Tous les attributs en privé !
  private $_force;
  private $_localisation;
  private $_experience;
  private $_degats;


  // Déclarations des constantes en rapport avec la force.
  const FORCE_PETITE = 20;
  const FORCE_MOYENNE = 50;
  const FORCE_GRANDE = 80;

  public function __construct()
  {

  }

  public function deplacer()
  {

  }

  public function frapper()
  {

  }

  public function gagnerExperience()
  {

  }
}
````
Pour accéder à une constante, il faut spécifier le nom de la classe, suivi du symbole double deux points, suivi du nom de la constante.
````
class Personnage
{
  private $_force;
  private $_localisation;
  private $_experience;
  private $_degats;


  // Déclarations des constantes en rapport avec la force.
  const FORCE_PETITE = 20;
  const FORCE_MOYENNE = 50;
  const FORCE_GRANDE = 80;


  public function __construct($forceInitiale)
  {
    //Assigneation de la valeur d'un attribut uniquement depuis son setter !
    $this->setForce($forceInitiale);
  }

  public function deplacer()
  {

  }

  public function frapper()
  {

  }

  public function gagnerExperience()
  {

  }
  
  public function setForce($force)
  {
    // On vérifie qu'on nous donne bien soit une « FORCE_PETITE », soit une « FORCE_MOYENNE », soit une « FORCE_GRANDE ».
    if (in_array($force, [self::FORCE_PETITE, self::FORCE_MOYENNE, self::FORCE_GRANDE]))
    {
      $this->_force = $force;
    }
  }
}
````
Du coup, lors de la création de l'objet:
````
// On envoie une « FORCE_MOYENNE » en guise de force initiale.
$perso = new Personnage(Personnage::FORCE_MOYENNE);
````
A noter que les constantes se notent en majuscules.

#L'hydratation

L'hydratation est un point essentiel dans le domaine de la POO, notamment lorsqu'on utilise des objets représentant des données stockées.

Quand on vous parle d'hydratation, c'est qu'on parle d'« objet à hydrater ». Hydrater un objet, c'est tout simplement lui apporter ce dont il a besoin pour fonctionner. En d'autres termes plus précis, hydrater un objet revient à lui fournir des données correspondant à ses attributs pour qu'il assigne les valeurs souhaitées à ces derniers. L'objet aura ainsi des attributs valides et sera en lui-même valide. On dit que l'objet a ainsi été hydraté.

On peut donc écrire une fonction hydrate():

````// Un tableau de données doit être passé à la fonction (d'où le préfixe « array »).
      public function hydrate(array $donnees)
      {
        foreach ($donnees as $key => $value)
        {
          // On récupère le nom du setter correspondant à l'attribut.
          $method = 'set'.ucfirst($key);
              
          // Si le setter correspondant existe.
          if (method_exists($this, $method))
          {
            // On appelle le setter.
            $this->$method($value);
          }
        }
      }
````

#Attributs

Il s'agit d'une variable. Il est possible ou non de les initialiser lors de leur déclaration. Ils sont toujours(?) privés (alors que la méthode pourra être privée ou publique), c'est ce qu'on appelle l'encapsulation.

````
class Personnage {
private $_force = 50;
private $_degats;
}
````
La valeur donnée par défaut doit être une expression scalaire statique. Par conséquent, leur valeur ne peut par exemple pas être issue d'un appel à une fonction ( private $_attribut = strlen('azerty') ) ou d'une variable, superglobale ou non ( private $_attribut = $_SERVER['REQUEST_URI'] ).

#Instanciation d’une classe et destruction d’objets

Lorsqu’on instancie une classe avec le mot clé new, on créé une référence de cette instanciation.
Et si on fait une copie de cet objet avec le symbole =, on créé une nouvelle référence vers cette instanciation.
Or pour supprimer une instanciation d’une classe, avec la fonction unset(), il faut que toutes les références de cette classe soient supprimées. Pour bien comprendre, reprenons l’exemple de Développez.com.
Pour cela, il faut savoir que la méthode magique __destruct() est déclenchée lorsqu’on supprime une instance d’une classe.
```
<?php
class Blog {
  function __destruct()
  {
    echo 'Je me meurs !';
  }
}
$monBlog = new Blog();
$monAutreBlog = $monBlog;
echo 'Allons soldats, tuons monBlog !';
unset($monBlog);
echo 'Puisqu\'il résiste, éliminons donc son frère !';
unset($monAutreBlog);

```
<b>Cet exemple affichera :</b>

Allons soldats, tuons monBlog ! <br>
Puisqu'il résiste, éliminons donc son frère ! <br>
Je me meurs !

#Qu'est ce que "cloner" en php POO

Au lieu d’utiliser le symbole =, on peut aussi utiliser le mot clé clone pour signifier que l’on fait une nouvelle instanciation de la classe.

La référence qui est créée vers cette instanciation n’a donc plus rien à voir avec la première.
Le résultat du code suivant devient alors évident :

```
<?php
   class Blog {
     function __destruct()
     {
       echo 'Je me meurs !';
     }
   }
   $monBlog = new Blog();
   $monAutreBlog = clone $monBlog;
   echo 'Allons soldats, tuons monBlog !';
   unset($monBlog);
   echo 'Continuons sur notre lancée, éliminons donc son frère !';
   unset($monAutreBlog);
```

<b>Cet exemple affichera :</b>

Allons soldats, tuons monBlog ! <br>
Je me meurs ! <br>
Continuons sur notre lancée, éliminons donc son frère ! <br>
Je me meurs ! 

#Résumons et clarifions

… = … : créé une nouvelle référence vers l’objet -> Si on modifie l’objet les deux instances sont donc modifiées
… = clone … : créé un nouvel objet -> Si on modifie l’un des deux objets, cela ne modifie pas l’autre

```
<?php
class Blog {
  var $nom;
}
$monBlog = new Blog();
$monBlog->nom = 'Bnbox !';
echo 'Valeur de $monBlog initialisée<br />';
echo '$monBlog : '.$monBlog->nom.'<br />';
$monAutreBlog = $monBlog;
$tonBlog = clone $monBlog;
echo '$monAutreBlog : '.$monAutreBlog->nom.'<br />';
echo '$tonBlog : '.$tonBlog->nom.'<br />';
echo '<br />Valeur de $monBlog modifiée<br />';
$monBlog->nom = '30 minutes par jour';
echo '$monBlog : '.$monBlog->nom.'<br />';
echo '$monAutreBlog : '.$monAutreBlog->nom.'<br />';
echo '$tonBlog : '.$tonBlog->nom.'<br />';
echo '<br />Valeur de $monAutreBlog modifiée<br />';
$monAutreBlog->nom = 'Bible Ipsum';
echo '$monBlog : '.$monBlog->nom.'<br />';
echo '$monAutreBlog : '.$monAutreBlog->nom.'<br />';
echo '$tonBlog : '.$tonBlog->nom.'<br />';
echo '<br />Valeur de $tonBlog modifiée<br />';
$tonBlog->nom = 'Flamb\'clair';
echo '$monBlog : '.$monBlog->nom.'<br />';
echo '$monAutreBlog : '.$monAutreBlog->nom.'<br />';
echo '$tonBlog : '.$tonBlog->nom.'<br />';
```

<b>Ce qui affichera :</b>

Valeur de $monBlog initialisée <br>
$monBlog : Bnbox ! <br>
$monAutreBlog : Bnbox ! <br>
$tonBlog : Bnbox !

Valeur de $monBlog modifiée <br>
$monBlog : 30 minutes par jour <br>
$monAutreBlog : 30 minutes par jour <br>
$tonBlog : Bnbox !

Valeur de $monAutreBlog modifiée <br>
$monBlog : Bible Ipsum <br>
$monAutreBlog : Bible Ipsum <br>
$tonBlog : Bnbox !

Valeur de $tonBlog modifiée <br>
$monBlog : Bible Ipsum <br>
$monAutreBlog : Bible Ipsum <br>
$tonBlog : Flamb'clair <br>
Bref le clonage n’est vraiment pas qu’une question de référence

#Les 3 fondamentaux de la POO

La Programmation Orientée Objet est dirigée par 3 fondamentaux : encapsulation, héritage et polymorphisme.

<b>Encapsulation:</b><br>
L’encapsulation permet de faire voir l’objet à l’extérieur comme une boîte noire ayant certaines propriétés (attributs et fonctions) et ayant un comportement spécifié. La manière dont ces propriétés ont été implémentées est alors cachée aux utilisateurs de la classe. L’implémentation peut être modifiée sans changer le comportement extérieur de l’objet. Cela permet donc de séparer la spécification du comportement d’un objet, de l’implémentation pratique de ces spécifications.

<b>Héritage:</b><br>
L’héritage, permettant entre autres la réutilisabilité et l’adaptabilité des objets. Ce principe est basé sur des classes dont les "filles" héritent des caractéristiques de leur(s) "mère(s)". Chacune des classes filles peut donc posséder les mêmes caractéristiques que ses classes mères et bénéficier de caractéristiques supplémentaires à celles de ces classes mères. Bien sur, toutes les méthodes de la classe héritée (fille) peuvent être redéfinies. Chaque classe fille peut, si le programmeur n’a pas défini de limitation, devenir à son tour classe mère.

<b>Polymorphisme:</b><br>
Cette capacité dérive directement du principe d’héritage vu précédemment. En effet, comme on le sait déjà, un objet va hériter des attributs et méthodes de ses ancêtres. Mais un objet garde toujours la capacité de pouvoir redéfinir une méthode. On voit donc apparaître ici ce concept de polymorphisme : choisir en fonction des besoins quelle méthode ancêtre appeler, et ce au cours même de l’exécution.

#Visibilité

De par le principe de l’encapsulation, il convient de pouvoir masquer certaines données et méthodes internes les gérant, et de pouvoir laisser visibles certaines autres devant servir à la gestion publique de l’objet. C’est le principe de la visibilité.

<b>Attributs et méthodes publics:</b><br>
Les attributs et méthodes dits publics sont accessibles par tous.

<b>Attributs et méthodes privés:</b><br>
La visibilité privée restreint la portée d’un attribut ou d’une méthode à l’objet où il ou elle est déclaré(e).

<b>Attributs et méthodes protégés:</b><br>
La visibilité protégée correspond à la visibilité privée excepté que tout attribut ou méthode protégé(e) est accessible dans tous les descendants (c’est à dire dans toutes les classes filles).

#Différents types de méthodes

Voici la description de quelques méthodes particulières à la Programmation Orientée Objet.

<b>Constructeurs et destructeurs</b><br>
Parmi les différentes méthodes d’un objet se distinguent deux types de méthodes bien particulières et remplissant un rôle précis dans sa gestion : les constructeurs et les destructeurs.

<b>Constructeurs</b><br>
Comme leur nom l’indique, les constructeurs servent à construire l’objet en mémoire. Un constructeur va se charger de mettre en place les données, d’associer les méthodes avec les attributs et de créer le diagramme d’héritage de l’objet, autrement dit de mettre en place toutes les liaisons entre les ancêtres et les descendants. Il peut exister en mémoire plusieurs instances d’un même type objet, par contre seule une copie des méthodes est conservée en mémoire, de sorte que chaque instance se réfère à la même zone mémoire en ce qui concerne les méthodes. Bien entendu, les attributs sont distincts d’un objet à un autre.

Quelques remarques concernant les constructeurs:

* Un objet peut ne pas avoir de constructeur explicite, il est alors créer par le compilateur.

* Certains langages (comme le Java) autorise d’avoir plusieurs constructeurs : c’est l’utilisateur qui décidera du constructeur à appeler. Comme pour toute méthode, un constructeur peut être surchargé, et donc effectuer diverses actions en plus de la construction même de l’objet. On utilise ainsi généralement les constructeurs pour initialiser les attributs de l’objet.

* S’il n’est pas nécessaire de fournir un constructeur pour un objet statique, il devient obligatoire en cas de gestion dynamique, car le diagramme d’héritage ne peut être construit de manière correcte que lors de l’exécution, et non lors de la compilation.

<b>Destructeurs</b><br>
Le destructeur est le pendant du constructeur : il se charge de détruire l’instance de l’objet. La mémoire allouée pour le diagramme d’héritage est libérée. Certains compilateurs peuvent également se servir des destructeurs pour éliminer de la mémoire le code correspondant aux méthodes d’un type d’objet si plus aucune instance de cet objet ne réside en mémoire.

Quelques remarques sur les destructeurs :

* Tout comme pour les constructeurs, un objet peut ne pas avoir de destructeur. Une fois encore, c’est le compilateur qui se chargera de la destruction statique de l’objet.

* Certains langages autorise d’avoir plusieurs destructeurs. Leur rôle commun reste identique, mais peut s’y ajouter la destruction de certaines variables internes pouvant différer d’un destructeur à l’autre.<br>
constructeur distinct est associé un destructeur distinct.

* En cas d’utilisation dynamique, un destructeur s’impose pour détruire le diagramme créé par le constructeur.

#Constructeur
C'est une méthode écrite dans la classe, qui d'initialiser les attributs dès la création de l'objet.

Il s'écrit comme ceci: ``__construct`` avec deux underscore au début.

Comme son nom l'indique, le constructeur sert à construire l'objet. Il est exécuté dès la création de l'objet et par conséquent, aucune valeur ne doit être retournée. Une classe fonctionne très bien sans constructeur, il n'est en rien obligatoire!
````
public function __construct($force, $degats) // Constructeur demandant 2 paramètres
  {
    echo 'Voici le constructeur !'; // Message s'affichant une fois que tout objet est créé.
    $this->setForce($force); // Initialisation de la force.
    $this->setDegats($degats); // Initialisation des dégâts.
    $this->_experience = 1; // Initialisation de l'expérience à 1.
  }

$perso1 = new Personnage(60, 0); // 60 de force, 0 dégât
$perso2 = new Personnage(100, 10); // 100 de force, 10 dégâts
````
Dans le constructeur, les valeurs sont initialisées en appelant les mutateurs correspondant. En effet, si on assignait directement ces valeurs avec les arguments, le principe d'encapsulation ne serait plus respecté et n'importe quel type de valeur pourrait être assigné !

On ne met jamais la méthode ``__construct`` avec le type de visibilité ``private`` car elle ne pourra jamais être appelée, one ne pourra donc pas instancier notre classe !

#Méthodes et classes abstraites

<b>Méthodes abstraites</b><br>
Une méthode abstraite est une méthode qu’il est nécessaire de surcharger. Elle ne possède pas d’implémentation. Ainsi, si on tente d’appeler une méthode abstraite, une erreur est déclenchée. Les méthodes abstraites sont généralement utilisées lorsque l’on bâtit un squelette d’objet devant donner lieu à de multiples descendants devant tous posséder un comportement analogue.

<b>Classe abstraite</b><br>
On retrouve le même principe au niveau de la classe. Une classe abstraite ne peut pas être instanciée. Par contre il est possible d’y mélanger des méthodes abstraites et concrète.

<b>Interface</b><br>
Une interface est un cas particulier de la classe abstraite car toutes ces méthodes sont abstraites. Seule l’interface de la classe apparaît.

#Interface

Techniquement, une interface est une classe entièrement abstraite. Son rôle est de décrire un comportement à notre objet. Une interface se déclare avec le mot-clé interface, suivi du nom de l'interface, suivi d'une paire d'accolades:
````
interface Movable
{
  public function move($dest);
}
````
Exemple: une voiture et un personnage n'ont pas de raison d'hériter d'une même classe, par contre, les deux doivent avoir la possibilité de se déplacer, donc on peut créer une interface représentant ce point commun.

* Toutes les méthodes présentes dans une interface doivent être publiques.

* Une interface ne peut pas lister de méthodes abstraites ou finales.

* Une interface ne peut pas avoir le même nom qu'une classe et vice-versa.

Il faut ensuite implémenter l'interface à la classe avec le mot-clé implements (c'est un peu comme faire hériter une classe d'une autre):

````
class Personnage implements Movable
{

}
````

Puis il faut alors obligatoirement implémenter les méthodes de l'interface dans la classe qui utilise l'interface (la méthode peut alors être abstraite ou finale dans la classe).

On peut implémenter plus d'une interface par classe, à condition qu'elles n'aient aucune méthode portant le même nom.

````
interface iA
{
  public function test1();
}

interface iB
{
  public function test2();
}

class A implements iA, iB
{
  // Pour ne générer aucune erreur, il va falloir écrire les méthodes de iA et de iB.
  
  public function test1()
  {
  
  }
  
  public function test2()
  {
  
  }
}
````
* Les constantes d'interface
Elles fonctionnent exactement comme les constantes de classes. Elles ne peuvent être écrasées par des classes qui implémentent l'interface.
````
interface iInterface
{
 const MA_CONSTANTE = 'Hello !';
}

echo iInterface::MA_CONSTANTE; // Affiche Hello !

class MaClasse implements iInterface
{

}

echo MaClasse::MA_CONSTANTE; // Affiche Hello !
````
* Héritage d'interface

Comme pour les classes, on peut faire hériter une interface d'une autre avec le mot-clé extands.

Par contre, on ne peut réécrire ni une méthode ni une constante qui a déjà été listée dans l'interface parente.

Contrairement aux classes, les interfaces peuvent hériter de plusieurs interfaces à la fois. Il suffit de séparer leur nom par une virgule.

````
interface iA
{
  public function test1();
}

interface iB
{
  public function test2();
}

interface iC extends iA, iB
{
  public function test3();
}
````
Dans cet exemple, si on imagine une classe implémentant iC, celle-ci devra implémenter les trois méthodes test1,test2 et test3.

* Interfaces prédéfinies

Il existe beaucoup d'interfaces prédéfinies. En voici quelques unes:

### ``Iterator``
Si notre classe implémente cette interface, on pourra modifier le comportement de notre objet lorsqu'il est parcouru. Cette interface comporte 5 méthodes:

current: renvoie l'élément coourant. key: retourne la clé de l'élément courant. next: déplace le pointeur sur l'élément suivant. rewind: remet le pointeur sur le premier élément. valid: vérifie si la position courante est valide.

C'est très pratique pour parcourir les attributs qui sont des tableaux, car on va pouvoirrenvoyer la valeur qu'on veut. Exemple:
````
class MaClasse implements Iterator
{
  private $position = 0;
  private $tableau = ['Premier élément', 'Deuxième élément', 'Troisième élément', 'Quatrième élément', 'Cinquième élément'];
  
  /**
   * Retourne l'élément courant du tableau.
   */
  public function current()
  {
    return $this->tableau[$this->position];
  }
  
  /**
   * Retourne la clé actuelle (c'est la même que la position dans notre cas).
   */
  public function key()
  {
    return $this->position;
  }
  
  /**
   * Déplace le curseur vers l'élément suivant.
   */
  public function next()
  {
    $this->position++;
  }
  
  /**
   * Remet la position du curseur à 0.
   */
  public function rewind()
  {
    $this->position = 0;
  }
  
  /**
   * Permet de tester si la position actuelle est valide.
   */
  public function valid()
  {
    return isset($this->tableau[$this->position]);
  }
}

$objet = new MaClasse;

foreach ($objet as $key => $value)
{
  echo $key, ' => ', $value, '<br />';
}
````
### ``SeekableIterator``
Cette interface hérite de l'interface Iterator, on n'aura donc pas besoin d'implémenter les deux à notre classe. Elle ajoute une méthode à la listedes méthodes Iterator: la méthode seek, qui permet de placer le curseur interne à une position précise (elle demande donc un argument).
````
class MaClasse implements SeekableIterator
{
  private $position = 0;
  private $tableau = ['Premier élément', 'Deuxième élément', 'Troisième élément', 'Quatrième élément', 'Cinquième élément'];
  
  // Retourne l'élément courant du tableau.

  public function current()
  {
    return $this->tableau[$this->position];
  }
  

   // Retourne la clé actuelle (c'est la même que la position dans notre cas).

  public function key()
  {
    return $this->position;
  }
  

   // Déplace le curseur vers l'élément suivant.

  public function next()
  {
    $this->position++;
  }
  

   // Remet la position du curseur à 0.

  public function rewind()
  {
    $this->position = 0;
  }
  

   // Déplace le curseur interne.

  public function seek($position)
  {
    $anciennePosition = $this->position;
    $this->position = $position;
    
    if (!$this->valid())
    {
      trigger_error('La position spécifiée n\'est pas valide', E_USER_WARNING);
      $this->position = $anciennePosition;
    }
  }
  

   // Permet de tester si la position actuelle est valide.

  public function valid()
  {
    return isset($this->tableau[$this->position]);
  }
}

$objet = new MaClasse;

foreach ($objet as $key => $value)
{
  echo $key, ' => ', $value, '<br />';
}

$objet->seek(2);
echo '<br />', $objet->current();
````
### ``ArrayAccess``
Permet de placer les crochets à la suite de l'objet, avec la clé à laquelle accéder. Il y a 4 méthodes:

offsetExists: vérifie l'existence de la clé entre crochets lorsque l'objet est passé à la fonction isset ou empty; offsetGet: on fait $obj['clé], la valeur 'clé' est donc passée à la méthode offsetGet. offsetSet: méthode appelée lorsqu'on assigne une valeur à une entrée. Cette méthode reçoit donc deux arguments, la valeur de la clé et la valeur qu'on veut lui assigner. offsetUnset: appelée lorsqu'on appelle la fonction unset sur l'objet avec la valeur entre crochets. Cette méthode reçoit un argument, la valeur qui est mise entre les crochets.
### ``Countable``
Elle contient une méthode :count Celle-ci doit obligatoirement renvoyer un entier. Elle sert à renvoyer le nombre d'entrées dans notre tableau.


#Méthode et attribut statique

Les méthodes et attributs statiques sont dits de classe. Un attribut statique existe dès que sa classe est chargée, en dehors et indépendamment de toute instanciation. Quelque soit le nombre d’instanciation de la classe, un attribut de classe, existe en un et un seul exemplaire.

Une méthode statique ne doit pas manipuler, directement ou indirectement, d’attributs non statiques de sa classe.

#Pointeur interne

Il peut se révéler indispensable pour un objet de pouvoir se référencer lui-même. Pour cela, toute instance dispose d’un pointeur interne vers elle-même. Ce pointeur peut prendre différentes appellations. En Java, c++, PHP il s’agira du pointeur "this".

#Quelques méthodes magiques utiles

__construct() : Appelée lorsqu’on tente de construire la class

__destruct() : Appelée lorsqu’on tente de détruire la class

__set() : Déclenchée lors de l’accès en écriture à une propriété de l’objet. Exemple d’utilisation

__get() : Déclenchée lors de l’accès en lecture à une propriété de l’objet. Exemple d’utilisation

__call() : Déclenchée lors de l’appel d’une méthode inexistante de la classe (appel non static).

__callstatic() : Déclenchée lors de l’appel d’une méthode inexistante de la classe (appel static) : disponible depuis PHP 5.3 et 6.0

__isset() : Déclenchée si on applique isset() à une propriété de l’objet

__unset() : Déclenchée si on applique unset() à une propriété de l’objet -> différence avec __destruct() ?

__sleep() : Exécutée si la fonction serialize() est appliquée à l’objet. Exemple d’utilisation

__wakeup() : Exécutée si la fonction unserialize() est appliquée à l’objet. Exemple d’utilisation

__toString() : Appelée lorsque l’on essaie d’afficher directement l’objet : echo $object;

__clone() : Appelé lorsque l’on essaie de cloner l’objet. Exemple d’utilisation

#Bonnes pratiques
####<b>L'auto-chargement des classes ``Auto load``</b>
Pour une question d'organisation, il vaut mieux créer un fichier par classe. Par exemple, nommer le fichier Maclasse.php et on place la classe dedans. Ensuite, il suffit d'inclure le fichier:
````
require 'MaClasse.php'; // J'inclus la classe.

$objet = new MaClasse; // Puis, seulement après, je me sers de ma classe.
````
Puis, pour éviter de les inclure une par une, on utilise l'auto-chargement des classes, c'est-à-dire qu'on crée dans le fichier principal (celui où on crée une instance de notre classe) une ou plusieurs fonctions qui charge(nt) le fichier déclarant la classe:
````
function chargerClasse($classe)
{
  require $classe . '.php'; // On inclut la classe correspondante au paramètre passé.
}

//Puis on va utiliser la fonction ``spl_autoload_registeren`` spécifiant en premier paramètre le nom de la fonction à charger

spl_autoload_register('chargerClasse'); // On enregistre la fonction en autoload pour qu'elle soit appelée dès qu'on instanciera une classe non déclarée.

$perso = new Personnage;
````

#Liste de vocabulaire à connaître (non exhaustive)

Classe/class : Une classe est une entité regroupant des variables et des fonctions.<br>Chacune de ces fonctions aura accès aux variables de cette entité.<br>Elle permet de définir la structure d’un objet qui pourra ensuite être utilisé plusieurs fois avec des options différentes, et dupliqué à loisir par le biais de classes filles. Mot clef : class
Instance : Une classe définie et chargée.

Instance : C'est le résultat d'une instanciation.<br>Une instanciation, c'est le fait d'instancier une classe. C'est une classe définie et chargée.<br>Instancier une classe, c'est se servir d'une classe afin qu'elle nous crée un objet. Une instance ( donc un objet) est utilisable concrètement.

Objet : Comme l’indique son nom, la composante principale de la Programmation Orientée Objet est l’objet.<br>Un objet regroupe les données et les moyens de traitement de ces données. Un objet est donc l'instance d’une classe. Elle est définie par le mot clef new.<br>
Un objet rassemble de fait deux éléments :

* Les attributs : ce sont les variables de l’objet : ce sont eux qui ont en charge les données à gérer. Dans la plupart des langages un attribut possède un type quelconque défini au préalable : nombre, caractère, ..., ou même un type objet. variable d’une class. Définie par le mot clef var, const ou rien du tout.

* Les méthodes : les méthodes sont les éléments d’un objet qui servent d’interface entre les données et le programme. Ce sont en fait les procédures ou fonctions destinées à traiter les données.

En somme, Un objet, c'est une instance de la classe pour pouvoir l'utiliser.


Méthode : Fonction d’une class. Définie par le mot clef function.

Surcharge/Override ou polymorphisme Ad hoc : Permet de définir des méthodes avec le même nom et ayant des fonctionnalités similaires (ex : afficher(), supprimer()) dans des classes héritant d’une même classe mais n’ayant pas d’autres liens entres elles. On parle ainsi de surcharge d’une méthode lorsque l’on redéfinie une méthode qui avait déjà été définie dans une classe parente. Ex : fonction trier() qui fonctionnera pour trier des livres ou des CD sans que le programmeur se souci du nom de la méthode.

Attribut ou méthode magique : Attribut ou méthode commençant généralement par deux underscores (__) , étant apparu dans PHP 5, et ayant des fonctionnalités impossible à coder « à la main » comme par exemple le déclenchement d’une méthode lors de l’instanciation d’une classe ou la suppression d’une instance. Ex : __construct, __clone, __toString

Méthode prédéfinie : Méthode déjà définie par PHP. Ex : get_parent_class, class_exists

Héritage/Extend : Notion permettant qu’une classe (dites fille) hérite des attributs et des méthodes d’une autre classe (dites parente). Mot clef : extends

Constructeur/constructor : Méthode permettant de créer un objet en instanciant une classe. Mot Clef : __construct($params)

Interface : Définie une liste de méthodes que doit contenir les classes qui implémentent cette interface. Mot clef : interface

Design pattern Singleton : Singleton garantit qu’une classe n’a qu’une seule instance et fournit un point d’accès global à cette instance.<br>
http://design-patterns.fr/singleton

Le principe d'encapsulation : L'un des gros avantages de la POO est que l'on peut masquer le code à l'utilisateur (l'utilisateur est ici celui qui se servira de la classe, pas celui qui chargera la page depuis son navigateur). Le concepteur de la classe a englobé dans celle-ci un code qui peut être assez complexe et il est donc inutile voire dangereux de laisser l'utilisateur manipuler ces objets sans aucune restriction. Ainsi, il est important d'interdire à l'utilisateur de modifier directement les attributs d'un objet. L'encapsulation garantit ainsi la validité des types et des valeurs des données des objets.<br>
Le principe est exactement le même pour la POO : l'utilisateur de la classe doit se contenter d'invoquer les méthodes en ignorant les attributs. Comme le pilote de l'avion, il n'a pas à les trifouiller. Pour instaurer une telle contrainte, on dit que les attributs sont privés.

Surcharger : Surcharger une methode, remplace le contenu de la fonction initial, par contre si tu appel parent::taMethode dans ta methode, cette appel va rapellez la methode de l'objet parent, donc on peut combiner les deux.

Namespaces : Sert à séparer les constantes, fonctions et classes dans différents espaces afin d'éviter tout conflit : on peut ainsi avoir plusieurs constantes, fonctions ou classes du même nom dans la même application.