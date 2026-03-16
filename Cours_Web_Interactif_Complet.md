# **🎓 Mini-Cours : Crée ton premier site interactif**

Bienvenue dans ce cours d'introduction au développement web. Nous allons construire une application complète en étapes progressives.

L'objectif est de comprendre comment les trois langages du web travaillent ensemble :

1. **HTML** (*HyperText Markup Language*) : Le squelette. Il définit la structure et le contenu de la page (titres, paragraphes, images).
2. **CSS** (*Cascading Style Sheets*) : L'habillage. Il permet de mettre en forme le contenu (couleurs, polices, disposition des éléments).
3. **JavaScript** : Le cerveau. C'est le langage de programmation qui rend la page interactive (réactions aux clics, calculs, animations).

## **🐣 Étape 0 : Le Strict Minimum (La base absolue)**

Avant de construire une page complète, voyons à quoi ressemble le code le plus simple possible. Pour qu'un navigateur comprenne qu'il lit une page web, il a besoin de balises spécifiques.

**Analyse du code :**

* \<\!DOCTYPE html\> : La carte d'identité du fichier (HTML5 moderne).  
* \<html\> : La boîte qui contient tout.  
* \<body\> : Le corps visible de la page.

### **📄 Code de l'Étape 0**
```html
<!DOCTYPE html>
<html>
<body>
    <h1>Hello World !</h1>
    <p>Ceci est ma toute première ligne de code.</p>
</body>
</html>
```

## **🏗️ Étape 1 : Le Squelette Structuré (HTML Sémantique)**

Passons aux choses sérieuses. Nous allons organiser notre page avec des balises qui ont du sens ("sémantiques").

**Les Nouveautés :**

* **Structure** : \<header\> (entête), \<section\> (contenu), \<footer\> (pied de page).  
* **Formulaire** : \<input\> pour écrire, \<button\> pour cliquer.  
* **Identifiants** (id="...") : Ils ne servent à rien pour l'instant, mais ce sont les "noms" que le JavaScript utilisera à l'étape suivante pour attraper les éléments.

### **📄 Code de l'Étape 1**

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Étape 1 : Structure</title>
</head>
<body>
    <!-- En-tête -->
    <header>
        <h1>Hello World !</h1>
        <p>Ceci est ma première page web.</p>
    </header>

    <!-- Zone principale -->
    <section>
        <label>Ton prénom :</label>
        <input type="text" id="monInput" placeholder="Écris ici...">
        
        <button id="monBouton">Clique-moi</button>
        
        <!-- Zone vide pour le résultat -->
        <div id="zoneResultat"></div>
    </section>

    <!-- Pied de page -->
    <footer>
        <p>Fin de la page.</p>
    </footer>
</body>
</html>
```

## **🧠 Étape 2 : L'Intelligence (Ajout du JavaScript)**

Le HTML est statique. Le JavaScript va lui donner vie. Nous allons "écouter" le clic sur le bouton et réagir.

**La logique expliquée :**

1. **Sélection** : document.getElementById permet de trouver nos balises HTML.  
2. **Écoute** : addEventListener attend le clic.  
3. **Condition** : if / else vérifie si l'utilisateur a écrit quelque chose.

### **📄 Code de l'Étape 2**

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Étape 2 : Interaction</title>
</head>
<body>
    <header>
        <h1>Hello World !</h1>
        <p>Maintenant, le bouton fonctionne.</p>
    </header>

    <section>
        <label>Ton prénom :</label>
        <input type="text" id="monInput" placeholder="Écris ici...">
        
        <button id="monBouton">Clique-moi</button>
        
        <div id="zoneResultat"></div>
    </section>

    <footer>
        <p>Fin de la page.</p>
    </footer>

    <!-- JAVASCRIPT -->
    <script>
        // 1. Sélection des éléments
        const leChamp = document.getElementById('monInput');
        const leBouton = document.getElementById('monBouton');
        const laZone = document.getElementById('zoneResultat');

        // 2. Réaction au clic
        leBouton.addEventListener('click', function() {
            const prenom = leChamp.value;

            // 3. Vérification
            if (prenom !== "") {
                laZone.innerHTML = "Bonjour " + prenom + " ! Tu as réussi l'étape 2.";
                laZone.style.color = "green"; // Petit ajout de style via JS
            } else {
                alert("Hé ! Écris ton prénom d'abord !");
            }
        });
    </script>
</body>
</html>
```

