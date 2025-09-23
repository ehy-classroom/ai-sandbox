# Leitfaden: DIY-Benchmarks für KI-Coding-Modelle (Praxis-Setup)

## Zielsetzung
- **Realistische Testszenarien** aus deinem Arbeitsumfeld (Praxismanagement, Web-Apps, kleine Tools).
- **Kosten & Ressourcenverbrauch verstehen**:
  - Wie schnell laufen Tokens/Kontingente leer?
  - Welche Modelle sind effizient im Agent-Loop?
- **Ressourcenplanung verbessern**:
  - Premium-Modelle nur dort einsetzen, wo sie ROI bringen.
  - Billigere/Lokale Modelle gezielt für Snippets oder Baselines nutzen.

---

## Benchmarks: Modelleinsätze & Charakteristika

### Claude Sonnet 4
- **Stärke**: Instruktionsgehorchsam, präzise Umsetzung, wenig Nachhaken nötig.
- **Einsatz**: Alltagsarbeit, Linting-Fixes, Multi-File-Refactor, DB-Architektur.
- **Benchmark-Rolle**: Daily Driver / Hauptreferenz.

### Claude Opus 4 (und 4.1)
- **Stärke**: liefert bei „sloppy prompts“ komplette, funktionierende Lösungen.
- **Einsatz**: fuzzy Aufgaben, kreative Komplettlösungen (z. B. Animation).
- **Benchmark-Rolle**: Premium-Joker, wenn du keine Lust auf Feintuning hast.

### GPT-5 (full)
- **Stärke**: stark im Reasoning, Architekturüberlegungen, lange Kontexte.
- **Schwäche**: ignoriert klare Anweisungen im Agent-Loop, Overhead.
- **Benchmark-Rolle**: nur für große Planungstasks, nicht für exakte Agent-Ausführung.

### GPT-5 mini
- **Stärke**: schnell, billig, kleine Snippets.
- **Schwäche**: verbose (erklärt intern seine Schritte), verliert bei längeren Aufgaben.
- **Benchmark-Rolle**: Snippet-Generator, Lernhilfe, Baseline.

### GPT-4.1 / GPT-4o
- **Stärke**: okay für Text, Doku, einfache Snippets.
- **Schwäche**: versagt bei Linting/konkreten Regeln, liefert „Garbage“ bei exakten Tasks.
- **Benchmark-Rolle**: Negativ-Vergleich, zeigt Qualitätsunterschiede.

### o3-mini / o4-mini
- **Stärke**: billig, schnell, trivialer Code.
- **Schwäche**: verliert bei Multi-File, Regel-Tasks.
- **Benchmark-Rolle**: Billig-Baseline.

### Meta-Llama-3.1 (lokal, 8B)
- **Stärke**: solide Open-Source, besser als Minis, kostenlos im Betrieb.
- **Schwäche**: kein Vergleich zu Premium (Kontextverlust, schwächerer Agent-Loop).
- **Benchmark-Rolle**: Lokaler Gratis-Benchmark, zeigt, was ohne Premium geht.

### DeepSeek-Coder, CodeLlama, CodeGemma (lokal)
- **Stärke**: kleine Snippets, Experimente, offline.
- **Schwäche**: nicht stabil bei Multi-File/Refactors.
- **Benchmark-Rolle**: Ergänzende Baselines.

---

## Benchmark-Kategorien

### 1. **Linting & Style-Fixes**
- README.md / Markdownlint / ESLint / Prettier.
- Erwartung: Modelle setzen triviale Regeln **ohne Nachfragen** um.
- Beobachtung: Sonnet 4 kann’s, GPT-4.1 liefert Garbage, Llama verweist aufs Tool.

### 2. **Snippets & Utility-Funktionen**
- Regex, kleine PHP-Funktionen, SQL-Queries.
- Erwartung: Mini-Modelle ausreichend, Sonnet/Opus stabiler.

### 3. **Multi-File-Refactors**
- z. B. Vue-Komponente aus JS-Prototyp herausziehen.
- Erwartung: Sonnet 4 schafft’s, GPT-5 ignoriert Regeln, Minis scheitern.

### 4. **Architektur & DB-Design**
- SQLite → MySQL Migration, Schema-Design.
- Erwartung: Premium (Sonnet/Opus/GPT-5) liefern tragfähige Pläne.

### 5. **Fuzzy Prompts**
- „Mach mir eine Bouncing-Ball-Animation mit Start/Stop“.
- Erwartung: Opus liefert funktionierende Komplettlösung, andere Modelle nicht.

### 6. **Tool-Delegation**
- Linting oder Testing → welche Modelle raten, eingebaute Tools zu nutzen?
- Beobachtung: Meta-Llama „ehrlich“, Sonnet fixiert selbst, GPT-4.1 halluziniert.

---

## Messpunkte für dich
- **Kosten** (API-Reports, Copilot %-Anzeige, Anthropic Console).
- **Tokenverbrauch** (Logs).
- **Korrekturen pro Task** (wie oft musst du nachjustieren?).
- **Arbeitszeit bis zum Ergebnis** (5 min vs. 30 min).
- **Subjektives Empfinden** (frustig vs. flowig).

---

## Ergänzende Benchmarks aus der Forschung
- **SWE-bench** (Goldstandard für repo-weite Aufgaben).
- **EvalPlus (HumanEval+/MBPP+)** für Snippet-Tests.
- **LiveCodeBench** für kontaminationsfreie Algorithmik- und Repair-Aufgaben.
- → Deine DIY-Benchmarks orientieren sich am SWE-bench-Prinzip, aber mit **Praxis-relevanten Szenarien** (Praxissoftware, Web-Apps, kleine Tools).

