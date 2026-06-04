# allgeier-maven-selenium-allure

GUI-Automatisierungsprojekt mit Selenium WebDriver gegen die Login-Funktion von `https://the-internet.herokuapp.com`, ergänzt um Allure Reporting.

## Zweck im Assessment

Dieses Repository dient **P02 - GUI-Automatisierung** und **P04 - Testtools und Pipeline-Integration**. Es zeigt denselben Selenium-Testkern wie die Variante ohne Allure und ergänzt nur die Reporting-Schicht.

## Technischer Stack

| Komponente | Version |
|---|---|
| Selenium Java | 4.44.0 |
| JUnit Jupiter | 6.1.0 |
| Allure Jupiter | 2.35.1 |
| AspectJ Weaver | 1.9.25.1 |
| Java | 25 |
| Maven | 3.9+ |
| Reporting | Maven Surefire, Allure |

## Zielsystem

**URL:** https://the-internet.herokuapp.com

The Internet ist ein öffentliches, bewusst für UI-Automatisierung bereitgestelltes Testziel.

## Voraussetzungen

- JDK 25+
- Maven 3.9+
- Google Chrome
- Internetzugang

## Ausführen

```bash
mvn clean verify
```

Die Ziel-URL und Zugangsdaten liegen in `src/test/resources/config.properties`.

## Reports

Surefire-Ergebnisse liegen nach dem Lauf unter:

```text
target/surefire-reports/
```

Allure-Ergebnisse liegen unter:

```text
target/allure-results/
```

Allure-Report erzeugen:

```bash
mvn allure:report
```

Der HTML-Report liegt anschliessend unter:

```text
target/allure-report/index.html
```

## Projektstruktur

```text
src/test/java/ch/allgeier/maven/selenium/pages/   Selenium Page Objects
src/test/java/ch/allgeier/maven/selenium/tests/   JUnit-Tests
src/test/resources/                               Testkonfiguration
pom.xml                                           Maven- und Allure-Konfiguration
```

## Hinweise für das Assessment

Das Projekt enthält bewusst eingebaute Fehler. Kandidaten sollen das Fehlerbild analysieren, die Ursache finden und eine fachlich passende Korrektur umsetzen. Die Auflösung steht nicht in dieser README.