## **📁 Étape 3 : L'Organisation Logique (JS Externe)**

Avant de commencer le design, une bonne pratique est de séparer la logique du contenu. Si notre site grandit, le code JavaScript ne doit pas polluer le HTML.

Nous allons donc déplacer notre code JS dans un fichier script.js.

### **📄 Fichier 1 : index.html**

Regardez tout en bas : la balise \<script\> ne contient plus de code, mais un lien src="script.js".

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Étape 3 : JS Externe</title>
</head>
<body>
    <header>
        <h1>Hello World ! 📁</h1>
        <p>Le JS est maintenant dans son propre fichier.</p>
    </header>

    <section>
        <label>Ton prénom :</label>
        <input type="text" id="monInput" placeholder="Écris ici...">
        <button id="monBouton">Clique-moi</button>
        <div id="zoneResultat"></div>
    </section>

    <footer>
        <p>Code propre et organisé.</p>
    </footer>
      
    <!-- C'EST ICI : ON LIE LE FICHIER JS EXTERNE -->
    <script src="script.js"></script>
</body>
</html>
```

### **📄 Fichier 2 : script.js**

Ce fichier ne contient **que** du JavaScript. Pas de balises HTML \<script\>, juste le code pur.

```js
// Fichier : script.js

// 1\. Sélection des éléments  
const leChamp = document.getElementById('monInput');  
const leBouton = document.getElementById('monBouton');  
const laZone = document.getElementById('zoneResultat');

// 2\. Définition de la fonction de réaction  
leBouton.addEventListener('click', function() {  
    const prenom = leChamp.value;  
      
    // 3\. Logique  
    if (prenom.trim() !== "") {  
        laZone.innerHTML = `👋 Enchanté, ${prenom} \!`;  
        laZone.style.color = "\#28a745"; // Vert succès  
        console.log("Succès : prénom affiché");  
    } else {  
        alert("Hé \! Écris ton prénom d'abord \!");  
        console.warn("Erreur : champ vide");  
    }  
});
```

## **🎨 Étape 4 : Le Design Artisanal (CSS Interne)**

Maintenant que le code est bien rangé, occupons-nous du style. Le site est fonctionnel mais brut. Pour cette étape, nous allons écrire du CSS dans l'entête du fichier HTML pour comprendre comment cela fonctionne.

*(Notez que nous gardons notre lien vers script.js en bas de page)*

### **📄 Code de l'Étape 4**

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Étape 4 : CSS Classique</title>
    <!-- CSS ÉCRIT À LA MAIN DANS LE FICHIER HTML -->
    <style>
        /* Style général de la page */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f0f2f5;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        /* La carte blanche au centre */
        .carte {
            background-color: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            width: 350px;
            text-align: center;
        }

        /* Les champs et boutons */
        input {
            width: 80%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            transition: background 0.3s;
        }

        button:hover {
            background-color: #0056b3;
        }

        .resultat-box {
            margin-top: 20px;
            font-weight: bold;
            color: #28a745;
        }
    </style>
</head>
<body>
    <main class="carte">
        <header>
            <h1 style="margin-top:0;">Hello World ! 🎨</h1>
            <p style="color: #666;">Design CSS Interne + JS Externe</p>
        </header>
        <section>
            <label style="display:block; text-align:left; margin-bottom:5px;">Ton prénom :</label>
            <input type="text" id="monInput" placeholder="Écris ici...">
            <button id="monBouton">Lancer le script</button>
            <div id="zoneResultat" class="resultat-box"></div>
        </section>
        <footer style="margin-top: 20px; font-size: 12px; color: #999;">
            <p>CSS Interne</p>
        </footer>
    </main>

    <!-- Lien vers notre script externe créé à l'étape précédente -->
    <script src="script.js"></script>
</body>
</html>
```

## **📁 Étape 5 : L'Organisation Visuelle (CSS Externe)**

Comme pour le JS à l'étape 3, écrire tout le CSS dans le HTML devient vite illisible. La solution professionnelle est de séparer le design dans un fichier style.css.

