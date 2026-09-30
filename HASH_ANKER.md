# 🔗 Hash-Anker der Feedback-Kette

Off-Server-Nachweis gegen rückwirkende Manipulation der Feedback-JSONL auf dem Webspace.

## Wie es funktioniert

Jeder Feedback-Eintrag enthält einen SHA-256-Hash über seinen Inhalt **plus** den Hash
des vorherigen Eintrags. Das ergibt eine fortlaufende Kette. Ändert ein Angreifer einen
älteren Eintrag, bricht die Kette gegen jeden Anker, der danach kommt.

Der **Git-Commit-Zeitstempel** ist dabei der unverfälschbare Zeuge: GitHub sieht,
wann welcher Hash committet wurde, und niemand kann rückwirkend committen.

## Wie du es benutzt

1. Alle paar Tage in den Viewer schauen: `https://innobytix-it.de/MelasFarm/issues/viewer.php`
2. Den Hash-Anker (ganz oben, "🔗 Aktueller Hash-Anker") kopieren
3. Hier unten als neuen Eintrag einfügen und committen

Beim Prüfen einer bestimmten Zeit später:
- Feedback-JSONL vom Server holen
- Kette bis zum gespeicherten Anker durchlaufen
- Wenn ein Eintrag vor dem Anker nicht mehr passt → Manipulation nachgewiesen

## Verlauf

Format: `YYYY-MM-DD HH:MM (Zeitzone) · N Einträge · HASH`

- **2026-09-30 18:07 (CEST) · 1 Eintrag · `e1361c731ea48cb68ff640f3fda9a08b9db12ea3a244b456a13d5373308a7235`**
  Genesis: erster Testeintrag nach Deployment auf innobytix-it.de.
