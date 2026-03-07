# ReefDose — Universal Smart Dosing Controller

<div align="center">

![Version](https://img.shields.io/badge/version-0.9.4-orange)
![Status](https://img.shields.io/badge/status-testing-yellow)
![HA](https://img.shields.io/badge/Home%20Assistant-2023.x%2B-41BDF5)
![License](https://img.shields.io/badge/license-Custom-orange)
![Use case](https://img.shields.io/badge/use%20case-universal-brightgreen)
![Code](https://img.shields.io/badge/code-coming%20soon-lightgrey)

**[Français](#français) | [English](#english)**

</div>

---

> ⚠️ **Le code n'est pas encore publié — en cours de test.**
> **Code not yet released — currently in real-world testing.**
> [Watch this repo](../../watchers) to be notified when it drops. ⭐

---

## Français

### Ce que ReefDose fait

ReefDose est un **contrôleur de dosage liquide universel** piloté par Home Assistant et ESP32.
Il gère 4 pompes péristaltiques avec précision — quelle que soit la solution dosée.

**Une dose = un volume précis, au bon moment, automatiquement.**
Tu configures une fois. Le reste se fait tout seul.

### À quoi ça sert ?

| Domaine | Pompe 1 | Pompe 2 | Pompe 3 | Pompe 4 |
|---|---|---|---|---|
| 🪸 Aquariophilie récifale | Kh | Ca | Mg | Phyto |
| 🌿 Hydroponie | Nutriment A | Nutriment B | pH Up | pH Down |
| 🌱 Plantes d'intérieur | Engrais N | Engrais P | Engrais K | Stimulateur |
| 🍺 Brassage | Acide | Base | Additif 1 | Additif 2 |
| 🔬 Laboratoire DIY | Solution 1 | Solution 2 | Solution 3 | Solution 4 |

> Chaque pompe a un **nom libre**, une **couleur libre**, ses propres **horaires** et sa propre **logique**.
> Aucune contrainte liée à un domaine particulier.

### Ce que tu obtiens

- 📊 **Dashboard complet** — desktop et mobile, FR et EN
- ⏰ **Fenêtre de dosage** — plage horaire configurable par pompe (début → fin)
- 🔄 **Intervalle calculé** automatiquement selon la fenêtre et la fréquence
- 🤝 **Matrice de compatibilité** — délai minimum entre chaque paire de pompes
- 🏷️ **Noms libres** — appelle tes pompes comme tu veux
- 📏 **Calibration** — mesure du débit réel ml/s, précision garantie
- 📦 **Gestion des réservoirs** — volume restant, jours restants, alerte seuil bas
- 📈 **Statistiques** — volumes dosés semaine/mois/année, doses réussies/manquées
- 🔔 **Alertes** — pompe hors ligne, réservoir bas, dose manquée
- ⏸️ **Pause globale** — stoppe tout en un clic

### Matériel requis

- ESP32 avec ESPHome
- Home Assistant (2023.x+)
- 4 pompes péristaltiques (tête de pompe DC 12V recommandée)
- C'est tout.

### Quand le code sera disponible ?

En cours de test sur installation réelle.
Le code sera publié en **v1.0.0** — quand il sera stable et documenté.

👉 **[Watch ce repo](../../watchers)** pour être notifié.
👉 **[Star ce repo](../../stargazers)** pour soutenir le projet.
👉 **[Rejoins les discussions](../../discussions)** pour échanger.

---

## English

### What ReefDose does

ReefDose is a **universal liquid dosing controller** powered by Home Assistant and ESP32.
It manages 4 peristaltic pumps with precision — whatever liquid you're dosing.

**One dose = the right volume, at the right time, automatically.**
Configure once. It runs itself.

### What can it dose?

| Domain | Pump 1 | Pump 2 | Pump 3 | Pump 4 |
|---|---|---|---|---|
| 🪸 Reef aquarium | Kh | Ca | Mg | Phyto |
| 🌿 Hydroponics | Nutrient A | Nutrient B | pH Up | pH Down |
| 🌱 Indoor plants | N fertilizer | P fertilizer | K fertilizer | Booster |
| 🍺 Brewing | Acid | Base | Additive 1 | Additive 2 |
| 🔬 DIY lab | Solution 1 | Solution 2 | Solution 3 | Solution 4 |

> Each pump has a **free name**, a **free color**, its own **schedule** and its own **logic**.
> No constraints tied to any specific domain.

### What you get

- 📊 **Full dashboard** — desktop and mobile, FR and EN
- ⏰ **Dosing window** — configurable time window per pump (start → end)
- 🔄 **Auto-calculated interval** based on window and requested frequency
- 🤝 **Compatibility matrix** — minimum delay between each pump pair
- 🏷️ **Free pump names** — call your pumps whatever you want
- 📏 **Calibration** — real flow rate measurement in ml/s
- 📦 **Reservoir management** — remaining volume, days left, low level alert
- 📈 **Statistics** — dosed volumes weekly/monthly/yearly, hits/misses
- 🔔 **Alerts** — pump offline, low reservoir, missed dose
- ⏸️ **Global pause** — stop everything in one click

### Required hardware

- ESP32 with ESPHome
- Home Assistant (2023.x+)
- 4 peristaltic pumps (DC 12V pump head recommended)
- That's it.

### When will the code be available?

Currently being tested on a real installation.
Code will be released as **v1.0.0** — when stable and fully documented.

👉 **[Watch this repo](../../watchers)** to get notified.
👉 **[Star this repo](../../stargazers)** to support the project.
👉 **[Join the discussions](../../discussions)** to share your use case.

---

## Roadmap

See [ROADMAP.md](ROADMAP.md) for the full plan.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

---

*Part of the [DIY Moi Ca](https://github.com/diymoica) project — [diymoica.com](https://diymoica.com)*
*Made with ❤️ in France — shared with the world*

---

## License

Copyright (c) 2026 DIY Moi Ca — Personal use only, no commercial use.
See [LICENSE](LICENSE) for full terms.
