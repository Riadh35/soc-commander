# SOC Commander v2.0 - Edition Professionnel

Centre de Commandement SOC (Security Operations Center) complet et professionnel pour la supervision de securite reseau.

---

## Table des matieres

- [Apercu](#apercu)
- [Fonctionnalites](#fonctionnalites)
- [Prerequis](#prerequis)
- [Installation](#installation)
- [Utilisation](#utilisation)
- [Modules et Onglets](#modules-et-onglets)
- [Systeme de Licences](#systeme-de-licences)
- [Integration IA (Ollama)](#integration-ia-ollama)
- [Themes](#themes)
- [Internationalisation](#internationalisation)
- [Architecture Technique](#architecture-technique)
- [Dependances](#dependances)
- [Configuration](#configuration)
- [Securite et Protection](#securite-et-protection)
- [Build et Distribution](#build-et-distribution)
- [Auteur](#auteur)

---

## Apercu

SOC Commander v2.0 est une application de bureau Windows concue pour les equipes de securite informatique.
Elle centralise la supervision des systemes, la detection de menaces, l'analyse reseau et la reponse aux incidents dans une interface unique et professionnelle construite avec PyQt6.

**Points forts :**

- 11 modules specialises accessibles par onglets
- Surveillance temps reel (CPU, RAM, disque, reseau)
- Capture et analyse de paquets reseau (Scapy)
- Assistant IA integre via Ollama (LLM local)
- Systeme d'alertes multi-niveaux (Critique, Warning, Info)
- Rapports exportables (HTML, TXT, CSV)
- Interface bilingue (Francais / Anglais)
- 3 themes visuels (SOC Dark, Cyber Blue, Matrix Green)
- Systeme de licence lie au materiel avec anti-tampering
- ~9 300 lignes de code Python

---

## Fonctionnalites

### 1. Tableau de Bord (Dashboard)
- Jauges circulaires animees temps reel (CPU, RAM, Disque)
- Cartes metriques avec barres de progression
- Mini graphiques de tendances (MiniBarChart)
- Metriques systeme, reseau, securite et PRTG
- Rafraichissement automatique configurable

### 2. Gestion des Capteurs
- Ajout, modification, suppression de capteurs
- Seuils d'alerte configurables (warning / critique)
- Etats : Up, Down, Warning, Paused, Unknown
- Filtrage et recherche avances
- Panneau de details par capteur

### 3. Inventaire Equipements
- Scan reseau par plage IP (ping + resolution DNS)
- Rafraichissement ARP rapide
- Detection automatique : IP, MAC, hostname, type d'equipement
- Export CSV de l'inventaire complet
- Recherche et filtrage

### 4. Cartographie Reseau
- Topologie visuelle interactive (QGraphicsView)
- Connexions entre hotes representees graphiquement
- Informations reseau local (IP, masque, passerelle)
- Scan de decouverte avec barre de progression

### 5. Centre de Securite
- Moteur de surveillance temps reel (SecurityLogEngine)
- Detection de connexions suspectes (ports backdoor : 4444, 5555, 6666, 1337, 31337)
- Detection de processus suspects (cmd.exe, powershell.exe, wscript.exe, certutil.exe, etc.)
- Alertes sur seuils systeme (CPU > 90%, RAM > 90%)
- Classification du trafic (WEB, REMOTE, MAIL, DATABASE, INFRASTRUCTURE, etc.)
- Lecture des journaux d'evenements Windows (win32evtlog)
- Filtrage par severite et categorie

### 6. Capture de Paquets
- Capture reseau en direct via Scapy (PCAPCaptureEngine)
- Filtrage par protocole, categorie, adresse IP
- Panneau de details par paquet (headers, payload)
- Statistiques en temps reel (total paquets, octets, repartition protocoles)
- Export CSV et sauvegarde PCAP
- Controles Start / Pause / Resume / Stop

### 7. Gestion des Alertes
- Tableau des alertes avec niveaux de severite (Critique, Warning, Info)
- Recherche et filtrage multi-criteres
- Acquittement individuel ou collectif
- Historique des alertes
- Export CSV
- Panneau de details d'alerte

### 8. Outils Reseau & Administration
- **108 commandes** organisees en categories :
  - **Reseau** : ping, tracert, nslookup, ipconfig, netstat, arp, route, nbtstat, net view
  - **Administration** : net user, net localgroup, wmic, tasklist, taskkill, systeminfo, whoami, schtasks
  - **Pare-feu** : netsh advfirewall (regles, profils, configuration complete)
  - **Console MMC** : 22 outils Windows (Services, Event Viewer, Device Manager, Disk Management, Registry Editor, Group Policy Editor, etc.)
- Terminal integre avec historique de commandes
- Export des resultats

### 9. Assistant IA
- Integration Ollama (LLM local, aucune donnee envoyee sur Internet)
- Modeles supportes : llama2, llama3, llama3.1, mistral, codellama, deepseek-coder-v2:16b
- Streaming de tokens en temps reel
- Injection automatique du contexte SOC (logs securite, connexions, alertes, infos systeme)
- 6 prompts rapides pre-configures pour l'analyse SOC
- Historique de conversation (12 derniers echanges)
- Controle de temperature (0.0 - 2.0)
- Export de conversation en fichier texte

### 10. Rapports & Analyses
- 8 types de rapports :
  - Rapport journalier
  - Rapport securite
  - Rapport capteurs
  - Rapport alertes
  - Rapport reseau
  - Rapport systeme
  - Rapport executif
  - Rapport personnalise
- Selection de periode (Aujourd'hui, 7 jours, 30 jours, Personnalise)
- Apercu HTML integre
- Export TXT, CSV
- Impression directe

### 11. Parametres & Configuration
- Intervalle de surveillance configurable
- Retention des donnees
- Nombre max d'alertes stockees
- Configuration du scan de securite
- URL et temperature Ollama
- Selection de langue (FR / EN)
- Selection de theme (3 themes)
- Aide et documentation integrees
- Informations legales / Disclaimer
### Installation 
Lancer le Fichier MSI : double clic sur ( SOC_Commander_2.0.msi )
l'application s'installe et creer un racourcci sur le Bureau .
### Premier lancement
1. L'application demarre en **mode demo** (7 jours d'essai)
2. Le **fingerprint machine** est affiche dans l'onglet Parametres
3. Copiez le fingerprint et envoyez-le a l'administrateur
4. L'administrateur genere une licence avec `generate_soc_license.py`
5. Collez la cle de licence dans le dialogue d'activation

### Navigation

- Utilisez les **11 onglets** en haut de la fenetre pour naviguer entre les modules
- L'en-tete affiche l'heure en temps reel et les statistiques des capteurs
- Le statut de la licence est affiche dans la barre de titre

---

## Modules et Onglets

| # | Onglet | Icone | Description |
|---|--------|-------|-------------|
| 1 | Tableau de Bord | 📊 | Supervision temps reel avec jauges et metriques |
| 2 | Capteurs | 📡 | Gestion et monitoring des capteurs reseau |
| 3 | Equipements | 🖥️ | Inventaire des equipements et scan reseau |
| 4 | Reseau | 🌐 | Cartographie et topologie reseau |
| 5 | Securite | 🛡️ | Centre de securite et detection de menaces |
| 6 | Capture Paquets | 📡 | Capture et analyse de paquets reseau |
| 7 | Alertes | 🚨 | Gestion centralisee des alertes |
| 8 | Outils | 🛠️ | 108 outils reseau et administration |
| 9 | Assistant IA | 🧠 | Analyse IA via Ollama |
| 10 | Rapports | 📈 | Generation et export de rapports |
| 11 | Parametres | ⚙️ | Configuration, aide et informations legales |

---

## Systeme de Licences

### Types de licence

| Type | Description | Duree |
|------|-------------|-------|
| **FULL** | Licence permanente, liee au materiel | Illimitee |
| **DEMO** | Essai gratuit | 7 jours |
| **EXPIRED** | Licence demo expiree | - |
| **INVALID** | Cle de licence invalide ou corrompue | - |

### Processus d'activation

```
1. Lancement de SOC Commander
        |
2. Generation automatique du fingerprint machine
   (MAC + CPU Serial + BIOS ID + Disk Serial -> SHA-256)
        |
3. L'utilisateur copie le fingerprint
        |
4. L'administrateur genere la licence avec generate_soc_license.py
   (Format : TYPE|FINGERPRINT|TIMESTAMP|CHECKSUM -> XOR + Base64)
        |
5. L'utilisateur colle la cle dans le dialogue d'activation
        |
6. Validation : checksum MD5, correspondance fingerprint
        |
7. Licence activee -> fonctionnalites completes
```

### Fichiers de licence

| Fichier | Role |
|---------|------|
| `machine_fingerprint.txt` | Empreinte materielle unique de la machine |
| `soc_license.lic` | Cle de licence chiffree (XOR + Base64) |
| `.soc_demo_start` | Marqueur chiffre de debut de periode d'essai |

## Integration IA (Ollama)

### Principe

SOC Commander utilise **Ollama** pour fournir un assistant IA local. Aucune donnee n'est envoyee sur Internet : tout le traitement se fait en local sur la machine.

### Installation d'Ollama

1. Telecharger et installer [Ollama](https://ollama.ai/)
2. Telecharger un modele :
   ```bash
   ollama pull llama3.1
   ```
3. Ollama demarre automatiquement sur `http://localhost:11434`

### Modeles supportes

| Modele | Taille | Description |
|--------|--------|-------------|
| llama2 | 7B | Meta LLaMA 2 |
| llama3 | 8B | Meta LLaMA 3 |
| llama3.1 | 8B | Meta LLaMA 3.1 (recommande) |
| mistral | 7B | Mistral AI |
| codellama | 7B | Code LLaMA (specialise code) |
| deepseek-coder-v2:16b | 16B | DeepSeek Coder v2 |

### Fonctionnalites IA

- **Streaming temps reel** : les tokens s'affichent au fur et a mesure de la generation
- **Injection de contexte** : l'IA recoit automatiquement les donnees SOC (logs, alertes, connexions)
- **Prompts rapides** : 6 analyses pre-configurees (connexions suspectes, alertes critiques, remediation, etc.)
- **Controle de temperature** : ajustable de 0.0 (deterministe) a 2.0 (creatif)
- **Export** : sauvegarde de la conversation en fichier texte

---

## Themes

3 themes visuels disponibles, modifiables dans Parametres :

| Theme | Style | Couleurs principales |
|-------|-------|---------------------|
| **SOC Dark** | Sombre professionnel (defaut) | Fond #0a1628, texte cyan #00ccff |
| **Cyber Blue** | Bleu cyberdefense | Fond #0d1b2a, accents bleus vifs |
| **Matrix Green** | Vert style Matrix | Fond #0a0a0a, texte vert #00ff41 |

Le changement de theme s'applique instantanement a toute l'interface.

---

## Internationalisation

L'interface est entierement traduite en **Francais** et **Anglais**.

- Systeme base sur un dictionnaire `TRANSLATIONS` (180+ cles)
- Classe `TranslationManager` avec methode `tr(key)`
- Changement de langue en temps reel dans les parametres
- Couvre tous les modules, boutons, labels, messages et tooltips

+-- Themes CSS/QSS
|   +-- STYLE                        SOC Dark (defaut)
|   +-- STYLE_CYBER_BLUE             Cyber Blue
|   +-- STYLE_MATRIX_GREEN           Matrix Green
|   +-- THEMES                       Dictionnaire nom -> stylesheet
|

## Configuration

### Parametres ajustables (onglet Parametres)

| Parametre | Defaut | Description |
|-----------|--------|-------------|
| Intervalle monitoring | 30 s | Frequence de rafraichissement des metriques |
| Retention donnees | 30 jours | Duree de conservation des donnees |
| Max alertes | 1000 | Nombre maximum d'alertes stockees |
| Scan securite | 10 s | Intervalle du moteur de securite |
| Max logs securite | 500 | Nombre maximum de logs conserves |
| URL Ollama | http://localhost:11434 | Adresse du serveur Ollama |
| Temperature IA | 0.7 | Creativite des reponses (0.0 - 2.0) |

## Securite et Protection

### Anti-tampering (CodeProtection)

### Detection de menaces reseau

**Ports suspects surveilles :**

| Port | Signification |
|------|---------------|
| 4444 | Backdoor (Metasploit par defaut) |
| 5555 | Backdoor potentiel |
| 6666 | Backdoor potentiel |
| 1337 | Backdoor (leet) |
| 31337 | Backdoor (eleet) |

**Processus suspects detectes :**
- `cmd.exe`, `powershell.exe`, `wscript.exe`, `cscript.exe`, `mshta.exe`, `certutil.exe`

### Classification du trafic

| Categorie | Ports |
|-----------|-------|
| WEB | 80, 443, 8080, 8443 |
| REMOTE | 22, 23, 3389, 5900 |
| MAIL | 25, 110, 143, 465, 587, 993, 995 |
| DATABASE | 3306, 5432, 1433, 27017, 6379 |
| DNS/INFRA | 53, 67, 68, 123, 161, 162 |
| FILE-TRANSFER | 20, 21, 69, 445, 139 |

## Auteur

**Riadh Ben Khaled**
- Email : riadh.khaled@gmail.com
- Copyright (c) 2026 SOC Commander v2.0 Edition Professionnel

---

## Licence

Ce logiciel est proprietaire. Toute reproduction, distribution ou modification non autorisee est interdite.
L'utilisation est soumise a l'activation d'une licence valide liee a la machine.

---

*SOC Commander v2.0 -- Edition Professionnel -- 2026*