Nous aurons donc 3 fichiers : index.html, style.css et script.js.

### **📄 Fichier : index.html (Étape 5\)**

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Étape 5 : Tout Séparé</title>
    <!-- LIEN VERS LE FICHIER CSS EXTERNE -->
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <main class="carte">
        <header>
            <h1 style="margin-top:0;">Hello World ! 🧠</h1>
            <p style="color: #666;">Tout est séparé proprement.</p>
        </header>

        <section>
            <label style="display:block; text-align:left; margin-bottom:5px;">Ton prénom :</label>
            <input type="text" id="monInput" placeholder="Écris ici...">
            <button id="monBouton">Lancer le script</button>
            <div id="zoneResultat" class="resultat-box"></div>
        </section>

        <footer style="margin-top: 20px; font-size: 12px; color: #999;">
            <p>HTML + CSS + JS séparés</p>
        </footer>
    </main>
      
    <!-- Lien JS -->
    <script src="script.js"></script>
</body>
</html>
```

### **📄 Fichier : style.css (Étape 5\)**

```css
/* Fichier : style.css */  
body {  
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;  
    background-color: #f0f2f5;  
    display: flex;  
    justify-content: center;  
    align-items: center;  
    height: 100vh;  
    margin: 0;  
}  
.carte {  
    background-color: white;  
    padding: 30px;  
    border-radius: 15px;  
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);  
    width: 350px;  
    text-align: center;  
}  
input {  
    width: 80%;  
    padding: 10px;  
    margin-bottom: 10px;  
    border: 1px solid #ccc;  
    border-radius: 5px;  
}  
button {  
    background-color: #007bff;  
    color: white;  
    border: none;  
    padding: 10px 20px;  
    border-radius: 5px;  
    cursor: pointer;  
    width: 100%;  
    font-size: 16px;  
    transition: background 0.3s;  
}  
button:hover {  
    background-color: #0056b3;  
}  
.resultat-box {  
    margin-top: 20px;  
    font-weight: bold;  
    color: #28a745;  
}
```

## **🚀 Étape 6 : Le Design Rapide (Tailwind CSS)**

Maintenant que vous maîtrisez l'organisation classique, appliquons-la à Tailwind CSS. Nous gardons notre fichier JS externe (script.js), mais nous allons modifier son contenu pour qu'il manipule les classes Tailwind au lieu du style direct.

### **📄 Fichier : index.html (Étape 6\)**

Remarquez que le JS est bien importé via \<script src="script.js"\> à la fin.

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Étape 6 : Tailwind CSS</title>
    <!-- Importation de Tailwind via Internet (CDN) -->
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-100 min-h-screen flex items-center justify-center font-sans">

    <!-- Carte principale -->
    <main class="bg-white p-8 rounded-xl shadow-2xl max-w-md w-full mx-4 border-t-4 border-blue-500">
        
        <header class="mb-6 text-center">
            <h1 class="text-3xl font-bold text-slate-800">Hello World ! 🚀</h1>
            <p class="text-slate-500 mt-2">Design moderne avec Tailwind.</p>
        </header>

        <section class="space-y-4">
            <div>
                <label class="block text-sm font-medium text-slate-700 mb-1">Ton prénom :</label>
                <!-- Input avec focus ring -->
                <input 
                    type="text" 
                    id="monInput" 
                    placeholder="Écris ici..." 
                    class="w-full px-4 py-2 border border-slate-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:outline-none transition"
                >
            </div>

            <!-- Bouton avec effet hover -->
            <button 
                id="monBouton"
                class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-lg transition shadow-md"
            >
                Lancer la magie ✨
            </button>

            <!-- Zone de résultat (cachée par défaut avec 'hidden') -->
            <div 
                id="zoneResultat" 
                class="hidden mt-4 p-4 bg-green-50 border border-green-200 rounded-lg text-green-700 text-center"
            ></div>
        </section>

        <footer class="mt-8 text-center text-xs text-slate-400">
            <p>Bravo, tu as fini le cours complet !</p>
        </footer>
    </main>

    <!-- JS EXTERNE : On pointe toujours vers le fichier séparé -->
    <script src="script.js"></script>
</body>
</html>
```
### **📄 Fichier : script.js (Mis à jour pour Tailwind)**

