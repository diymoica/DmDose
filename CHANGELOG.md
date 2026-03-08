# Changelog — ReefDose

All notable changes to this project are documented here.
Format based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)

---

## [0.9.8] — 2026-03-08
### Added
- **Simulation mode** — test the system without affecting real data
  - `input_boolean.rd_sim_mode` : enable/disable simulation mode
  - `input_number.rd_sim_interval` : configurable firing interval (1–10 min)
  - `input_boolean.rd_sim_real_pumps` : optionally trigger real pumps during simulation
  - Stats fully protected when active : counters, tank volumes and totals are not modified
  - `last_dose` timestamp still updates for timing verification
  - Red warning banner displayed on the Control dashboard when simulation is active
  - Simulation controls added to Settings dashboard, Global section

### Fixed
- Auto dosing automations blocked each other when firing simultaneously at H:00
  - Root cause : P1 set the dose lock to ON, blocking P2/P3/P4 until the next hour
  - Fix : dose lock condition removed from auto dosing automations — the queued script handles sequencing natively

### Changed
- `input_boolean.rd_test_mode` (introduced in v0.9.7) renamed to `input_boolean.rd_sim_mode`
- Global dose delay max reduced from 60 to 5 minutes — mechanical use only, chemical delays belong in the compatibility matrix

---

## [0.9.7] — 2026-03-08
### Fixed
- Automatic dosing was completely non-functional
  - Root cause : empty message field in Pump 4 alert caused YAML parser to discard the 4 auto dosing automations
  - Fix : message restored, automations now present and active
- Timezone error when comparing last dose timestamp with current time
  - Error : `TypeError: can't subtract offset-naive and offset-aware datetimes`
  - Fix : `strptime()` replaced with `as_datetime().replace(tzinfo=now().tzinfo)` (16 occurrences)
- Duplicate entity definitions between `rd_config.yaml` and `rd_stat.yaml`
  - Affected : `total_volume`, `total_doses`, `missed_doses`, `last_dose` × 4 pumps
  - Fix : removed from `rd_config.yaml`, kept in `rd_stat.yaml`
- Status icon always displayed red regardless of pump state
  - Root cause : dashboard tested a French string (`'En ligne'`) but sensor returns English (`'Online'`)
  - Fix : now tests `binary_sensor.reefdose_status` directly — works in any language
- "Dosing in progress" indicator was not tappable — no way to manually reset a stuck dose lock
  - Fix : tap action added with confirmation dialog

### Added
- Initial test mode toggle `input_boolean.rd_test_mode` (replaced by simulation mode in v0.9.8)

### Changed
- Global dose delay capped at 5 min max (was 60)
- Dashboard labels and explanatory text updated to clarify mechanical vs chemical delays

---

## [0.9.6] — 2026-03-07
### Fixed
- Dosing window rejected when end time is set to midnight (0h00)
  - Example : start 22h00 → end 0h00 showed "End before start" and a -1320 min interval
  - Fix : end time = 0h00 is now treated as 1440 minutes (end of day)

---

## [0.9.5] — 2026-03-07
### Added
- Full day mode per pump (`input_boolean.rd_pX_full_day`)
  - ON (default) : doses spread evenly across 24h, aligned to clock hours
  - OFF : custom window with start and end time
  - Start/end time fields hidden when full day is ON
- Tank refilled scripts — "Tank refilled!" button was returning an error (scripts were missing)
- Explanatory text above compatibility matrix in all 4 dashboards

### Fixed
- Pump names displayed as raw Jinja template in bar-card and glance cards
- "Next dose" sensor showed "Tomorrow" immediately after enabling full day mode
- Calibration mode did not deactivate after pump run

---

## [0.9.4] — 2026-03-07
### Added
- Manual dose cycle reset option per pump (`input_boolean.rd_pX_manual_resets_cycle`)
  - OFF (default) : manual dose is out-of-cycle, auto schedule continues unchanged
  - ON : manual dose resets the cycle — next auto dose fires 1 interval after the manual dose

### Changed
- Theme CSS variables renamed from pump-specific names to universal `p1/p2/p3/p4` scheme
  - `kh-color` → `p1-color`, `ca-color` → `p2-color`, etc.

---

## [0.9.3] — 2026-03-07
### Added
- Free pump name per pump (`input_text.rd_pX_name`)
  - Displayed dynamically in all dashboard section headers
  - Default : "Pump 1" / "Pump 2" / "Pump 3" / "Pump 4"
  - Examples : "Kh", "Ca", "Nutrient A", "pH Up", "Engrais N"...

---

## [0.9.2] — 2026-03-07
### Added
- Compatibility matrix — 6 configurable minimum delays between pump pairs
  - p1↔p2, p1↔p3, p1↔p4, p2↔p3, p2↔p4, p3↔p4
  - Set to 0 to allow two pumps to dose back-to-back
  - Dose blocked and counted as missed if delay not elapsed
- Settings dashboard section for compatibility matrix

---

## [0.9.1] — 2026-03-07
### Added
- Dosing window per pump (start time → end time)
- Interval sensor per pump (auto-calculated from window and frequency)
- Window validation sensor : OK / "Too many doses for window" / "End before start"
- Automations blocked automatically when window configuration is invalid
- "Next dose" sensor updated to show "Tomorrow" after end time

---

## [0.9.0] — 2026-03-07
### Added
- Fixed start time per pump
- Dosing schedule derived from start time + frequency
- "Next dose" sensor per pump (countdown to next scheduled dose)
- Per-minute trigger for exact scheduling (was hourly)

---

## [0.8.0] — 2026-03-07
### Added
- Full English translation of all package files
- Multi-language support : FR / EN / ES / IT / DE translation files
- GitHub-ready structure
- Split into 5 modular package files
- DMC Theme with CSS variables for pump colors
- Desktop dashboard FR + EN, Mobile dashboard FR + EN
- Full reset button with confirmation

---

## [0.7.0] — 2026-03-07
### Added
- DMC color theme via HA CSS variables
- Mini Graph Card — 7-day tank level history
- Mobile dashboard (2-column layout)

---

## [0.6.0] — 2026-03-05
### Added
- ESPHome binary sensor for connection status
- 3-view dashboard : Control / Settings / Statistics
- 4-column grid layout

---

## [0.5.0] — 2026-03-05
### Added
- Single ESPHome device setup
- Package structure with `!include_dir_named`
- Notification group (`notify.reefdose_admin`)

---

## [0.4.0] — 2026-03-04
### Added
- Split monolithic YAML into 5 modular files

---

## [0.3.0] — 2026-03-03
### Added
- Complete statistics : daily / weekly / monthly / yearly volumes, missed doses, timestamps
- Daily counter reset at midnight

---

## [0.2.0] — 2026-03-03
### Added
- Calibration system per pump (ml/s flow rate measurement)
- Tank level tracking (remaining volume, %, days remaining, alert threshold)
- Low tank alert notifications
- Anti-overlap system

---

## [0.1.0] — 2026-03-03
### Added
- Initial release — 4 pumps via ESP32 / ESPHome
- Automatic dosing (daily dose, frequency, offset)
- Manual dose trigger per pump
- Auto mode toggle and global pause
- Basic dashboard (Mushroom + Bar Card)
