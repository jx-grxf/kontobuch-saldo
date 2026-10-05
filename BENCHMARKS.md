# Saldo – Benchmark

<img src="saldo.svg" width="72" align="right" alt="Saldo">

**Saldo 0.1.0** ist das Buchungsmodell von Kontobuch: Qwen3-0.6B mit LoRA, trainiert auf eigenen Übungsfällen (Trainingslauf v5).
Gemessen wird auf Fällen, die das Modell nie gesehen hat.

## Auf einen Blick

| | |
|---|---|
| Neue Fälle richtig, in der App | **95,5 %**, 0 falsch angezeigt (Regeln allein 64,0 %) |
| Echte Buchfälle richtig, in der App | **67 von 69**, 0 falsch angezeigt (HTL I und II) |
| Saldo allein, neue Fälle / Buchfälle | 96,0 % / 75,4 % |
| Fallart richtig erkannt | 99,8 % |
| Zeit pro Fall | 0,26 s (Median in der App, llama.cpp auf der GPU, MacBook Pro M5 Pro) |
| Größe | 639 MB (GGUF Q8_0) |
| Läuft | auf dem Gerät, ohne Internet; Mac (GPU), Windows und Linux (CPU) |

> Saldo darf eine Buchung bestätigen, aber nie als falsch markieren. Eine falsche Antwort von Saldo erreicht einen Schüler deshalb nie als „falsch“.

## Neue Fälle (400)

Geschrieben aus Firmennamen, Personen, Waren und Formulierungen, die im Training nicht vorkamen.

| Weg | richtig | falsch | keine Antwort | Genauigkeit | |
|---|---:|---:|---:|---:|---|
| Regeln allein | 256 | 0 | 144 | **64,0 %** | `█████████████░░░░░░░` |
| Saldo allein | 384 | 13 | 3 | **96,0 %** | `███████████████████░` |
| Regeln + Saldo | 397 | 1 | 2 | **99,2 %** | `████████████████████` |
| **In der App** (Saldo geprüft) | 382 | 0 | 18 | **95,5 %** | `███████████████████░` |

## Echte Buchfälle (69)

Übungen aus *Unternehmensrechnung HTL I* und *HTL II*: drei ganze Übungen aus Seitenbildern gelesen wie in der App, dazu einzelne Fälle zu Anlagenverkauf, Versicherungsschaden, Forderungsausfall, Bonus, Eigenverbrauch und Gehalt. Nie trainiert, nur gemessen.

| Weg | richtig | falsch | keine Antwort | Genauigkeit | |
|---|---:|---:|---:|---:|---|
| Regeln allein | 57 | 0 | 12 | **82,6 %** | `█████████████████░░░` |
| Saldo allein | 52 | 14 | 3 | **75,4 %** | `███████████████░░░░░` |
| Regeln + Saldo | 67 | 2 | 0 | **97,1 %** | `███████████████████░` |
| **In der App** (Saldo geprüft) | 67 | 0 | 2 | **97,1 %** | `███████████████████░` |

| Übung | Fälle | Saldo allein | Regeln + Saldo |
|---|---:|---:|---:|
| htl2 Ü 4.15 | 2 | 1/2 | 2/2 |
| htl2 Ü 4.20 | 1 | 1/1 | 1/1 |
| htl2 Ü 4.21 | 2 | 2/2 | 2/2 |
| htl2 Ü 4.18 | 2 | 2/2 | 2/2 |
| htl2 Ü 6.6 | 3 | 2/3 | 2/3 |
| htl2 Ü 1.24 | 3 | 2/3 | 2/3 |
| htl2 Ü 1.25 | 1 | 1/1 | 1/1 |
| htl1 Ü 9.30 | 5 | 5/5 | 5/5 |
| htl1 Ü 9.33 | 10 | 8/10 | 10/10 |
| K 1.3 | 20 | 12/20 | 20/20 |
| Ü 1.26 | 10 | 8/10 | 10/10 |
| Ü 1.21 | 10 | 8/10 | 10/10 |

## Nach Fallart (neue Fälle)

