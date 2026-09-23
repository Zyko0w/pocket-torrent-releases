<p align="center">
  <img src="logo.png" width="112" alt="Logo de Pocket Torrent">
</p>

<h1 align="center">Pocket Torrent</h1>

<p align="center">
  <b>Le client torrent pour Windows qui télécharge vite, discrètement, et reste à sa place quand tu joues.</b><br>
  Torrents, liens magnet et téléchargements directs · VPN intégré · Interface en français
</p>

<p align="center">
  <a href="https://github.com/Zyko0w/pocket-torrent-releases/releases/latest"><b>⬇ Télécharger la dernière version</b></a>
</p>

---

> **Nouveau nom.** Jusqu'à la version 0.1.1, l'application s'appelait **Torrent Cloud**. La mise à jour
> vers Pocket Torrent est automatique : ta liste de téléchargements, tes réglages et tes torrents en
> cours sont conservés, et l'ancienne installation est retirée toute seule.

## Pourquoi Pocket Torrent

- **Simple** : colle un lien, c'est parti. Tout le reste a des réglages par défaut raisonnables.
- **Discret** : chiffrement des échanges, DNS chiffré, VPN avec coupure automatique, aucune télémétrie.
- **Respectueux de ton PC** : le mode jeu libère la connexion dès qu'un jeu se lance, et l'application
  se fait oublier près de l'horloge.
- **Moderne** : moteur écrit en Rust ([librqbit](https://github.com/ikatson/rqbit), amélioré pour
  Pocket Torrent), interface légère, mises à jour signées.

## Fonctionnalités

### Télécharger
- Liens **magnet**, fichiers **.torrent** (glisser-déposer dans la fenêtre accepté) et **liens directs** http(s), avec reprise après coupure.
- **Choix des fichiers** avant et pendant le téléchargement, avec un ordre de priorité par fichier.
- **Lecture pendant le téléchargement** : une vidéo s'ouvre dans ton lecteur (VLC, mpv…) sans attendre la fin.
- **File d'attente** avec priorités (haute, normale, basse), nombre de téléchargements simultanés et « démarrer maintenant ».
- **Catégories** avec leur propre dossier, **dossiers surveillés** (un .torrent déposé est ajouté tout seul).
- **Limites de vitesse**, **planificateur** (autres limites la nuit, par exemple), limite par lien direct.
- **Partage** : ratio et durée maximum, création d'un torrent à partir d'un fichier.

### Rester discret
- **VPN** : tout passe par la carte réseau du VPN, et tout s'arrête s'il se coupe (reprise automatique à son retour).
- **Tunnel WireGuard intégré** : importe le fichier `.conf` de ton fournisseur, seuls les téléchargements l'utilisent.
- **Chiffrement** des échanges avec les pairs (obligatoire ou préféré), **DNS chiffré** (DNS over HTTPS).
- **Mode discret** et **mode confidentialité renforcée** (identité du client masquée, UPnP coupé…).
- **Liste de blocage d'IP**, alerte sur les **fichiers dangereux** (`.exe` caché dans un film…), analyse **Microsoft Defender** en option.
- **Aucune télémétrie**, aucun compte.

### Au quotidien
- **Mode jeu** : quand un jeu de ta liste démarre, les téléchargements ralentissent ou se mettent en pause.
- **Éteindre le PC à la fin** des téléchargements (avec une minute pour annuler).
- Démarrage avec Windows, ouverture des liens magnet depuis le navigateur, notifications, réduction près de l'horloge.
- **Cloudflare R2** (optionnel) : envoi automatique en ligne une fois le téléchargement fini, avec liens de partage.
- **Statistiques** cumulées, export et import de la liste pour **changer de PC**, journal exportable sans données sensibles.

### Sous le capot
- Moteur BitTorrent complet : DHT, PEX, trackers HTTP/UDP, µTP (optionnel), sources web (BEP 19),
  extension Fast (BEP 6), partage partiel (BEP 21), « les plus rares d'abord », réciprocité d'envoi (choking).
- Ouverture automatique du port sur la box (**UPnP** et **NAT-PMP**), refermé à la fermeture.

## Installation

1. Télécharge **`PocketTorrent_<version>_x64-setup.exe`** depuis la
   [dernière version](https://github.com/Zyko0w/pocket-torrent-releases/releases/latest)
   (les versions jusqu'à la 0.1.1 s'appellent `TorrentCloud_…`).
2. Lance-le. Pas besoin de droits administrateur : l'application s'installe pour ton compte.
3. Si Windows affiche « Windows a protégé votre ordinateur », clique sur **Informations complémentaires**
   puis **Exécuter quand même** : l'installeur n'a pas (encore) de certificat de signature Microsoft payant.

**Configuration requise** : Windows 10 ou 11, 64 bits. Le composant WebView2 est déjà présent sur Windows 11
et sur les Windows 10 à jour.

## Mises à jour

Pocket Torrent vérifie au démarrage s'il existe une nouvelle version et te la **propose** dans un bandeau :
rien n'est installé sans ton accord. Chaque version est **signée** : avant d'installer, l'application vérifie
la signature, et refuse un fichier modifié.

Chaque version publiée contient trois fichiers :

| Fichier | À quoi il sert |
| --- | --- |
| `PocketTorrent_<version>_x64-setup.exe` | L'installeur. **C'est le seul dont tu as besoin** pour installer à la main. |
| `PocketTorrent_<version>_x64-setup.exe.sig` | La signature de l'installeur, vérifiée par l'application avant une mise à jour. |
| `latest.json` | La fiche que l'application consulte pour savoir si une nouvelle version existe. |

## Confidentialité

Pocket Torrent n'envoie **aucune donnée d'utilisation**. Les seules connexions qu'il établit de lui-même :

- les pairs, trackers et nœuds DHT de tes torrents (le principe même de BitTorrent) ;
- les serveurs DNS chiffrés (Cloudflare 1.1.1.1, Quad9, Google) pour trouver les adresses ;
- GitHub, au démarrage, pour chercher une mise à jour (désactivable, et coupé en mode confidentialité renforcée) ;
- ta box, pour ouvrir le port (UPnP / NAT-PMP, coupé avec le VPN et en mode renforcé) ;
- Cloudflare R2, seulement si tu l'as configuré.

## Désinstallation

**Paramètres Windows → Applications → Pocket Torrent → Désinstaller.** Tes fichiers téléchargés ne sont
jamais supprimés. Pour effacer aussi la liste et les réglages, coche la case proposée pendant la
désinstallation.

## Bon usage

Pocket Torrent est un outil de partage de fichiers. Utilise-le pour des contenus que tu as le droit de
télécharger et de partager (distributions Linux, logiciels libres, œuvres du domaine public ou sous
licence libre…).

---

<sub>Ce dépôt ne contient que les versions publiées (installeurs signés et fichiers de mise à jour).</sub>
