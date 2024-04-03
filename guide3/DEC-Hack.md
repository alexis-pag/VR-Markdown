# Modification et amélioration de la plateforme DEC

## Installation et configuration de reshade pour DEC

## Tracage de la communocation de la plate forme

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

