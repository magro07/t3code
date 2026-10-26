# Fork-Fahrplan (magro07/t3code)

Dieser Fork erweitert T3 Code um die Funktionen, die vorher im Projekt „Brise“
(github.com/magro07/brise) entstanden sind. Grundsatz: T3 Codes Stärken
(Performance, Remote-fähig, mehrere Oberflächen) nicht beschädigen, jede Funktion
klein und vollständig umsetzen statt viel halb.

Brise dient als Vorlage für Logik und Erkenntnisse, nicht als Code-Quelle.

## 0. Grundlage

- [ ] Desktop-App für Fedora bauen und installieren (RPM, Updates aus diesem Fork).
- [ ] CI des Forks baut Linux (RPM, AppImage, deb), Windows, macOS.
- [ ] **Onboarding ohne weitere Abhängigkeiten:** Installer herunterladen, starten,
      Anbieter anmelden. Keine CLI, kein Node, kein Terminal nötig. Fehlende Agenten
      installiert die App selbst.
- [ ] **Fernzugriff für Freunde:** einfach einrichtbar (T3 Code hat Remote-Grundlagen:
      Tailscale, Relay/Tunnel, Pairing-Links). Ziel: Freund bekommt einen Link und
      arbeitet mit, ohne eigene Infrastruktur.

## 1. Mistral Vibe und Cortecs

- [ ] Mistral Vibe als Anbieter (über ACP), Anmeldung per Vibe-Key oder Browser.
- [ ] GLM-5.3 als Standardmodell mit den echten Denkstufen. Gemessen am 26.10.2026
      gegen die Mistral-API (`zai-glm-5-3`):
      `reasoning_effort` low/high/max → 200 (max erzeugt Reasoning-Tokens),
      none/medium → 400. Vibes Mistral-Backend verfälscht low→none (400) und
      max→high; deshalb Aufrufe selbst durchreichen (Proxy oder direkte API).
      Denkstufen für alle Modelle messen statt raten.
- [ ] **Voxtral 3 als Spracheingabe (STT)**, auswählbar, läuft über den Vibe- bzw.
      Mistral-Key.
- [ ] **Cortecs** (cortecs.ai, ZDR): Modelle ohne Datenspeicherung
      (`allow_zero_data_retention`), Warnung bei sensiblen Daten (DSGVO,
      Geschäftsgeheimnisse, EU AI Act) mit Wechsel auf ein ZDR-Modell.
- [ ] **Decision-Modelle über Cortecs** (Decisions-API) für Brises kleine
      Entscheidungen: Aufgabe einstufen, Denkstufe wählen, Sensitivität prüfen.
- [ ] **ZDR-Workspaces/-Projekte:** Projekte mit besonderem Schutz, die nur
      Modelle ohne Datenspeicherung nutzen, strengere Freigaben, keine
      Weitergabe an Dienste mit Speicherung, deutlich gekennzeichnet.

## 2. Zusammenarbeit und Teams

- [ ] Sessions bzw. Threads teilen, Rollen (Zuschauer, Mitarbeiter, Freigeber).
- [ ] Gastzugang auf dem eigenen Abo mit Limits (ohne den Schlüssel zu teilen).
      Claude-Code-Abo nicht für Gäste nutzen (Anthropics Bedingungen).
- [ ] Teams mit Admin-Richtlinien (Einstellungen sperren, Modelle erlauben, Budget).
- [ ] Selbst-Hosting dort, wo nötig, klar dokumentiert (Homelab).

## 3. Master-Session und Kurator

- [ ] Orchestrator-Thread, der Unter-Threads startet, steuert und Ergebnisse
      zusammenführt (Worktrees, Merge nach Freigabe).
- [ ] Kurator-Modell entscheidet dynamisch je Teilaufgabe über Anbieter, Modell,
      Denkstufe und Budget; Leitplanken in den Einstellungen.
- [ ] Model Council (zweite Meinungen anderer Modelle), eigene Benchmarks.

## 4. Nutzung, Stats und Budget

- [ ] Kosten und Tokens je Anbieter und Modell, Monatsbudget über alle Anbieter.
- [ ] t/s, Latenz (TTFT) je Modellaufruf.
- [ ] Schöne All-Time-Stats (Heatmap, Streaks, Lieblingsmodelle, Verlauf).

## Später

- Design-Modus mit Designsystem und Designsprache, 3D-Modus, Secrets-Eingabe,
  mehrere Vibe-Keys. Dabei die Kritik an Brise beachten: gleiche Werkzeuge
  (Modellwahl, Spracheingabe, @-Referenzen, Projektzuordnung) überall, flüssiges
  Scrollen und gute Performance auch im Vollbild.
