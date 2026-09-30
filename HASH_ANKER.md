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

*(noch leer — nach dem ersten Feedback kannst du hier den Anker eintragen)*

Format:
```
YYYY-MM-DD HH:MM UTC · N Einträge · HASH
```

<!--
Beispiel:
2026-10-01 14:32 UTC · 5 Einträge · 3b8a1f2e4c5d6789abcdef0123456789abcdef0123456789abcdef0123456789
-->
