# ReefDose — Roadmap

**[English](#english) | [Français](#français)**

---

## English

### Current status : v0.9.8 — Pre-release testing

The project is actively tested on a real reef aquarium.
Core dosing features are functional and validated. The goal of v1.0.0 is to confirm 48h stability before the first public stable release.

---

### ✅ Already available (v0.9.8)

- Automatic dosing — 4 pumps, configurable time window per pump
- Full day mode — clock-aligned dosing (e.g. 24 doses → every hour at :00)
- Compatibility matrix — minimum delay between each pump pair, offsets calculated automatically
- Manual dose — triggerable at any time from the dashboard
- Cycle reset option — manual dose can optionally shift the auto schedule
- Real-time validation — warning when configuration is inconsistent
- Calibration — real flow rate measurement (ml/s)
- Tank management — volume, %, days remaining, low level alert
- Statistics — weekly / monthly / yearly / total volumes, successful and missed doses
- 7-day tank level graph
- Push notifications — pump offline, low tank, missed dose
- Simulation mode — test timing and sequencing without affecting real data
- Automatic automation reload after simulation ends
- Global pause
- Full reset with confirmation
- Desktop + mobile dashboard (FR / EN)
- Free pump names and colors

---

### 🔜 v1.0.0 — First stable release

- Complete real-world validation (48h continuous run) ✅ in progress
- Fix : overdosing when changing pump mode mid-day
- Final documentation and GitHub release

---

### 🔜 v1.1.0 — Safety first

- **Hardware safety timeout** — ESP32 cuts the pump automatically after a configurable max duration, preventing flooding in case of HA crash or automation failure
- **HA watchdog (soft + hard)** — soft level : pump OFF + warning notification / hard level : all pumps OFF + urgent notification
- **Physical manual dose button** — a hardware button on the ESP32 triggers a manual dose exactly like the dashboard button, with HA confirmation and stats update. Works even if the dashboard is unreachable.

---

### 🔜 v1.2.0 — Precision and coherence

- **Recalculate remaining doses on config change** — when a pump's schedule is changed mid-day, the system currently ignores doses already delivered and creates a full new plan, causing overdosing. Fix : read daily counter and spread only remaining doses across the remaining window.
- **Sub-second dose precision** — dose durations currently rounded to whole seconds. Fix : float durations (0.1s resolution) for 10× better precision on small doses.
- **Volume coherence** — prevent setting remaining volume or alert threshold above tank capacity. Fix : dynamically cap `input_number` max when tank volume changes.

---

### 🔜 v1.3.0 — User experience

- **Responsive single-file dashboard** — desktop + mobile merged into one adaptive file
- **Interactive setup tutorial** — 7-step guided onboarding (notifications, calibration, safety, dosing config, compatibility, simulation, production)

---

### 🔮 Future versions

#### Emergency Bluetooth mode
When WiFi is unavailable, the ESP32 can be controlled via Bluetooth as an emergency fallback.
Minimal interface : trigger a manual dose per pump. No stats, no schedule — just keep the tank alive.

#### ESP32 offline fallback
When Home Assistant is unreachable, the ESP32 continues dosing independently using a local schedule stored in ESPHome. Statistics are synchronized when HA reconnects.
Requires an external RTC module for accurate timekeeping without WiFi.

#### Modular pump expansion
Support for more than 4 pumps via additional ESP32 modules (`reefdose_2`, `reefdose_3`...).
All modules managed from a single dashboard.

#### Per-pump color customization
Choose pump colors directly from the dashboard, without editing theme files.

#### Event-based dosing (lights integration)
Trigger doses relative to lighting events (after lights on / after lights off + configurable delay).
Requires a separate lighting automation project.

#### Magnetic stirrer support
Dedicated ESP32 module for stirring each reservoir before dosing.

---

### 💡 Ideas under consideration

- Dose confirmation via push notification
- Weekly dose summary push report (every Monday)
- Holiday / pause mode (suspend dosing for X days)
- Multi-system support (2 independent dosing setups on the same HA instance)
- Dose history export (CSV)
- Advanced statistics (missed dose rate %, real vs configured volume comparison)

---

### Not planned

- Cloud connectivity — ReefDose is and will remain fully local
- Mobile app — the HA mobile app covers notifications
- Support for more than 4 pumps on a single ESP32 — hardware limitation

---

## Français

### État actuel : v0.9.8 — Tests pré-release

Le projet est testé activement sur un aquarium récifal réel.
Les fonctionnalités de dosage sont opérationnelles et validées. L'objectif de la v1.0.0 est de confirmer la stabilité sur 48h avant la première release publique stable.

---

### ✅ Déjà disponible (v0.9.8)

- Dosage automatique — 4 pompes, fenêtre horaire configurable par pompe
- Mode jour entier — dosage aligné sur l'horloge (ex : 24 doses → toutes les heures à :00)
- Matrice de compatibilité — délai minimum entre chaque paire de pompes, offsets calculés automatiquement
- Dose manuelle — déclenchable à tout moment depuis le dashboard
- Option reset de cycle — une dose manuelle peut décaler le planning automatique
- Validation en temps réel — alerte si la configuration est incohérente
- Calibration — mesure du débit réel (ml/s)
- Gestion des réservoirs — volume, %, jours restants, alerte seuil bas
- Statistiques — volumes semaine / mois / année / total, doses réussies et manquées
- Graphique historique 7 jours des niveaux réservoirs
- Notifications push — pompe hors ligne, réservoir bas, dose manquée
- Mode simulation — testez le timing et l'enchaînement sans affecter les vraies données
- Rechargement automatique des automations après fin de simulation
- Pause globale
- Reset complet avec confirmation
- Dashboard desktop + mobile (FR / EN)
- Noms et couleurs libres par pompe

---

### 🔜 v1.0.0 — Première release stable

- Validation complète en conditions réelles (run continu 48h) ✅ en cours
- Correction : surdosage lors du changement de mode en cours de journée
- Documentation finale et release GitHub

---

### 🔜 v1.1.0 — Sécurité avant tout

- **Timeout de sécurité hardware** — l'ESP32 coupe la pompe automatiquement après une durée max configurable, en cas de crash HA ou de défaillance d'automation
- **Watchdog HA (doux + dur)** — niveau doux : pompe OFF + notification warning / niveau dur : toutes les pompes OFF + notification urgence
- **Bouton de dose manuelle physique** — un bouton hardware sur l'ESP32 déclenche une dose manuelle exactement comme le bouton du dashboard, avec confirmation HA et mise à jour des stats. Fonctionne même si le dashboard est inaccessible.

---

### 🔜 v1.2.0 — Précision et cohérence

- **Recalcul des doses restantes lors d'un changement de config** — quand la configuration change en cours de journée, le système ignore les doses déjà livrées et crée un nouveau planning complet, causant un surdosage. Correction : lire le compteur journalier et n'étaler que les doses restantes sur la fenêtre restante.
- **Précision sub-seconde** — les durées de dose sont actuellement arrondies à la seconde entière. Correction : valeurs float (résolution 0.1s) pour une précision 10× supérieure sur les petites doses.
- **Cohérence des volumes** — empêcher de saisir un volume restant ou un seuil d'alerte supérieur au volume du réservoir. Correction : plafonner dynamiquement le `max` des `input_number` quand le volume du réservoir change.

---

### 🔜 v1.3.0 — Expérience utilisateur

- **Dashboard responsive fichier unique** — desktop + mobile fusionnés en un seul fichier adaptatif
- **Tutoriel d'installation interactif** — 7 étapes guidées (notifications, calibration, sécurité, config dosage, compatibilité, simulation, production)

---

### 🔮 Versions futures

#### Mode urgence Bluetooth
En cas de perte WiFi, l'ESP32 peut être contrôlé via Bluetooth en mode urgence.
Interface minimale : déclencher une dose manuelle par pompe. Pas de stats, pas de planning — juste garder le bac en vie.

#### Dosage offline ESP32
Quand Home Assistant est inaccessible, l'ESP32 continue à doser de manière autonome grâce à un planning stocké dans ESPHome. Les statistiques sont synchronisées au retour de la connexion.
Nécessite un module RTC externe pour maintenir l'heure sans WiFi.

#### Expansion modulaire des pompes
Support de plus de 4 pompes via des modules ESP32 supplémentaires (`reefdose_2`, `reefdose_3`...).
Tous les modules gérés depuis un seul dashboard.

#### Personnalisation des couleurs par pompe
Choisir les couleurs des pompes directement depuis le dashboard, sans modifier les fichiers de thème.

#### Dosage déclenché par événement (intégration lumières)
Déclencher les doses par rapport aux événements d'éclairage (après allumage / après extinction + délai configurable).
Nécessite un projet d'automation lumières séparé.

#### Support agitateur magnétique
Module ESP32 dédié pour agiter chaque réservoir avant le dosage.

---

### 💡 Idées en réflexion

- Confirmation de dose par notification push
- Rapport hebdomadaire par push (chaque lundi)
- Mode vacances / pause (suspendre le dosage pendant X jours)
- Support multi-système (2 systèmes de dosage indépendants sur le même HA)
- Export de l'historique des doses (CSV)
- Statistiques avancées (taux de doses manquées %, comparaison volume réel vs configuré)

---

### Hors périmètre

- Connexion cloud — ReefDose est et restera entièrement local
- Application mobile — l'app HA couvre les notifications
- Plus de 4 pompes sur un seul ESP32 — limitation matérielle
