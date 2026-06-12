# GuestOps Module Registry

Öffentliches Verzeichnis aller verfügbaren GuestOps-Module.

Enthält ausschließlich `manifest.json` und `module.compose.yml` pro Modul —
kein Quellcode, kein Dockerfile. Die Docker-Images liegen in der privaten
Container-Registry (ghcr.io/ex0th) und erfordern Authentifizierung.

---

## Verfügbare Module

| Modul | Verzeichnis | Beschreibung |
|-------|------------|-------------|
| Schichtübergabe | `shift-handover/` | Digitale Schichtübergabe mit Checklisten, Unterschriften und PDF-Export |
| IT-Betriebsdokumentation | `itdoc/` | Digitales Betriebshandbuch: Geräte, Domains, SaaS, Notfallplan, Wartungsverträge |

---

## Installation in GuestOps Core

```bash
POST /api/modules/install
{
  "repo_url": "https://github.com/ex0th/guestops-module-registry",
  "source_ref": "main",
  "module_path": "shift-handover"
}
```

Voraussetzung: GuestOps Core ≥ 0.5.0

---

## Struktur

```
guestops-module-registry/
└── {module-slug}/
    ├── manifest.json       Metadaten, Permissions, Config-Schema
    └── module.compose.yml  Compose-Template für den Deployment-Agent
```

Die Dateien werden bei jedem Release automatisch durch `release.sh` aktualisiert.
