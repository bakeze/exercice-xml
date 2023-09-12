# XML : TP 1

## _Premiers documents XML_
# 1. XML
1. Mise en place de l’environnement de travail.
On peut utiliser plusieurs éditeurs pour faciliter le traitement et l’analyse de documents XML. Dans ce TP, on utilise VSCode et son extension XML par RedHat. Lancez donc VSCode et installezl’extension ci-dessous :


2. Créez un nouveau dossier dans votre espace de travail et ouvrez-le sous Visual Studio Code. Créez un nouveau document que vous appellerez enseignants.xml et placez-y le contenu cidessous :

```sh
<enseignants>
<enseignant dep="ISIS">
<nom> Singer </nom>
<prenom> Nicolas </prenom>
</enseignant>
<enseignant dep=ISIS>
<nom> Trouilhet </Nom>
<prenom> Sylvie </prenom>
<age> 38 <age>
</enseignant>
</enseignant>
```
_Ce document n’est pas bien formé. Corrigez toutes ses erreurs._

# 2. DTD
1. Ajoutez au début du fichier xml, la DTD suivante:

```sh
<!DOCTYPE enseignants [
<!ELEMENT enseignants ( enseignant ) >
<!ELEMENT enseignant ( nom, prenom, age) >
<!ELEMENT nom (#PCDATA) >
<!ELEMENT prenom (#PCDATA) >
<!ELEMENT age (#PCDATA) >
<!ATTLIST enseignant dep CDATA #REQUIRED>
]>
```

Vérifiez que le document XML n’est pas valide par rapport à cette DTD. Corrigez la DTD pour que ce soit le cas.

2. Modifiez la DTD pour autoriser un deuxième prénom optionnel pour chaque enseignant. Ajoutez également un attribut optionnel du nom de `annee` sur l'élément `enseignants` qui permet éventuellement de préciser l'année concernée par la liste. En parallèle modifiez le fichier xml pour rajouter ces informations et vérifiez que le document XML reste valide par rapport à sa DTD.

3. Transformez la DTD locale en DTD externe. Pour cela, créez un nouveau chier de type DTD que vous appellerez `enseignants.dtd` . Copiez dans ce nouveau fichier, le contenu de votre DTD locale (uniquement la liste des éléments et des attributs) et sauvez-le. Remplacez ensuite la DTD locale du chier XML par la ligne : 
 `<!DOCTYPE enseignants SYSTEM "enseignants.dtd">`
 Vérifiez que le lien entre le XML et sa DTD continue de fonctionner (par exemple en ajoutant des nouvelles balises dans le XML et en vérifiant que la DTD les détecte bien en erreur)

4. Ajoutez une définition d’entité dans la DTD comme suit :
`<!ENTITY isis "ISIS">` Utilisez cette entité dans le document XML à la place de chaque occurence de la chaine de caractère ISIS. Vérifiez que le document reste valide.

# 3. Comparaison avec JSON
1. JSON est aussi un format très utilisé dans l’échange d’informations entre applications informatiques Comparons la même information exprimée en JSON. Pour cela vous pouvez utiliser ce convertisseur en ligne : https://jsonformatter.org/xml-to-json 
Vérifiez que les listes de balises en XML deviennent des tableaux en JSON (notation `[]` ) et que les balises structurées deviennent des objets (notation `{}` ). Vous pouvez également voir que les attributs et les balises terminales sont traitées de la même façon et deviennent des associations clé-valeur (notation `"clé" : "valeur"`).

# 4. Filmographie
Nous voulons réaliser un document XML qui stocke une liste de films. Le descriptif typique d'un film est le suivant (vous pouvez trouver des exemples sur www.cinefil.com ou sur www.allocine.fr ) :

# _King kong_
- Américain - 2005 - 3h08 - Visa : 114089
- Film d'aventures de Peter Jackson
- avec Peter Jackson, Naomi Watts, Jack Black, Adrien Brody
- New York, 1933. Artiste de music-hall à la rue, Ann Darrow rencontre l'audacieux
explorateur/réalisateur Carl Denham. Ce dernier rêve de terminer son lm inachevé, mais nourrit surtout la folle ambition d'être le premier à découvrir le secret de la mystérieuse Skull Island. Il va entraîner Ann dans sa périlleuse aventure...
- Sortie en salle le mercredi 14 décembre 2005
- Ce film est programmé dans 547 salles
- 2 838 759 entrées depuis sa sortie

1. Concevoir l'organisation d'un document XML qui permet de représenter une liste de films. Cette information devra reprendre tous les renseignements donnés ci-dessus en respectant les contraintes suivante :
   - Le document doit avoir pour racine un élément films qui contiendra plusieurs éléments `films` décrivant chacun un `film`.
   - L'information sur l’année de sortie (sur 4 chiffres) et sur le numéro de Visa devra figurer en attribut de l'élément film.
   - Le titre du film devra figurer dans un élément `titre`.
   - Les informations sur la date de sortie en salle, le nombre d'entrées et le nombre de salles devront être des sous-éléments d'un élément appelé `exploitation`.
   - La date de sortie en salle n'a pas besoin d'être décomposée mais doit faire figurer le jour de la semaine (exemple : `mercredi 7 mars 2022`).
   - Il doit y avoir un élément acteur par acteur du film et ces éléments doivent être contenus dans un élément acteurs Pour simplifier, on ne prévoira qu’un seul réalisateur qui doit être placé dans un élément `realisateur`.
   - Le film peut être rattaché à plusieurs genres comme par exemple aventure, action, comédie,etc.
   - La durée du film doit être donnée en minutes.
   - Le descriptif du scénario doit être placé dans une section littérale ( `<![CDATA[ ]]>`) à l’intérieur d'un élément scénario .
   - Vous ajouterez dans l'élément exploitation un élément listepays qui listera une liste de noms de pays européens (pas plus de 3) dans lesquels le film est sorti (en plus de la France). Le nom du pays devra figurer dans un élément pays .
   
2. Créez un document XML spécifiant un film au moyen de la structure définie. Vérifiez que le document produit est bien formé et appelez le `filmographie.xml`.

3. Faites vérifier la structure par l’enseignant avant de passer à la question suivante.
4. Réalisez le DTD correspondant à votre document XML. Appelez-la filmographie.dtd .
5. Vérifiez que votre document XML est bien valide vis-à-vis de la DTD.
6. Complétez votre cinématographie pour avoir 4 films au total.


> Auteur : M. Nicolas Singer 
> Reprise : Bakayoko Marc Ezechiel 
