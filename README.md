- Création de votre projet
- Installer webpack
- Faire un **npm install**
- Installer TailwindCss **npm install -D tailwindcss postcss-loader purgecss-webpack-plugin glob-all path autoprefixer**
- Installer Postcss Import **npm install -D postcss-import**
- Installer Postcss.config.js & Tailwind.config.js **npx tailwindcss init -p**
- Dans le Postcss rajouter :

```js
let tailwindcss = require('tailwindcss')

module.exports = {
    plugins: [
        tailwindcss('./tailwind.config.js'),
        require('postcss-import'),
        require('autoprefixer')
    ],
};
```

- Dans le Tailwind rajouter :

```js
module.exports = {
  content: ["./templates/**/*.{html,twig}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

- MODIModifier le Webpack.config.js :

```JS
 .enablePostCssLoader((options) => {
        options.postcssOptions = {
            // the directory where the postcss.config.js file is stored
            config: './postcss.config.js'
        };
    })
```

- Décommentaiter les balise dans base.html.twig
- Ajouter dans le **asset/style/app.css**

```CSS
@tailwind base;
@tailwind components;
@tailwind utilities;
```

- Lancer **npx tailwindcss -i assets/styles/app.css -o public/build/app.css --watch**
- Lancer le server symfony : **symfony serve -d**
- Pour la mise en prod faire un **npm run build**

