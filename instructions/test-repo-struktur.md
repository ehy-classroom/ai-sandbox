# Vorschlag: Test-Repo-Struktur für DIY KI-Benchmarks

test-repo/
│
├─ README.md                  # Beschreibung des Ziels: KI-Modelle in praxisnahen Aufgaben testen
├─ instructions.md             # Globale Instruktionen, gelten für alle Modelle
├─ agent-bootstrap.md          # Bootstrap-Regeln (wie in deinem bestehenden Setup)
├─ model-prompts.md            # Sammlung von System-Prompts (Sonnet, Opus, GPT-5, Minis)
│
├─ benchmarks/
│   ├─ linting/
│   │   ├─ bad_readme.md       # Absichtlich schlecht formatiert, zum Fixen
│   │   └─ bad_code.js         # JS-Datei mit Linting-Fehlern
│   │
│   ├─ snippets/
│   │   ├─ regex_tasks.md      # Aufgabenbeschreibung
│   │   └─ helpers.php         # zu ergänzende PHP-Utility-Funktionen
│   │
│   ├─ refactor/
│   │   ├─ prototype.js        # Monolithische Datei
│   │   └─ target_structure.md # Zielstruktur (Komponenten)
│   │
│   ├─ db/
│   │   ├─ schema_sqlite.sql   # Ausgangsschema
│   │   └─ migrate_to_mysql.md # Aufgabe: Migration vorbereiten
│   │
│   ├─ fuzzy/
│   │   └─ bouncing_ball.md    # Aufgabe: Animation mit Start/Stop
│   │
│   └─ delegation/
│       ├─ markdownlint.md     # Aufgabe: soll Tool nutzen, nicht halluzinieren
│       └─ test_fail_case.js   # Datei mit failing Tests
│
├─ results/
│   ├─ sonnet4/
│   ├─ opus4/
│   ├─ gpt41/
│   ├─ gpt5/
│   ├─ gpt5mini/
│   ├─ o3mini/
│   └─ llama31/
│       └─ … (dokumentierte Outputs, Kosten, Zeitaufwand, subjektives Empfinden)
│
└─ scripts/
    ├─ run_linter.sh           # deterministische Tools (Markdownlint, ESLint)
    └─ run_tests.sh            # Jest/PHPUnit Tests für automatisierte Überprüfung
