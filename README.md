# Manuel d’utilisateur grammaires locales étendues

Les grammaires locales étendues (ELG) permettent d’accéder à une fonction définie à l’extérieur d’Unitex. 

## Utilisation
Afin de créer une ELG il suffit de créer une GL avec des variables (d’entrée ou sortie). À la fin de la GL, il faut rajouter une boîte vide dont la description appelle la fonction définie auparavant et qui prend en entrée les variables extraites du texte. Une fois le graphe prêt, il s’utilise avec « Locate Pattern ». Si le mode « Grammar outputs are not taken into account » est sélectionné, la fonction ne sera pas exécutée. En revanche, en mode « Merge with input text » affichera les séquences trouvées suivies par la sortie de la fonction. La troisième option « Replace recognized sequences » affichera seulement la sortie de la fonction et non les séquences trouvées. 
Note : Les ELG peuvent seulement s’utiliser avec « Locate Pattern ». Leur utilisation avec CasSys ou « Explore Graph Path » créera des erreurs. 

## Stockage des fichiers 
Les fichiers des fonctions externes sont stockés à l’extérieur des fichiers des graphes. Le répertoire défini par défaut se trouve dans Unitex-GramLab/App/elg. Cependant, l’interface permet à l’utilisateur de définir un autre répertoire pour stocker les fonctions. Cette fonctionnalité se trouve dans Info > Preferences > Directories. 

![image](https://github.com/user-attachments/assets/b296375c-b6f3-4d60-93b9-bcbdec05a515)

Figure 1: Définir un autre répertoire pour les ELG

Les fonctions externes sont sauvegardées dans des fichiers avec l’extension .upp et elles sont écrites dans le langage de programmation Lua. Pour définir une nouvelle fonction, il faut donc créer un fichier nomDuFichier.upp et définir à l’intérieur une ou plusieurs fonctions. Ensuite, la référence à l’intérieur d’un graphe peut lancer la fonction définie auparavant. 

## Syntaxe 
La syntaxe pour appeler une fonction est la suivante : $@fonction(${variable})$. Les signes dollars indique à Unitex que le texte ne sera pas affiché tel quel mais le contenu stocké dans cette « variable ». Avec le signe @ la fonction est appelée. Ce qui est suit est soit le nom du fichier, si le fichier contient une seule fonction, soit le nom du fichier suivi par le nom de la fonction. Les deux noms sont séparés par un point. Les arguments de la fonction sont donnés entre parenthèses. 

![image](https://github.com/user-attachments/assets/b4e029c0-634d-40f6-9a34-af1159014bac)

Figure 2: Exemple d'utilisation d'une ELG

Il est possible de passer en argument une donnée définie qui sera la même pour chaque appelle à la fonction. De plus, la fonction peut prendre en argument une variable définie auparavant dans le graphe. Pour ce faire, il suffit de suivre la syntaxe de l’exemple : Le signe dollar suivi par le nom de la variable entre accolades. 

![image](https://github.com/user-attachments/assets/35dbd91a-3160-468a-9fb1-7165a26437fa)

Figure 3: Exemple d'une fonction appelé avec le nom du fichier et le nom de la fonction.
