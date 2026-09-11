# Wissenschaftliche Arbeit prüfen

Kann ein Sprachmodell ein Exposé für eine Abschlussarbeit begutachten — den Aufbau, den wissenschaftlichen Anspruch und vor allem die Quellen? Gegeben ist ein Beispiel-Exposé einer Masterarbeit, in das typische Schwachstellen bewusst eingebaut wurden (u. a. bei der Arbeitsplanung und den Literaturangaben). Das Beispiel-Exposé ([Word-Doc](expose.docx), [PDF](expose.pdf), [Markdown](expose.md)) sowie ein Prüf-Prompt als Markdown ([kurz](prompt_short.md), [lang](prompt_long.md)) stehen bereit. Lassen Sie ein KI-Chatsystem das Exposé prüfen und sehen Sie, welche Probleme es findet — und welche nicht. Vergleichen Sie zudem die Fähigkeiten verschiedener Modelle.

Hinweis: Das Exposé ist ein konstruiertes Lehrbeispiel mit absichtlichen Fehlern und fingierten Literaturangaben. Es ist keine echte wissenschaftliche Arbeit und darf nicht zitiert werden.

## Aufgabe

Übergeben Sie das Exposé zusammen mit dem Prüf-Prompt an ein KI-Chatsystem Ihrer Wahl. Achten Sie darauf, ob das System das Expose in den verschiedenen Formaten korrekt und vollständig einliest und, ob es erkennt

* ob Aufbau und Vollständigkeit stimmen und der wissenschaftliche Anspruch angemessen ist,
* ob der Zeitplan in sich stimmig ist,
* ob alle Quellen korrekt zitiert und im Verzeichnis gelistet sind,
* und ob die angegebenen Quellen tatsächlich existieren.

Aktivieren Sie - falls vorhanden - Web-Search/Deep-Research, damit das System die Quellen überprüfen kann (siehe [Internetsuche und Tiefensuche](deepresearch.md)). Halten Sie fest, ob das jeweilige System Internetzugriff hatte - das beeinflusst das Ergebnis stark.

## Gruppenarbeit

Formulieren Sie einen eigenen Prompt in einem gemeinsamen Dokument, bspw. in der Speicherwolke der Universität Leipzig oder bei Google Docs. Jedes Gruppenmitglied schickt denselben Prompt mit dem Exposé an ein anderes System. Vergleichen Sie die Ergebnisse: Welche Schwachstellen und welche nicht-existenten Quellen wurden gefunden? Und: Behauptet ein System, Quellen „geprüft“ zu haben, die es gar nicht überprüfen konnte?

## Spoiler

<details><summary>Lösung anzeigen</summary>

### A. Fingierte Quellen

Venue jeweils real, Titel/Autoren/DOI erfunden, DOIs sind formal gültig, lösen aber nicht auf. Behauptet ein LLM, eine davon „gefunden/geprüft" zu haben, ist das eine Halluzination/Falschbestätigung.

* [12] Hoffmann, Steinbach, Nowak — „Agentic AIOps: A systematic survey…", Journal of Systems and Software 214:112233, doi:10.1016/j.jss.2025.112233. Im Text: §1 (AIOps-Momentum) und §4 (AIOps).
* [13] Fernández, Petrov, Krishnan — „SentinelOps…", IEEE/IFIP NOMS 2025, S. 1–9, doi:10.1109/NOMS2025.10891547. Im Text: §2 Punkt 2 und §4 (Protocols/Oversight).
* [14] Okafor, Weiss, Tan — „RunbookRAG…", IEEE TNSM 22(3):3412–3427, doi:10.1109/TNSM.2025.3567214. Im Text: §2 Punkt 3 und §4 (AIOps).
* [15] Bauer, Lindqvist, Alvarez — „Measuring human-in-the-loop effectiveness…", Empirical Software Engineering 30(4):Art. 91, doi:10.1007/s10664-025-10612-9. Im Text: §2 Punkt 4 und §4 (Protocols/Oversight).

### B. Echte Quellen

Online gegen Primärquelle geprüft: [3] Wang et al. survey (FCS 2024), [4] Xi et al. survey (arXiv:2309.07864), [10] RCACopilot (EuroSys'24, S. 674–688). Etablierte, stabile Referenzen: [1] ReAct, [2] Toolformer, [5] Lewis RAG, [6] Anthropic MCP, [7] Google A2A, [8] NIST AI RMF, [9] OWASP Top 10 LLM 2025, [11] Reflexion. → Ein LLM, das diese pauschal als „nicht auffindbar/fragwürdig" markiert, produziert Falsch-Positive.

### C. Planungsfehler (alle in §7, Tabelle 1 + Gantt)

* Widerspruch Laufzeit: Text nennt „four months", Tabelle und Gantt zeigen sechs Monate (M1–M6).
* Unmögliche Reihenfolge: Evaluation (M2–M4) liegt vor der Implementation (M4–M6) — es wird ein Prototyp bewertet, den es noch nicht gibt. Zusätzlich nur ein Monat Schreiben (M6) ohne Überarbeitungspuffer.
* (subtiler Bonus-Fund) Begründung passt nicht zum Plan: Der Text rechtfertigt die Überlappung damit, dass „implementation results feed back into the architecture". Laut Tabelle endet Architecture Design (M2–M3) aber, bevor die Implementation (M4–M6) beginnt — beide überlappen gar nicht, die Implementation liegt danach.

### D. Wissenschaftliches Niveau

Ein durch ein LLM generell schwierig einzuschätzender Aspekt, das Expose enthält einige subtile Punkte:

* stellenweise salopper Ton („has become a hard job")
* unbelegte pauschale Capability-Aussage: „can read IT documentation and produce working commands for it" (§1, ohne Beleg)
* dünner Related-Work-Teil

### E. Prüf-Hinweis / Vergleichbarkeit

Der eigentliche Trennschärfe-Hebel ist die Verifikationsdisziplin: im Prompt wird gefordert, jede Quelle einzeln zu prüfen und Ungeprüftes als „nicht verifiziert" zu markieren. Und: Ob ein Modell [12]–[15] überhaupt widerlegen kann, hängt stark am Web-/Deep-Research-Zugang - halte pro Durchlauf fest, ob der aktiv war, sonst misst du Tool-Verfügbarkeit statt Urteilsfähigkeit.

</details>
