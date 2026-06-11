# renpic.sh

Script Bash de renommage automatique d'images JPG à partir de leurs métadonnées EXIF.

## Description

`renpic.sh` parcourt un répertoire donné et renomme chaque fichier `.jpg` en utilisant la date de prise de vue extraite des données EXIF de l'image.

**Exemple :** `CIMG0921.jpg` → `2012-08-20_10-26-57_Bretagne.jpg`

---

## Prérequis

Le paquet `exif` doit être installé sur le système :

```bash
sudo apt install exif
```

---

## Utilisation

```bash
./renpic.sh [-h] [-s suffixe] -d répertoire
```

### Options

| Option | Description |
|--------|-------------|
| `-d répertoire` | **(Obligatoire)** Répertoire contenant les images à renommer |
| `-s suffixe` | Texte ajouté après la date, avant l'extension (ex : `_Bretagne`) |
| `-h` | Affiche l'aide |

---

## Exemples

**Renommage simple :**
```bash
./renpic.sh -d ./Images
# CIMG0921.jpg → 2012-08-20_10-26-57.jpg
```

**Avec suffixe :**
```bash
./renpic.sh -s _Bretagne -d ./Images
# CIMG0921.jpg → 2012-08-20_10-26-57_Bretagne.jpg
```

**Afficher l'aide :**
```bash
./renpic.sh -h
```

---

## Comportement

- Les fichiers sans données EXIF sont **ignorés** (avertissement affiché).
- Si le répertoire spécifié n'existe pas, le script s'arrête avec un message d'erreur.
- L'option `-d` est obligatoire.

---

## Format de renommage

La date est extraite du tag EXIF `DateTimeOriginal` et formatée ainsi :

```
AAAA-MM-JJ_HH-MM-SS[suffixe].jpg
```

---

## Auteur

Script réalisé dans le cadre du cours **Bash – INFO B1** (Ynov Campus).
