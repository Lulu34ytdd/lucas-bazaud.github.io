# Portfolio — Lucas Bazaud

Portfolio personnel multi-pages, statique, responsive, prêt à être publié gratuitement sur **GitHub Pages**.

Aucun backend, aucune base de données, aucun PHP : uniquement HTML, CSS et JavaScript vanilla.

## 📁 Structure

```
portfolio/
├── index.html          → Accueil
├── about.html           → À propos
├── projects.html        → Galerie de projets (filtres + recherche)
├── experience.html      → Parcours / timeline
├── skills.html           → Compétences
├── contact.html          → Contact (mailto)
├── css/
│   ├── style.css         → Design tokens, base, composants
│   ├── responsive.css    → Breakpoints, menu mobile
│   └── animations.css    → Animations, prefers-reduced-motion
├── js/
│   ├── main.js            → Thème sombre/clair, menu mobile, scroll reveal
│   ├── projects.js        → Données des projets + filtres/recherche
│   └── contact.js         → Formulaire de contact (mailto) + copie e-mail
└── assets/                → Images, icônes, documents (CV, etc.)
```

## 🚀 Publier sur GitHub Pages

1. Crée un dépôt sur GitHub (par ex. `portfolio`), public.
2. Depuis le dossier `portfolio/` en local :
   ```bash
   git init
   git add .
   git commit -m "Premier déploiement du portfolio"
   git branch -M main
   git remote add origin https://github.com/<ton-pseudo>/<nom-du-depot>.git
   git push -u origin main
   ```
3. Sur GitHub : **Settings → Pages**.
4. Dans **Source**, choisis la branche `main` et le dossier `/ (root)`.
5. Clique sur **Save**. Le site sera publié en quelques minutes à l'adresse :
   `https://<ton-pseudo>.github.io/<nom-du-depot>/`

### Nom de domaine personnalisé (plus tard)

1. Ajoute un fichier `CNAME` à la racine du projet contenant ton domaine (ex. `lucasbazaud.dev`).
2. Chez ton registrar, ajoute un enregistrement `CNAME` pointant vers `<ton-pseudo>.github.io`.
3. Dans **Settings → Pages**, renseigne le domaine personnalisé et active *Enforce HTTPS*.

## ✏️ Où modifier tes informations

| Élément | Fichier(s) |
|---|---|
| Nom affiché, textes de présentation | `index.html`, `about.html` |
| Adresse e-mail | `contact.html`, `js/contact.js` (constante `EMAIL`), pieds de page de toutes les pages |
| Parcours / stages | `experience.html` |
| Compétences et niveaux | `skills.html` |
| Ajouter un projet | `js/projects.js` → tableau `PROJECTS` (voir ci-dessous) |
| Couleurs / thème | `css/style.css` → bloc `:root` (variables `--accent`, `--bg`, etc.) et bloc `[data-theme="light"]` |
| Titre, description, favicon (SEO) | balises `<title>`, `<meta name="description">` et `<link rel="icon">` en haut de chaque page |

## ➕ Ajouter un projet

Dans `js/projects.js`, ajoute un objet au tableau `PROJECTS` :

```js
{
  title: "Nom du projet",
  category: "Web", // Web, Serveurs, Systèmes, Minecraft, FiveM, Roblox, Python, Autres
  description: "Description courte du projet.",
  technologies: ["HTML", "CSS"],
  githubUrl: "",     // laisse vide si pas de lien
  demoUrl: "",       // laisse vide si pas de lien
  date: "2026",
  status: "active",  // active, paused, archived
}
```

Le projet apparaît automatiquement dans la galerie, avec filtre par catégorie et recherche.

## 🌙 Mode sombre / clair

Le choix du visiteur est mémorisé dans `localStorage` (clé `lb-portfolio-theme`). Aucune donnée n'est envoyée où que ce soit.

## 📩 Formulaire de contact

Le site étant statique, le formulaire de contact construit un lien `mailto:` avec les champs remplis et ouvre le client mail du visiteur — il n'y a pas d'envoi automatique côté serveur. C'est la solution la plus fiable et gratuite pour un site hébergé sur GitHub Pages, sans dépendre d'un service tiers.

Si tu veux un vrai envoi sans passer par le client mail du visiteur, des services gratuits comme [Formspree](https://formspree.io) ou [Web3Forms](https://web3forms.com) existent, mais ont des limites de volume sur leur offre gratuite — ce n'est volontairement pas inclus ici pour rester 100% autonome.

## ♿ Accessibilité

- Navigation au clavier et focus visible partout.
- Lien d'évitement (« Aller au contenu »).
- `prefers-reduced-motion` respecté.
- Contrastes vérifiés en mode sombre et clair.
