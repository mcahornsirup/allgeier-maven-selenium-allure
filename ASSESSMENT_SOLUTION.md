# Assessment-Lösung: allgeier-maven-selenium-allure

> **ACHTUNG:** Diese Datei ist ausschließlich für Prüfer bestimmt und darf nicht an Kandidaten weitergegeben werden.

## Eingebaute Fehler

### Bug 1 – Fehlerhafter Selektor im Page Object

**Datei:** `src/test/java/ch/allgeier/maven/selenium/pages/LoginPage.java`
**Zeile:** `@FindBy(id = "flash-container")`

**Fehlerbild:**
Beide Tests (`testSuccessfulLogin` und `testInvalidLogin`) schlagen mit `NoSuchElementException` fehl, da die Flash-Nachricht nicht gefunden werden kann.
```
org.openqa.selenium.NoSuchElementException: no such element: Unable to locate element: {"method":"css selector","selector":"[id="flash-container"]"}
```

**Ursache:** Die tatsächliche ID des Flash-Elements lautet `flash`, nicht `flash-container`.

**Korrektur:** `@FindBy(id = "flash-container")` → `@FindBy(id = "flash")`

**Erwartetes Verhalten nach Korrektur:** `testSuccessfulLogin` besteht; `testInvalidLogin` schlägt wegen Bug 2 weiter fehl.

---

### Bug 2 – Falsche erwartete Zeichenkette in Assertion

**Datei:** `src/test/java/ch/allgeier/maven/selenium/tests/LoginTest.java`
**Zeile:** `assertTrue(flash.contains("Invalid credentials"), ...)`

**Fehlerbild:**
`testInvalidLogin` schlägt mit `AssertionError` fehl (nach Behebung von Bug 1):
```
AssertionError: Flash-Nachricht soll Fehlermeldung enthalten, war: Your username is invalid! ×
expected: <true> but was: <false>
```

**Ursache:** Die tatsächliche Fehlermeldung lautet "Your username is invalid!", nicht "Invalid credentials".

**Korrektur:** `flash.contains("Invalid credentials")` → `flash.contains("Your username is invalid!")`

**Erwartetes Verhalten nach Korrektur:** Beide Tests bestehen.
