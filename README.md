# ReefDose — Roadmap

**[English](#english) | [Français](#français)**

---

## English

### Current status : v0.9.8 — Pre-release

The project is actively tested on a real reef aquarium.
Core dosing features are functional. The goal of v1.0.0 is to validate stability before the first public stable release.

---

### ✅ Already available (v0.9.8)

- Automatic dosing — 4 pumps, configurable time window per pump
- Full day mode — clock-aligned dosing (e.g. 24 doses → every hour at :00)
- Manual dose — triggerable at any time
- Cycle reset option — manual dose can optionally shift the auto schedule
- Compatibility matrix — minimum delay between each pump pair
- Real-time validation — warning when configuration is inconsistent
- Calibration — real flow rate measurement (ml/s)
- Tank management — volume, %, days remaining, low level alert
- Statistics — weekly / monthly / yearly / total volumes, successful and missed doses
- 7-day tank level graph
- Push notifications — pump offline, low tank, missed dose
- Simulation mode — test timing and sequencing without affecting real data
- Global pause
- Full reset with confirmation
- Desktop + mobile dashboard (FR / EN)
- Free pump names and colors

---

### 🔜 v1.0.0 — First stable release

- Complete real-world validation (continuous 48h run)
- Final bug fixes from testing phase
- Documentation review

---

### 🔮 Planned — future versions

#### ESP32 offline fallback
When Home Assistant is unreachable, the ESP32 continues dosing independently using a local schedule stored directly in ESPHome. Statistics are synchronized when HA reconnects.

Requires an external RTC module (DS3231 recommended, ~2-5€) for accurate timekeeping without WiFi.

#### Modular pump expansion
Support for more than 4 pumps via additional ESP32 modules (`reefdose_2`, `reefdose_3`...).
All modules managed from a single dashboard.

#### Per-pump color customization
Choose pump colors directly from the dashboard, without editing theme files.

---

### 💡 Ideas under consideration

- Dose confirmation via push notification (tap to confirm a dose was received)
- Weekly dose summary push report (every Monday)
- Holiday / pause mode (suspend dosing for X days)
- Multi-system support (2 independent dosing setups on the same HA instance)
- Simulation mode improvements (per-pump control, scheduled test scenarios)

---

### Not planned

- Cloud connectivity — ReefDose is and will remain fully local
- Mobile app — the HA mobile app covers notifications
- Support for more than 4 pumps on a single ESP32 — hardware limitation

---

## Français

### État actuel : v0.9.8 — Pré-release

Le projet est testé activement sur un aquarium récifal réel.
Les fonctionnalités de dosage principales sont opérationnelles. L'objectif de la v1.0.0 est de valider la stabilité avant la première release publique stable.

---

### ✅ Déjà disponible (v0.9.8)

- Dosage automatique — 4 pompes, fenêtre horaire configurable par pompe
- Mode jour entier — dosage aligné sur l'horloge (ex : 24 doses → toutes les heures à :00)
- Dose manuelle — déclenchable à tout moment
- Option reset de cycle — une dose manuelle peut décaler le planning automatique
- Matrice de compatibilité — délai minimum entre chaque paire de pompes
- Validation en temps réel — alerte si la configuration est incohérente
- Calibration — mesure du débit réel (ml/s)
- Gestion des réservoirs — volume, %, jours restants, alerte seuil bas
- Statistiques — volumes semaine / mois / année / total, doses réussies et manquées
- Graphique historique 7 jours des niveaux réservoirs
- Notifications push — pompe hors ligne, réservoir bas, dose manquée
- Mode simulation — testez le timing et l'enchaînement sans affecter les vraies données
- Pause globale
- Reset complet avec confirmation
- Dashboard desktop + mobile (FR / EN)
- Noms et couleurs libres par pompe

---

### 🔜 v1.0.0 — Première release stable

- Validation complète en conditions réelles (run continu 48h)
- Corrections des derniers bugs identifiés pendant les tests
- Révision de la documentation

---

### 🔮 Prévu — versions futures

#### Dosage offline ESP32
Quand Home Assistant est inaccessible, l'ESP32 continue à doser de manière autonome grâce à un planning stocké directement dans ESPHome. Les statistiques sont synchronisées au retour de la connexion.

Nécessite un module RTC externe (DS3231 recommandé, ~2-5€) pour maintenir l'heure sans WiFi.

#### Expansion modulaire des pompes
Support de plus de 4 pompes via des modules ESP32 supplémentaires (`reefdose_2`, `reefdose_3`...).
Tous les modules gérés depuis un seul dashboard.

#### Personnalisation des couleurs par pompe
Choisir les couleurs des pompes directement depuis le dashboard, sans modifier les fichiers de thème.

---

### 💡 Idées en réflexion

- Confirmation de dose par notification push (appuyer pour confirmer la réception d'une dose)
- Rapport hebdomadaire par push (chaque lundi)
- Mode vacances / pause (suspendre le dosage pendant X jours)
- Support multi-système (2 systèmes de dosage indépendants sur le même HA)
- Améliorations du mode simulation (contrôle par pompe, scénarios de test programmés)

---

### Hors périmètre

- Connexion cloud — ReefDose est et restera entièrement local
- Application mobile — l'app HA couvre les notifications
- Plus de 4 pompes sur un seul ESP32 — limitation matérielle
