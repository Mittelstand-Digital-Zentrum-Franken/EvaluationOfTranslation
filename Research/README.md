# Research: Evaluierungsmetriken zur Evaluierung der Übersetzungsqualität

In diesem Dokument werden verschiedene Metriken und Herangehensweisen zur Evaluierung der Qualität von Übersetzungen vorgestellt. Die Auswahl der geeigneten Metriken ist entscheidend, um eine präzise Bewertung der Übersetzungsqualität zu ermöglichen.

Hierfür gibt es unterschiedliche Bereiche mit welchen sich die Metriken befassen:

1. **Stringbasierte Metriken**
2. **Deep Learning-basierte Metriken**
3. **Sprachmodelle als Evaluatoren**
4. **Readability mithilfe von Textstat**

<br/>

## Stringbasierte Metriken
**Definition**: Metriken oder Maßeinheiten, die auf Zeichenketten oder Textdaten basieren, um Eigenschaften von Texten zu quantifizieren und zu analysieren.

**Beispiele**:
- **Länge**: Anzahl der Zeichen oder Zeichenketten in einem Text.
- **Wortanzahl**: Anzahl der Wörter in einem Text.
- **Vorkommen eines bestimmten Zeichens oder einer bestimmten Zeichenkette**: Häufigkeit eines bestimmten Zeichens oder einer Zeichenkette im Text.
- **Häufigkeit von Wörtern**: Wie oft bestimmte Wörter im Text auftreten.
- **Vergleich von Zeichenketten**: Messung der Ähnlichkeit zwischen zwei Zeichenketten (z.B. Levenshtein-Distanz, Jaccard-Index).
- **Entropie**: Maß für die Unvorhersehbarkeit der Zeichenfolge.
- **Lesbarkeitsindex**: Versucht, die Lesbarkeit eines Textes zu quantifizieren.
- **TF-IDF (Term Frequency-Inverse Document Frequency)**: Maß für die Bedeutung eines Wortes in einem Dokument relativ zu einer Sammlung von Dokumenten.

**Metriken**:

| Metrik | Definition | Vorteile | Nachteile |
|--------|------------|----------|-----------|
| **BLEU** | Bewertet die Übereinstimmung von n-Grammen zwischen der Übersetzung und einer Referenzübersetzung. | Schnell, weit verbreitet, automatisierte Bewertung | Berücksichtigt keine Synonyme, ignoriert den Kontext |
| **ChrF** | Bewertet die Übersetzung auf Basis der Übereinstimmung von Zeichen- und Wortn-Grammen. | Berücksichtigt Zeichen- und Wortebene, nützlich für morphologisch reiche Sprachen | Geringere Bekanntheit und Akzeptanz im Vergleich zu BLEU |

<br/>

## Deep Learning-basierte Metriken

**Definition**: Diese Metriken nutzen neuronale Netze und Lernalgorithmen, um die Qualität von Übersetzungen zu bewerten, oft unter Berücksichtigung komplexer sprachlicher Zusammenhänge und Kontexte.

**Mögliche Herangehensweisen**:
- **End-to-End-Metriken**: Evaluierung durch komplette Modelle, die Übersetzungen direkt bewerten.
- **Vergleich der Satz-Tokens im Einbettungsraum**: Verwendet Einbettungsräume, um die semantische Ähnlichkeit zwischen Satz-Tokens zu bewerten.

**Metriken**:
| Metrik | Definition | Vorteile | Nachteile |
|--------|------------|----------|-----------|
| **BERTScore** | Nutzt kontextuelle Einbettungen von BERT, um die semantische Ähnlichkeit zwischen der Übersetzung und Referenzübersetzungen zu messen. | Nutzt kontextuelle Einbettungen, um semantische Ähnlichkeiten zu messen | Rechenintensiv, benötigt vortrainierte Modelle |
| **mBERT** | Mehrsprachiges Modell von BERT, das für die Bewertung von Übersetzungen in mehreren Sprachen optimiert ist. | Mehrsprachig, gut für Übersetzungen zwischen verschiedenen Sprachen | Benötigt umfangreiche Ressourcen für Training und Bewertung |
| **COMET** | Bewertet Übersetzungen durch Vergleich der semantischen Ähnlichkeit und des Kontextes unter Verwendung vortrainierter Modelle. | Bietet umfassende Bewertung unter Berücksichtigung des Kontexts | Komplexe Implementierung, Rechenaufwand |

<br/>

## Sprachmodelle als Evaluatoren

**Definition**: Sprachmodelle werden verwendet, um die Qualität von Übersetzungen zu bewerten, indem sie den Text im Hinblick auf Lesbarkeit und Verständlichkeit analysieren.