| Fallart | Fälle | Regeln | Saldo | Regeln + Saldo |
|---|---:|---:|---:|---:|
| Aufwand | 54 | 90,7 % | 90,7 % | 100,0 % |
| Warenverkauf | 43 | 100,0 % | 93,0 % | 100,0 % |
| Wareneinkauf | 38 | 100,0 % | 89,5 % | 100,0 % |
| Anlagenkauf | 36 | 61,1 % | 97,2 % | 100,0 % |
| Sonstiger Ertrag | 17 | 82,3 % | 100,0 % | 100,0 % |
| Gutschrift an Kunden | 13 | 100,0 % | 100,0 % | 100,0 % |
| Abschreibung | 13 | 30,8 % | 92,3 % | 92,3 % |
| USt-Zahllast | 12 | 100,0 % | 100,0 % | 100,0 % |
| Gehaltsabrechnung | 11 | 0,0 % | 100,0 % | 100,0 % |
| Mahnung vom Lieferanten | 11 | 100,0 % | 100,0 % | 100,0 % |
| Mahnung | 10 | 100,0 % | 100,0 % | 100,0 % |
| Materialeinkauf | 9 | 100,0 % | 100,0 % | 100,0 % |
| Versicherungsschaden | 8 | 0,0 % | 100,0 % | 100,0 % |
| Zinsen und Spesen | 8 | 50,0 % | 100,0 % | 100,0 % |
| Forderungsausfall | 7 | 0,0 % | 85,7 % | 85,7 % |
| Kartenabrechnung | 7 | 0,0 % | 100,0 % | 100,0 % |
| Innergemeinschaftlicher Erwerb | 6 | 0,0 % | 100,0 % | 100,0 % |
| Ausgangsfracht | 6 | 83,3 % | 100,0 % | 100,0 % |
| Rückstellung | 6 | 0,0 % | 100,0 % | 100,0 % |
| Reisekosten | 6 | 0,0 % | 100,0 % | 100,0 % |
| Kfz-Kosten | 6 | 0,0 % | 100,0 % | 100,0 % |
| Steuerfreie Lieferung | 5 | 0,0 % | 100,0 % | 100,0 % |
| Eigenverbrauch | 5 | 0,0 % | 100,0 % | 100,0 % |
| Dienstgeberabgaben | 5 | 0,0 % | 100,0 % | 100,0 % |
| Bestandsveränderung | 5 | 0,0 % | 100,0 % | 100,0 % |
| USt-Umbuchung | 5 | 0,0 % | 80,0 % | 80,0 % |
| Anlagenverkauf | 4 | 0,0 % | 100,0 % | 100,0 % |
| Zahlung vom Kunden | 4 | 100,0 % | 100,0 % | 100,0 % |
| Bezugskosten | 4 | 100,0 % | 100,0 % | 100,0 % |
| Darlehen | 4 | 25,0 % | 100,0 % | 100,0 % |
| Zahlung an Lieferanten | 4 | 100,0 % | 100,0 % | 100,0 % |
| Inzahlungnahme | 4 | 0,0 % | 100,0 % | 100,0 % |
| Umsatzbonus | 3 | 0,0 % | 100,0 % | 100,0 % |
| Anlagen in Bau | 3 | 0,0 % | 100,0 % | 100,0 % |
| Bareinzahlung | 3 | 100,0 % | 100,0 % | 100,0 % |
| Abgabenzahlung | 3 | 0,0 % | 100,0 % | 100,0 % |
| Eigenleistung | 3 | 0,0 % | 100,0 % | 100,0 % |
| Einfuhrumsatzsteuer | 2 | 0,0 % | 100,0 % | 100,0 % |
| Gutschrift vom Lieferanten | 2 | 100,0 % | 100,0 % | 100,0 % |
| Barabhebung | 1 | 100,0 % | 100,0 % | 100,0 % |
| Einzelwertberichtigung | 1 | 0,0 % | 100,0 % | 100,0 % |
| Privateinlage | 1 | 100,0 % | 100,0 % | 100,0 % |
| Privatentnahme Bank | 1 | 100,0 % | 100,0 % | 100,0 % |
| Privatentnahme bar | 1 | 100,0 % | 100,0 % | 100,0 % |

## Verlauf

| Lauf | Prompt | neue Fälle: Saldo / Regeln + Saldo | Buchfälle: Saldo / Regeln + Saldo |
|---|---|---:|---:|
| v5@data-v5-400 (400 neue Fälle) | + 15 Fallarten, Bestand und Halbjahr benannt | 96,0 % / 99,2 % | 75,4 % / 97,1 % |
| v4@data-v5-400 (400 neue Fälle) | + Fallart, Abschluss, Anlagen, Gehalt | 61,0 % / 76,8 % | 66,7 % / 85,5 % |
| v3 (200 neue Fälle) | + Buchformate, Konto bei offenen Belegen | 88,5 % / 99,0 % | 72,5 % / 100,0 % |
| v2 (2000 neue Fälle) | Beträge mit Herkunft | 87,8 % / 95,6 % | 67,5 % / 100,0 % |

## So wird gemessen

- **Richtig** heißt: Jedes Konto endet mit dem richtigen Betrag auf der richtigen Seite; die Reihenfolge der Zeilen zählt nicht.
- **Regeln allein** zählt nur Fälle, bei denen sich die Engine sicher ist; nur diese beurteilt die App ohne Saldo.
- **Saldo allein**: Eine Antwort, die sich nicht lesen lässt, nicht aufgeht oder einen Betrag verwendet, der nicht im Prompt steht, zählt als „keine Antwort“.
- **Regeln + Saldo**: Regeln, wo sie sicher sind, sonst die Antwort von Saldo.
- **In der App** ist, was ein Schüler sieht: wie Regeln + Saldo, aber jede Antwort von Saldo geht durch die Prüfung der App: sie muss aufgehen, jeden Betrag des Falls buchen, eine genannte Steuer, ein genanntes Konto und das Personenkonto buchen und zum Wörterbuch der Regeln passen. Was die Prüfung nicht besteht, bleibt „nicht sicher“ und wird nie als falsch angezeigt.
- Die neuen Fälle schreibt derselbe Generator wie die Trainingsfälle, aber nur aus dem Teil der Wortlisten, der im Training fehlt. Die Buchfälle bleiben auf dem Rechner, auf dem gemessen wird; sie werden nie veröffentlicht und nie trainiert.
- Der veröffentlichte Lauf wurde mit 400 neuen Fällen gemessen. Die Zeit pro Fall ist die der App selbst (llama.cpp in Rust, mit derselben Grammatik wie in der App).

Gemessen und erzeugt im (nicht öffentlichen) Repository von Kontobuch.
