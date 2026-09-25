<p align="center">
  <img src="logo.png" width="112" alt="Pocket Torrent">
</p>

<h1 align="center">Pocket Torrent</h1>

<p align="center">
  Client BitTorrent pour Windows, avec VPN intégré et téléchargements directs.<br>
  <a href="https://github.com/Zyko0w/pocket-torrent-releases/releases/latest"><b>Télécharger la dernière version</b></a>
</p>

---

## Fonctionnalités

**Téléchargement**
- Liens magnet, fichiers `.torrent` (y compris par glisser-déposer) et liens directs HTTP(S) avec reprise.
- Sélection et ordre de priorité des fichiers, avant et pendant le téléchargement.
- File d'attente à trois niveaux de priorité, qui déterminent l'ordre de démarrage et la part de bande passante.
- Limites de vitesse globales et par téléchargement, planificateur horaire.
- Catégories avec dossier dédié ; dossier des téléchargements en cours en option (déplacement à la fin).
- Flux RSS de séries : ajout automatique des nouveaux épisodes, avec filtres simples ou expressions régulières
  (RSS, Atom, Jackett, Prowlarr).
- Trackers privés : trackers de secours utilisés dans l'ordre du `.torrent`.
- Liens magnet copiés proposés à l'ajout au retour sur la fenêtre.
- Partage avec ratio et durée maximum.

**Confidentialité**
- Liaison stricte à l'interface du VPN, avec arrêt immédiat en cas de coupure et reprise automatique.
- Tunnel WireGuard intégré (import du fichier `.conf` du fournisseur), limité aux téléchargements.
- Proxy SOCKS5 : tout le trafic des téléchargements passe par lui, sans fuite.
- Redirection de port ProtonVPN (NAT-PMP).
- Chiffrement des échanges entre pairs (MSE), DNS chiffré (DNS over HTTPS).
- Mode discret et mode confidentialité renforcée.
- Liste de blocage d'IP, détection des fichiers dangereux, analyse Microsoft Defender en option.
- Aucune télémétrie, aucun compte.

**Utilisation**
- Mode jeu : ralentissement ou pause automatique au lancement d'un jeu.
- Arrêt du PC à la fin des téléchargements.
- Démarrage avec Windows, association des liens magnet et `.torrent`, notifications.
- Envoi automatique sur storage.to une fois terminé, avec lien de partage (optionnel, sans compte).
- Graphique du débit en direct (global et par téléchargement), statistiques, état des trackers.
- Export et import de la liste de téléchargements.

**Moteur**
- Basé sur [librqbit](https://github.com/ikatson/rqbit) (Rust), étendu pour Pocket Torrent.
- DHT, PEX, trackers HTTP/UDP, µTP, sources web (BEP 19), extension Fast (BEP 6), partage partiel (BEP 21),
  sélection des pièces les plus rares, réciprocité d'envoi, fin de partie (end-game), priorité des pairs
  (BEP 40), identifiants DHT sécurisés (BEP 42), perçage de NAT (BEP 55).
- Ouverture automatique du port sur le routeur (UPnP, NAT-PMP).

## Nouveautés de la 0.4.0

| Ajouté | Retiré |
| --- | --- |
| Proxy SOCKS5 | Lecture pendant le téléchargement (bouton « Lire ») |
| Dossier des téléchargements en cours | |
| Filtres RSS en expressions régulières | |
| Perçage de NAT (BEP 55), fin de partie, BEP 40 et 42 | |

Sécurité : audit et test d'intrusion complets ; une dizaine de failles corrigées, dont deux sérieuses
(un paquet réseau pouvait arrêter la DHT ; un fichier de réglages abîmé désactivait le VPN obligatoire).

## Correctifs de la 0.2.2

- Plantage de l'application lors de la lecture du presse-papiers (retour sur la fenêtre).
- Fenêtres de console qui s'ouvraient pendant l'analyse Microsoft Defender et l'arrêt programmé du PC.

## Nouveautés de la 0.2.1

| Ajouté | Retiré |
| --- | --- |
| Envoi en ligne sur storage.to | Envoi sur Cloudflare R2 |
| Flux RSS de séries | Création de torrents (« Partager en torrent ») |
| Limite de vitesse par torrent | |
| Proposition des liens magnet copiés | |
| Graphique du débit en direct | |

Retirés dans la 0.2.0 : dossiers surveillés, programmes externes (commandes à l'ajout ou à la fin
d'un téléchargement), import des réglages de la version web.

## Installation

1. Téléchargez `PocketTorrent_<version>_x64-setup.exe` depuis la
   [dernière version](https://github.com/Zyko0w/pocket-torrent-releases/releases/latest).
2. Lancez l'installateur. Aucun droit administrateur n'est requis.
3. Si Windows SmartScreen affiche un avertissement : **Informations complémentaires**, puis **Exécuter quand même**.
   L'installateur n'est pas signé par un certificat Microsoft (Authenticode).

Configuration requise : Windows 10 ou 11, 64 bits.

## Mises à jour

Les nouvelles versions sont proposées au démarrage et ne s'installent qu'après accord. Chaque mise à jour est
signée ; l'application vérifie la signature avant installation et refuse tout fichier modifié.

| Fichier | Rôle |
| --- | --- |
| `PocketTorrent_<version>_x64-setup.exe` | Installateur |
| `PocketTorrent_<version>_x64-setup.exe.sig` | Signature de l'installateur (mises à jour automatiques) |
| `latest.json` | Description de la dernière version (mises à jour automatiques) |

## Connexions réseau

Pocket Torrent n'établit que les connexions suivantes :

- pairs, trackers et nœuds DHT des torrents ;
- serveurs DNS chiffrés (Cloudflare, Quad9, Google) ;
- GitHub, pour la recherche de mises à jour (désactivable) ;
- routeur, pour l'ouverture du port (UPnP, NAT-PMP ; désactivée avec le VPN et en mode renforcé) ;
- serveur VPN, pour la redirection de port (si activée) ;
- proxy SOCKS5 choisi dans les réglages (s'il est activé, tout le trafic des téléchargements passe par lui) ;
- storage.to, pour les téléchargements marqués « Envoyer sur storage.to » ;
- serveurs des flux RSS configurés (par le même chemin réseau que les téléchargements).

## Désinstallation

**Paramètres Windows › Applications › Pocket Torrent › Désinstaller.** Les fichiers téléchargés sont
conservés. Une option de l'assistant permet d'effacer aussi les réglages et la liste de téléchargements.

## Utilisation responsable

Pocket Torrent est un outil de partage de fichiers. Son utilisation doit se limiter aux contenus que vous
êtes autorisé à télécharger et à partager.

---

<sub>Ce dépôt contient uniquement les versions publiées : installateurs signés et fichiers de mise à jour.</sub>
