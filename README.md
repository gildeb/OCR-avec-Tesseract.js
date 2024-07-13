Reconnaissance des caractères à l'aide du module javascript Tesseract, dans les images du flux vidéo envoyé par l'ESP32-cam vers le terminal (PC, smartphone).


https://github.com/user-attachments/assets/5703b561-69f8-49c5-beba-7b22765f1160



https://github.com/user-attachments/assets/20fa7589-f346-4a5a-ad28-5c4617dbf2f1


# Installation

- charger le firmware micropython (_micropython_camera_feeeb5ea3_esp32_idf4_4.bin_) sur l'ESP32-cam
- charger les fichiers python et le fichier html dans le système de fichier de l'ESP32-cam
- dans le fichier _WifiConnect.py_, mettre à jour les identifiants de connexion ('myssid' et 'mypwd'),

# Utilisation

Connecter l'ESP32-cam au PC et lancer WifiConnect dans le shell Thonny pour afficher l'adresse IP  de l'ESP32-cam :

```
>>> from WifiConnect import WifiConnect
>>> WifiConnect()
```

A la fin du fichier _main.py_ , ajouter la ligne : ```from ws_tesseract import *```

Déconnecter l'ESP32-cam du PC, et le remettre sous tension

Dans le navigateur du terminal (PC ou smartphone), ouvrir une page à l'adresse IP de l'ESP32-cam. Le flux vidéo doit s'afficher dans la fenêtre vidéo. Les caractères reconnus par Tesseract dans les images sont affichés en dessous de cette fenêtre

# Remarques

On peut restreindre la liste des caractères possibles en utilisant la variable javascript _tessedit_char_whitelist_ (voir le fichier _tesseract.html_). 

La résolution des images est limitée à 160 x 120 pixels et la fréquence à 10 images/s.
Ces deux paramètres sont modifiables, mais une résolution ou une fréquence plus élevées risquent de bloquer l'ESP32-cam.

L'envoi des images utilise un websocket. Il est possible d'envoyer des informations du terminal vers l'ESP32-cam (fonction _notify_), mais la fonctionnalité n'est pas utilisée.
