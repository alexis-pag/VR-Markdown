# Modification et amélioration de la plateforme DEC

## Installation et configuration de reshade pour DEC

## Tracage de la communication de la plate forme

```
@echo off
set /p appname="Entrez le nom de l'application (sans l'extension .exe): "
netstat -ano | findstr :80 > temp.txt
for /f "tokens=5" %%a in ('type temp.txt') do (
    for /f "tokens=1" %%b in ('tasklist /fi "pid eq %%a" ^| findstr /i %appname%.exe') do (
        if "%%b"=="%appname%.exe" (
            echo Connexion trouvee: PID %%a
        )
    )
)
del temp.txt
```

Ce script demande d’abord le nom de l’application, puis utilise netstat pour lister toutes les connexions sur le port 80 (HTTP), filtre ces connexions pour obtenir les PID correspondants, et utilise tasklist pour trouver l’application correspondant à ces PID. Si une correspondance est trouvée, elle affiche le PID.
Notez que :
Vous devrez peut-être exécuter ce script avec des privilèges d’administrateur pour obtenir toutes les informations nécessaires.
Remplacez :80 par le port spécifique que vous souhaitez surveiller, si nécessaire.
Ce script est un exemple de base et peut nécessiter des ajustements selon vos besoins spécifiques.

### execution etape par etape
Pour exécuter le script étape par étape, suivez ces instructions :
Ouvrez l’invite de commande en faisant un clic droit sur le menu Démarrer et en sélectionnant “Invite de commandes (admin)” ou “Windows PowerShell (admin)”.
Tapez chaque commande du script une par une, en appuyant sur Entrée après chaque ligne pour l’exécuter. Voici les commandes décomposées :
set /p appname="Entrez le nom de l'application (sans l'extension .exe): "

Cette commande vous demandera de saisir le nom de l’application.
netstat -ano | findstr :80 > temp.txt

netstat -ano liste toutes les connexions et écoutes actives ainsi que les ports TCP et UDP ouverts, et findstr :80 filtre les résultats pour le port 80, redirigeant la sortie vers temp.txt.
for /f "tokens=5" %%a in ('type temp.txt') do (

Cette boucle lit temp.txt et extrait le cinquième élément de chaque ligne, qui correspond au PID.
for /f "tokens=1" %%b in ('tasklist /fi "pid eq %%a" ^| findstr /i %appname%.exe') do (

Cette commande utilise tasklist pour lister les tâches qui correspondent au PID trouvé, puis findstr pour filtrer par le nom de l’application.
if "%%b"=="%appname%.exe" (
    echo Connexion trouvee: PID %%a
)

Si le nom de l’application correspond, cette commande affiche le PID de la connexion trouvée.
Après avoir entré chaque commande, observez les résultats dans l’invite de commande pour vérifier que chaque étape fonctionne comme prévu.
Si vous rencontrez des erreurs lors de l’exécution des commandes, notez le message d’erreur et le moment où il se produit, cela aidera à diagnostiquer le problème. N’oubliez pas de remplacer :80 par le port que vous souhaitez surveiller si nécessaire.
