# Pour toi — cadeau interactif

Version originale inspirée du principe du Reel : un code à quatre chiffres, trois cadeaux, un bouquet de tulipes, un album et une lettre. Aucun fichier du créateur Instagram n'a été repris.

## Essayer

Ouvrir `index.html` dans Edge, Chrome, Firefox ou Safari. Aucun logiciel à installer, aucun `npm install` à lancer.

Code de démonstration : **8706**. Saisir les chiffres puis cliquer sur le cœur. Le clavier de l'ordinateur fonctionne aussi. Les trois cadeaux s'ouvrent dans n'importe quel ordre. Le bouton Musique lance une petite mélodie originale ; un MP3 peut la remplacer.

## Personnaliser dans VS Code

Ouvrir le dossier et chercher `const CONFIG` dans `index.html` (Ctrl+F). Tout le contenu modifiable est regroupé à cet endroit.

- `recipient` : prénom du destinataire.
- `sender` : signature.
- `pin` : exactement quatre chiffres, conservés entre guillemets, par exemple `"0710"`.
- `pinHint` : indice pour deviner le code.
- `welcome` / `intro` : textes d'accueil.
- `flowerNotes` : les deux messages autour du bouquet.
- `letterGreeting` / `letterParagraphs` : début de la lettre et paragraphes.
- `musicTitle` : titre affiché lorsque la musique joue.
- `musicSrc` : chemin d'un MP3 dont vous pouvez autoriser la diffusion, par exemple `"assets/musique.mp3"`. Laisser vide pour la mélodie intégrée.
- `coverPhotos` : chemins des deux portraits, par exemple `["assets/moi.jpg", "assets/toi.jpg"]`.
- `memories` : autant d'images que souhaité. Modifier `src`, `caption`, `description`. Si `src` reste vide, une illustration décorative est affichée.

Les dix photos fournies sont intégrées dans l’album, sans retouche. Les légendes sont numérotées pour ne pas inventer le contexte des souvenirs. Le destinataire est Rosalie. La lettre est adaptée à l’histoire évoquée dans vos échanges : souvenirs et encouragements pour ses études à l’étranger. Elle peut être modifiée dans CONFIG. Le code actuel est 8706, et la signature est Jason.

Exemple pour une photo :

```js
{ src: "assets/photo-01.jpg", illustration: "sunset", caption: "Le titre de notre souvenir", description: "Une phrase personnelle." }
```

Utiliser des noms de fichiers simples, sans espaces ni accents, et respecter les majuscules. Les fichiers doivent réellement se trouver dans le dossier `assets`. Les URL absolues et les liens de partage Drive ne remplacent pas forcément un fichier image directement accessible.

## Publier sur GitHub Pages depuis le navigateur

1. Sur votre compte GitHub, créer un nouveau dépôt nommé `pour-toi`. Ne pas remplacer un portfolio existant.
2. Ajouter `index.html`, `.nojekyll` et les éventuels fichiers du dossier `assets` à la racine du dépôt. Ne pas envoyer le ZIP lui-même : le décompresser d'abord.
3. Dans le dépôt, ouvrir **Settings → Pages**.
4. Dans **Build and deployment**, choisir **Deploy from a branch**.
5. Choisir la branche **main**, dossier **/(root)**, puis enregistrer.
6. Attendre la fin du déploiement ; GitHub affiche ensuite l'adresse du site dans Pages. Ouvrir cette adresse, tester le code et les cadeaux sur téléphone.

Ces intitulés peuvent évoluer. Le projet est un site statique sans dépendances ni étape de compilation.

## Variante avec le terminal VS Code

Créer d'abord un dépôt GitHub vide, puis ouvrir le terminal dans ce dossier. Remplacer l'URL de la dernière commande par celle du nouveau dépôt si nécessaire.

```bash
git init
git add .
git commit -m "Créer le cadeau interactif Pour toi"
git branch -M main
git remote add origin https://github.com/cerveau-bleu/pour-toi.git
git push -u origin main
```

Configurer ensuite Pages comme expliqué ci-dessus. Si `origin` existe déjà, vérifier `git remote -v` et le dépôt cible avant de changer quoi que ce soit. L'URL du dépôt ci-dessus est une destination proposée, pas un dépôt déjà créé.

Après une modification :

```bash
git add .
git commit -m "Personnaliser le cadeau"
git push
```

## Confidentialité

Le code est un élément de la surprise : il ne chiffre pas la lettre et ne protège pas les photos. Toute personne qui accède aux fichiers du site peut les lire, même sans saisir le code. `noindex` demande aux moteurs de ne pas indexer la page, mais ne contrôle pas son accès. Ne publiez pas de contenu intime ou confidentiel sur cette version statique. Une vraie protection nécessiterait une autre architecture.

## Vérification

Syntaxe JavaScript et parcours fonctionnels vérifiés avec un DOM simulé : codes incomplets/incorrects/corrects, trois cadeaux, album circulaire et fermeture. Les commandes audio ont été vérifiées avec un lecteur simulé. Le rendu visuel, le son réel et le fonctionnement sur téléphone restent à contrôler dans votre navigateur. Vérifier les fichiers personnels après leur ajout.

Documentation GitHub : https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
