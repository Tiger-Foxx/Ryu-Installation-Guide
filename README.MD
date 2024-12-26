# Guide d'installation de Ryu (avec Fox 🦊 Style !)

Bienvenue dans ce guide d'installation de Ryu ! Si tu cherches à installer ce framework pour ton projet SDN et que tu veux le faire dans un style "renard" (un peu excentrique, mais efficace), tu es au bon endroit ! Attention, cet itinéraire n'est pas pour les âmes sensibles, mais si tu suis chaque étape, tu finiras par dompter Ryu avec la grâce d'un renard 🦊.

## Pré-requis : Installe Python 3.9 (ou ... 3.8 mais pas plus recent !! )

### Étape 1 : Vérifier ta version de Python 🐍

Ryu exige une version de Python 3.8 ou 3.9. Si tu as une version plus ancienne, tu vas devoir la mettre à jour. Pas de panique, je vais te guider. **D'abord, vérifie ta version de Python** avec :

```bash
python3 --version
```

Si tu vois quelque chose comme `Python 3.6.x` ou plus bas, c'est le moment de rétrograder (ou mettre à jour) Python. Si tu as Python 3.9, tu peux passer à l'étape suivante. Sinon, voici comment installer Python 3.9 !

---

### Étape 2 : Installer Python 3.9 avec `wget`

Voici le plan : installer Python 3.9 à partir de la source, et ça commence par télécharger les sources avec `wget`. **Sur Kali/Ubuntu**, tu peux procéder ainsi :

1. **Télécharge les sources de Python 3.9** :
   
   ```bash
   wget https://www.python.org/ftp/python/3.9.0/Python-3.9.0.tgz
   ```

2. **Extraire les fichiers** :
   
   ```bash
   tar -xvf Python-3.9.0.tgz
   ```

3. **Naviguer dans le dossier extrait** :
   
   ```bash
   cd Python-3.9.0
   ```

4. **Configurer Python et compiler** :
   
   ```bash
   ./configure --enable-optimizations
   ```

5. **Construire Python (sans `make altinstall` pour éviter les conflits)** :
   
   ```bash
   sudo make altinstall
   ```

   Ça peut prendre un petit moment, alors prends une pause (et pourquoi pas un café ?).

---

### Étape 3 : Mettre Python 3.9 comme alias

Une fois Python 3.9 installé, il est temps de faire en sorte que ton terminal utilise cette version par défaut. **Crée un alias pour Python** :

```bash
sudo update-alternatives --install /usr/bin/python3 python3 /usr/local/bin/python3.9 1
```

OU SI TU NE VEUT PAS QUE CE SOIT DINITIFF :
```bash
sudo alias python3=python3.9 heheheh
```

Pour vérifier que tout fonctionne correctement :

```bash
python3 --version
```

Tu devrais maintenant voir `Python 3.9.x`. C'est bon, tu es prêt à attaquer la suite !

---

## Étape 4 : Créer un environnement virtuel

Pas question d'installer Ryu et ses dépendances directement dans le système. Non, non, non. On va tout mettre dans un environnement virtuel (comme un renard dans sa tanière).

1. **Installe `venv`** si ce n'est pas déjà fait :

   ```bash
   sudo apt install python3.9-venv
   ```

2. **Créer l'environnement virtuel** (appelle-le `ryuenv` par exemple) :

   ```bash
   python3 -m venv ryuenv
   ```

3. **Active ton environnement virtuel** :

   ```bash
   source ryuenv/bin/activate
   ```

   Tu devrais maintenant voir `(ryuenv)` avant ton prompt de terminal, ce qui signifie que l'environnement est activé. Bravo, tu avances bien !

---

## Étape 5 : Installation de Ryu

Maintenant que ton environnement virtuel est prêt, c'est le moment d'installer **Ryu**.

1. **Installe Ryu avec `pip`** :

   ```bash
   pip install ryu
   ```

   Ça devrait se faire sans problème, mais si tu rencontres une erreur, tu peux essayer de mettre à jour `pip` avant :

   ```bash
   pip install --upgrade pip
   ```

2. **Vérifie que Ryu est bien installé** :

   ```bash
   ryu-manager --version
   ```

   Tu devrais voir la version de Ryu qui s'affiche. Si c'est le cas, tu es prêt à commencer à utiliser Ryu. Si une erreur survient, passe à l'étape suivante.

---

## Étape 6 : Installation de `eventlet` (version 0.30.2)

**Attention** : L'installation de `eventlet` peut poser des problèmes, notamment avec les versions récentes. Nous allons donc installer une version spécifique (0.30.2) qui est compatible avec Ryu.

1. **Désinstalle toute version précédente de `eventlet`** :

   ```bash
   pip uninstall eventlet
   ```

2. **Installe `eventlet` version 0.30.2** :

   ```bash
   pip install eventlet==0.30.2
   ```

   Si tu rencontres des erreurs, assure-toi d'avoir les dépendances nécessaires pour compiler `eventlet`. Par exemple, sur Ubuntu/Kali, tu pourrais avoir besoin de :

   ```bash
   sudo apt-get install build-essential
   ```

---

## Étape 7 : Ryu Manager

Si tout s'est bien passé jusqu'ici, tu devrais pouvoir lancer **Ryu Manager** sans problème. Pour tester, exécute la commande suivante :

```bash
ryu-manager
```

Si tout fonctionne, tu es officiellement prêt à commencer à utiliser Ryu. 🦊

---

## Solutions aux problèmes fréquents

### **Problème : `AttributeError` avec `eventlet`**

Si tu rencontres une erreur liée à `eventlet` (comme des problèmes de compatibilité), essaie d'installer une version plus ancienne, par exemple :

```bash
pip install eventlet==0.30.2
```

### **Problème : `python3` n'est pas trouvé après installation**

Si tu as installé Python 3.9 et que le terminal ne le reconnaît pas, assure-toi d'avoir bien mis à jour les alternatives avec la commande :

```bash
sudo update-alternatives --install /usr/bin/python3 python3 /usr/local/bin/python3.9 1
```

---

## Conclusion
Ah ! et une derniere chose !!!!!! a chaque fois que tu voudrais utiliser ryu , tu devras activer l'environnement virtuel heheh !
Si tu suis ce guide à la lettre, tu devrais avoir un environnement **Ryu** fonctionnel et stable. Tu peux maintenant commencer à explorer ce framework et construire des solutions SDN (Software-Defined Networking) qui déchirent. 🦊

Et n'oublie pas, si ça marche, c'est grâce à toi (et à moi aussi, bien sûr). Allez, au boulot, et que le code soit avec toi !