**Mögliche Herangehensweisen**:
- **Readability auf Ausgangstext**: Bewertung der Lesbarkeit des Ausgangstextes im Vergleich zur Übersetzung.
- **Einfache Texte besser übersetzt als schwierigere?**: Vergleich der Übersetzungsqualität bei unterschiedlichen Textschwierigkeiten.
- **Lesbarkeit über Sprachen hinweg vergleichbar?**: Untersuchung, ob die Lesbarkeit zwischen verschiedenen Sprachen vergleichbar ist.
- **Zurückübersetzungen**: Überprüfung, ob der übersetzte Text bei einer Rückübersetzung zum Originaltext zurückkehrt.
- **Einzelne Wörter und Überschriften**: Detaillierte Bewertung der Übersetzung einzelner Wörter und Überschriften.

**Metriken**:


| Metrik | Definition | Vorteile | Nachteile |
|--------|------------|----------|-----------|
| **BERT** | Bewertet die Qualität von Texten durch Kontextualisierung und semantische Einbettungen. | Kontextbewusste Bewertung, gute Performance bei Textanalysen | Hoher Rechenaufwand, nicht immer intuitiv interpretierbare Ergebnisse |
| **GPT** | Nutzt generative Fähigkeiten zur Bewertung der Qualität und Kreativität von Texten. | Hohe Qualität der generierten Texte, nützlich für kreative und kontextreiche Bewertungen | Kostspielig, benötigt umfangreiche Rechenressourcen |

<br/>

## Textstat

Die Library <a href="https://pypi.org/project/textstat/">Textstat</a> ist ein Python-Paket zur Analyse und Berechnung von Textstatistiken, das besonders auf die Lesbarkeit von Texten abzielt. Es bietet Funktionen zur Berechnung von Metriken wie dem Flesch-Kincaid-Index, der Gunning-Fog-Skala und der Coleman-Liau-Index, um die Verständlichkeit und Komplexität von Texten zu bewerten. Textstat ist einfach zu bedienen und nützlich für Anwendungen in der Textverarbeitung, beim Schreiben von klarer Sprache und beim Bildungsbereich.

Es gibt folgende Möglichkeiten zu Bewertung der Readability:


| Score                            | Geeignet für                          | Fokus                              | Herangehensweise                                                         |
|----------------------------------|---------------------------------------|------------------------------------|--------------------------------------------------------------------------|
| Dale-Chall Readability Formula   | Allgemeine Leserschaft                | Wortvertrautheit                   | Verwendet eine Liste vertrauter Wörter zur Bewertung der Schwierigkeit   |
| Spache Readability Formula       | Primarschultexte                      | Wortfrequenz und Satzlänge         | Gut für niedrigere Schulstufen geeignet                                  |
| SMOG Readability Formula         | Allgemeine Geschäftsdokumente         | Grammatik, Syntax und Wortwahl     | Bezieht grammatische Schwierigkeit ein                                   |
| Flesch Reading Ease              | Breites Spektrum, einschließlich Bildungstexte | Satzlänge und Wortsilben  | Liefert einen Wert, der die Lesbarkeit angibt                            |
| Gunning Fog Index                | Geschäfts- und Fachtexte              | Wortkomplexität und Satzlänge      | Ideal zur Analyse von Materialien der Oberstufe                          |
| Fry Graph                        | Bildungstexte und Dokumente           | Satz- und Silbenzählung pro 100 Wörter | Visuelles Werkzeug zur Bewertung der Lesbarkeit                      |
| Coleman-Liau Readability Formula | Notenstufenbewertung                  | Zeichenzählung                     | Fokussiert auf Zeichen anstelle von Silben zur Einschätzung der Lesbarkeit |
| McAlpine EFLAW                   | Englisch als Fremdsprache             | Wortvertrautheit und Struktur      | Entwickelt für nicht-muttersprachliche Englischlerner                    |
| Automated Readability Index (ARI)| Allgemeine Leserschaft                | Zeichen pro Wort und Wörter pro Satz | Liefert eine Notenstufenbewertung für Lesbarkeit                       |
| Flesch-Kincaid                   | Breites Spektrum, einschließlich militärischer Dokumente | Satzlänge und Silbenzahl   | Häufig im US-amerikanischen Bildungssystem verwendet          |
| FORCAST                          | Militär- und technische Handbücher    | Häufigkeit einsilbiger Wörter      | Entwickelt für nicht-narrative Materialien                               |
| Linsear Write                    | Englische Texte für Nicht-Muttersprachler | Satz- und Wortlänge            | Einfaches Berechnungsverfahren                                           |
| Raygor Estimate Graph            | Breites Spektrum, einschließlich Lehrbücher | Satzlänge und Wortanzahl     | Bietet eine visuelle Lesbarkeitsschätzung                                |
| Laesbarhedsindex (LIX)           | Schwedische Texte                     | Wort- und Satzlänge                | Berechnet die Lesbarkeit für schwedische Texte                           |
