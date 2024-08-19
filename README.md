<a id="readme-top"></a>

<!-- PROJECT LOGO AND TITLE-->
<h1 align="center">
  <br>
  <a href="https://github.com/fmaag/MDZ_Usecase/tree/main"><img src="images/MD_Logo.png" alt="Markdownify" width="200"></a>
  <br>
  Evaluierung der Übersetzungsqualität
  <br>
</h1>
<h4 align="center">In Zusammenarbeit mit der <a href="https://www.nureg.de/" target="_blank">Nureg GmbH</a>.</h4>


<!-- LINKS -->
<p align="center">
  <a href="https://www.python.org/downloads/release/python-3100/"><img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"></a>
  <a href="https://jupyter.org/">
  <img src="https://img.shields.io/badge/Jupyter_Notebooks-5.7.2-yellowgreen?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter Notebooks Badge">
</a>


<!-- TABLE OF CONTENTS -->
<p align="center">
  <a href="#ziel-des-Projekts">Ziel</a> •
  <a href="#Environment-Varbiablen">Projektaufbau</a> •
  <a href="#Projektaufbau">Environment Variablen</a> •
  <a href="#erkenntnisse">Erkentnisse</a> •
  <a href="#contact">Contace</a> •
  <a href="#partner">Partner</a>
</p>



<br />

<!-- ZIEL DES PROJEKTS -->
<h1>Ziel des Projekts</h1>

Um eine verlässliche Bewertung zu gewährleisten, benötigen wir sowohl eine präzise Metrik, die eng mit menschlichen Urteilen korreliert, als auch eine Sammlung hochwertiger Referenzübersetzungen, um die Metrik zu validieren. Aus diesem Grund haben wir, das Mittelstand Digital Zentrum Franken, in Zusammenarbeit mit der Nureg GmbH aus Nürnberg, ein innovatives Digitalisierungsprojekt ins Leben gerufen. In diesem Projekt wurden verschiedene Metriken hinsichtlich ihrer Eignung zur Bewertung von Similarity und Readability untersucht. Die vielversprechendsten Metriken haben wir in dem Jupyter Notebook [Jupyter Notebook „Qualitätsprüfung“](https://github.com/Mittelstand-Digital-Zentrum-Franken/EvaluationOfTranslation/blob/main/Qualitaetspruefung.ipynb) zusammengefasst.


<br>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- AUFBAU DES PROJEKTS -->
<h1>Aufbau des Projekts</h1>

### Inhalt

1. Stringbasierte Metriken
    1. [BLEU](https://github.com/Mittelstand-Digital-Zentrum-Franken/EvaluationOfTranslation/blob/main/Research/BLEU.ipynb)
    2. [ChrF](https://github.com/Mittelstand-Digital-Zentrum-Franken/EvaluationOfTranslation/blob/main/Research/ChrF.ipynb)

2. Deep Learning basierte Metriken
    1. [Bert Score](https://github.com/Mittelstand-Digital-Zentrum-Franken/EvaluationOfTranslation/blob/main/Research/BertScore.ipynb)
    2. [mBert](https://github.com/Mittelstand-Digital-Zentrum-Franken/EvaluationOfTranslation/blob/main/Research/mBert.ipynb)
    3. [Comet](https://github.com/Mittelstand-Digital-Zentrum-Franken/EvaluationOfTranslation/blob/main/Research/Comet.ipynb)

3. Sprachmodell als Evaluator
    1. [Textstat mit BERT Embedding](https://github.com/Mittelstand-Digital-Zentrum-Franken/EvaluationOfTranslation/blob/main/Research/Textstat.ipynb)
    2. [GPT](https://github.com/Mittelstand-Digital-Zentrum-Franken/EvaluationOfTranslation/blob/main/Research/GPT.ipynb)



<br>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ENVIRONMENT VARIABLEN -->
<h1>Environment Variablen</h1>
Um die Qualitätsprüfung mithilfe von GPT von OPEN AI durchführen zu können muss der Open AI Key in einer Environment Variable lokal gespeichert werden. Der Key wir dann über den Python Code aufgerufen. Zum festlegen der Envorionment Variable wird folgendes Vorgehen vorgeschlagen:

<br>

1. Drücken Sie die `Windows-Taste` und geben Sie "CMD" ein
2. Wählen Sie die `CMD als Administrator ausführen` aus
3. Festlgen der Environment Variable

    ```
    setx OPENAI_KEY "VALUE"
    ```
4. Überprüfen der Environment Variable
    ```
    echo $env:OPENAI_KEY
    ```
5. Aufrufen der Environment Variable in Python
    ```
    meine_variable = os.getenv('OPENAI_KEY')

    if meine_variable is not None:
        print(f'Der Wert von MEINE_VARIABLE ist: {meine_variable}')
    else:
        print('Die Umgebungsvariable MEINE_VARIABLE ist nicht gesetzt.')
    ```

<br>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ERKENNTNISSE -->
<h1>Erkenntnisse</h1>

### Similarity


### Readability
Die <a href="https://readabilityformulas.com/how-to-decide-which-readability-formula-to-use/">Readability</a> spielt eine bedeutende Rolle.

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






Alle Unteruschung sind in dem JN "Textstat" zu finden.
In Qualitätsprüfung werden die passenden zusammengeführt.






<br>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
<h1>Contact</h1>

* <p align="left">
    <img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="LinkedIn" height="30" width="40"/>
  Vernetzt euch gerne mit uns auf <a href="https://linkedin.com/in/mittelstand-digital-zentrum-franken">LinkedIn</a>
</p>

* <p align="left">
    <img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="Instagram" height="30" width="40" />
  Folgt uns gerne auf <a href="https://instagram.com/mittelstand_digital_franken">Instagram</a> um keine Neuigkeiten mehr zu verpassen
</p>

* <p align="left">
    <img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/rss.svg" alt="Webside" height="30" width="40" />
  Alle neuen Infos, Projekte, Kurse und Blogbeiträge findet ihr auf unserer <a href="https://digitalzentrum-franken.de/">Webside</a>
</p>

* <p align="left">
    <img align="center" src="https://cdn-icons-png.flaticon.com/128/10804/10804813.png" alt="Mail" height="40" width="40" />
  Schreib uns eine Mail an <a href="mailto:info@digitalzentrum-franken.de">info@digitalzentrum-franken.de</a>
</p>

<br />
<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- PARTNER -->
<h1>Partner</h1>
<img src="images/Partner.png" alt="Logos">
<img src="images/Bundesministerium.png" alt="Logos">

<br />
<p align="right">(<a href="#readme-top">back to top</a>)</p>
