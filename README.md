# Jira-Postman-tests_
<br>

## Opis projektu

Celem projektu jest praktyczna nauka testowania API na przykładzie Jira Cloud REST API. <br>

<br>

## Technologie
- **Jira Cloud REST API** 
- **Postman** 

<br>

## Dokumentacja 

- [Dokumentacja Jira Cloud REST API](https://developer.atlassian.com/cloud/jira/platform/rest/v2/intro/)
- [Postman – oficjalna strona](https://www.postman.com/)
<br>

## Przypadki testowe

Poniżej znajduje się pełna lista przypadków testowych realizowanych w projekcie. Każdy przypadek zawiera opis, kroki oraz oczekiwany rezultat.
<br>

### 1. Pobranie mojego accountId (GET)

**Opis:**  
Sprawdzenie, czy użytkownik może pobrać swój własny accountId przez API Jira.

**Kroki:**  
- Wysłanie żądania GET na endpoint `/rest/api/2/myself`.

**Oczekiwany rezultat:**  
- Status odpowiedzi 200 (OK).
- Odpowiedź zawiera pole `accountId`.


<br>

### 2. Utworzenie projektu (POST Create Project)

**Opis:**  
Weryfikacja możliwości utworzenia nowego projektu w Jira przez API.

**Kroki:**  
- Wysłanie żądania POST na endpoint `/rest/api/2/project` z wymaganym body (`key`, `projectTypeKey`, `lead`).

**Oczekiwany rezultat:**  
- Status odpowiedzi 201 (Created).
- Odpowiedź zawiera dane nowego projektu (`id`, `key`, `name`).


<br>

### 3. Utworzenie zadania (POST Create Issue)

**Opis:**  
Sprawdzenie, czy można utworzyć nowe zadanie w wybranym projekcie Jira.

**Kroki:**  
- Wysłanie żądania POST na endpoint `/rest/api/2/issue` z wymaganym body (`fields.project.key`, `fields.summary`, `fields.issuetype.id`).

**Oczekiwany rezultat:**  
- Status odpowiedzi 201 (Created).
- Odpowiedź zawiera klucz i id nowego zadania.


<br>

### 4. Aktualizacja zadania (PUT Update Issue)

**Opis:**  
Weryfikacja możliwości aktualizacji danych istniejącego zadania.

**Kroki:**  
- Wysłanie żądania PUT na endpoint `/rest/api/2/issue/{issueIdOrKey}` z nowymi wartościami (np. `fields.summary`).

**Oczekiwany rezultat:**  
- Status odpowiedzi 204 (No Content).
- Po pobraniu zadania wartości są zaktualizowane.

<br>

### 5. Utworzenie filtra (POST Create Filter)

**Opis:**  
Sprawdzenie, czy można utworzyć nowy filtr wyszukiwania w Jira.

**Kroki:**  
- Wysłanie żądania POST na endpoint `/rest/api/2/filter` z wymaganym body (`name`, `jql`).

**Oczekiwany rezultat:**  
- Status odpowiedzi 201 (Created).
- Odpowiedź zawiera id i nazwę nowego filtra.

<br>

### 6. Aktualizacja filtra (PUT Update Filter)

**Opis:**  
Weryfikacja możliwości aktualizacji istniejącego filtra.

**Kroki:**  
- Wysłanie żądania PUT na endpoint `/rest/api/2/filter/{id}` z nowymi wartościami (np. `name`, `jql`).

**Oczekiwany rezultat:**  
- Status odpowiedzi 200 (OK).
- Odpowiedź zawiera zaktualizowane dane filtra.


<br>

### 7. Dodanie komentarza do zadania (POST Add Comment to Issue)

**Opis:**  
Test sprawdza, czy użytkownik może dodać komentarz do istniejącego zadania.

**Kroki:**  
- Wysłanie żądania POST na endpoint `/rest/api/2/issue/{issueIdOrKey}/comment` z treścią komentarza w body.

**Oczekiwany rezultat:**  
- Status odpowiedzi 201 (Created).
- Odpowiedź zawiera treść i identyfikator nowego komentarza.

<br>

### 8. Przypisanie użytkownika do zadania (PUT Assign User to Issue)

**Opis:**  
Test sprawdza, czy można przypisać wybranego użytkownika do zadania.

**Kroki:**  
- Wysłanie żądania PUT na endpoint `/rest/api/2/issue/{issueIdOrKey}/assignee` z accountId użytkownika w body.

**Oczekiwany rezultat:**  
- Status odpowiedzi 204 (No Content).
- Pole `assignee` w zadaniu jest zaktualizowane na wskazanego użytkownika.

<br>

### 9. Aktualizacja priorytetu zadania (PUT Update Issue Priority)

**Opis:**  
Test sprawdza, czy można zaktualizować priorytet istniejącego zadania.

**Kroki:**  
- Wysłanie żądania PUT na endpoint `/rest/api/2/issue/{issueIdOrKey}` z polem `priority` w body.

**Oczekiwany rezultat:**  
- Status odpowiedzi 204 (No Content).
- Po pobraniu zadania pole `priority` jest zaktualizowane.


<br>

### 10. Usunięcie zadania (DELETE Issue)

**Opis:**  
Test sprawdza, czy można usunąć istniejące zadanie przez API.

**Kroki:**  
- Wysłanie żądania DELETE na endpoint `/rest/api/2/issue/{issueIdOrKey}` z poprawnym identyfikatorem zadania.

**Oczekiwany rezultat:**  
- Status odpowiedzi 204 (No Content).
- Ponowna próba pobrania usuniętego zadania zwraca status 404 (Not Found).

<br>