Pour que Tailwind fonctionne bien (ex: afficher la zone cachée par hidden), nous devons mettre à jour notre fichier JS externe pour qu'il ajoute/enlève des classes utilitaires.

```js
// Fichier : script.js (Version Tailwind)

const leChamp = document.getElementById('monInput');  
const leBouton = document.getElementById('monBouton');  
const laZone = document.getElementById('zoneResultat');

leBouton.addEventListener('click', function() {  
    const prenom = leChamp.value;  
      
    if (prenom.trim() !== "") {  
        // SUCCÈS  
        laZone.innerHTML = `👋 Enchanté, \<strong\>${prenom}\</strong\> \!`;  
          
        // Tailwind : on retire la classe 'hidden' pour afficher  
        laZone.classList.remove('hidden');   
          
        // Bonus : On change le bouton en vert via les classes  
        leBouton.textContent = "C'est fait \! ✅";  
        leBouton.classList.replace('bg-blue-600', 'bg-green-600');  
        leBouton.classList.replace('hover:bg-blue-700', 'hover:bg-green-700');  
    } else {  
        // ERREUR  
        // Tailwind : on ajoute une bordure rouge  
        leChamp.classList.add('border-red-500', 'ring-2', 'ring-red-200');  
          
        // On retire l'erreur après 2 secondes  
        setTimeout(() => {  
            leChamp.classList.remove('border-red-500', 'ring-2', 'ring-red-200');  
        }, 2000);  
    }  
});
```

## **🤖 Étape 7 : L'IA comme Assistant (Prompt Engineering)**

Une fois que vous comprenez le code (HTML, CSS, JS et leur séparation), vous pouvez utiliser l'Intelligence Artificielle pour coder plus vite. Mais attention, l'IA ne devine pas tout : il faut lui donner des instructions précises (un **prompt**).

Voici un "Prompt Expert" pour générer la même application que l'Étape 6, mais en respectant les standards de qualité les plus modernes (2026).

### **📋 Le Prompt à copier-coller**

Tu peux envoyer ce message à ChatGPT, Claude ou Gemini :

```txt
Agis comme un **Développeur Front-End Senior** expert en standards web modernes (2026).

**Objectif :**

Crée une carte interactive simple 'Hello World' qui demande le prénom de l'utilisateur.

**Stack Technique :**

1. **HTML5 Sémantique** (Accessible, balises appropriées).  
2. **Tailwind CSS** (via CDN pour la démo) : Utilise une approche Mobile-First, avec support du Dark Mode natif.  
3. **Vanilla JS (ES6+)** : Code modulaire, pas de var, utilisation de const/let et Arrow Functions. Le JS doit être dans un fichier séparé.

**Fonctionnalités requises :**

* Un champ input et un bouton 'Valider'.  
* Validation des données : Si l'input est vide, affiche une erreur visuelle (bordure rouge \+ message ARIA pour l'accessibilité).  
* Succès : Affiche 'Bonjour \[Prénom\]' avec une animation fluide d'apparition.  
* **Séparation des préoccupations** : Fournis le code en 2 blocs distincts (index.html et script.js).

**Design** (Style 2026\) :

* Minimaliste, coins très arrondis (xl ou 2xl), ombres douces et diffuses.  
* Typographie parfaitement lisible (Inter ou system-ui).  
* Micro-interactions au survol et au focus (transition smooth).

Assure-toi que le code est robuste, commenté en français et prêt à l'emploi.
```

### **💡 Pourquoi ce prompt est efficace ?**

1. **Le Rôle (Persona)** : "Agis comme un Développeur Senior". Cela force l'IA à éviter les solutions débutantes ou obsolètes.  
2. **Standards 2026** : On insiste sur l'accessibilité (ARIA), le Dark Mode et le Mobile-First, qui sont indispensables aujourd'hui.  
3. **Contraintes Techniques** : On précise "Pas de var", "ES6+", "Fichier séparé". Sans ça, l'IA pourrait te donner du vieux code JavaScript ou tout mélanger dans le HTML.  
4. **Détails Design** : En demandant des "ombres douces" et "coins très arrondis", on aide l'IA à créer un design moderne et agréable.
