
Jesteś asystentem AI, którego zadaniem jest podsumowanie rozmowy na temat planowania PRD (Product Requirements Document) dla MVP i przygotowanie zwięzłego podsumowania dla następnego etapu rozwoju. W historii konwersacji znajdziesz następujące informacje:
1. Opis projektu
2. Zidentyfikowany problem użytkownika
3. Historia rozmów zawierająca pytania i odpowiedzi
4. Zalecenia dotyczące zawartości PRD

Twoim zadaniem jest:
1. Podsumować historię konwersacji, koncentrując się na wszystkich decyzjach związanych z planowaniem PRD.
2. Dopasowanie zaleceń modelu do odpowiedzi udzielonych w historii konwersacji. Zidentyfikuj, które zalecenia są istotne w oparciu o dyskusję.
3. Przygotuj szczegółowe podsumowanie rozmowy, które obejmuje:
   a. Główne wymagania funkcjonalne produktu
   b. Kluczowe historie użytkownika i ścieżki korzystania
   c. Ważne kryteria sukcesu i sposoby ich mierzenia
   d. Wszelkie nierozwiązane kwestie lub obszary wymagające dalszego wyjaśnienia
4. Sformatuj wyniki w następujący sposób:

<conversation_summary>
<decisions>
1.  **Model AI:** Aplikacja będzie korzystać z API GPT-4 do generowania fiszek.
2.  **Proces generowania:** Użytkownik wkleja tekst (do 500 znaków), z którego AI tworzy listę fiszek-kandydatów. Każdą z nich można indywidualnie zaakceptować, edytować lub odrzucić.
3.  **Format fiszki:** Fiszka składa się z pytania ("przód", max. 200 znaków) i odpowiedzi ("tył").
4.  **Zarządzanie fiszkami:** Zapewnione pełne operacje CRUD (tworzenie, przeglądanie, edycja, usuwanie) na fiszkach.
5.  **Organizacja (Zestawy):** Fiszki można organizować za pomocą tagów (nazywanych zestawami). Fiszka może mieć wiele tagów lub nie mieć ich wcale.
6.  **System powtórek (Spaced Repetition):** Zintegrowana zostanie gotowa biblioteka open-source.
7.  **Sesja nauki:** Użytkownik wybiera zestaw do nauki, ocenia swoją wiedzę ("wiedziałem" / "nie wiedziałem"), a także może wybrać kolejność wyświetlania fiszek.
8.  **Uwierzytelnianie:** Logowanie i rejestracja przez e-mail/hasło w oparciu o Supabase (szczegóły w osobnym dokumencie).
9.  **Eksport danych:** Użytkownik może wyeksportować swoje fiszki do pliku JSON. Struktura fiszki w JSON to: pytanie, odpowiedź i tablica ID zestawów.
10. **Paginacja:** Lista fiszek w zestawach będzie paginowana (20 na stronę).
11. **Obsługa błędów:** W przypadku błędu API AI wyświetlany będzie prosty, generyczny komunikat.
12. **Funkcjonalności poza MVP:** Świadomie zrezygnowano z analityki, metryk sukcesu, zbierania feedbacku, limitów użycia AI, zaawansowanego RODO, trybu offline i funkcji dostępności.
</decisions>

<matched_recommendations>
1.  **Kontrakt API:** Konieczne jest zdefiniowanie precyzyjnego kontraktu API (np. OpenAPI/Swagger) między frontendem a backendem, zwłaszcza dla funkcji generowania fiszek.
2.  **Projekt schematu bazy danych:** Należy zaprojektować schemat bazy danych, uwzględniając użytkowników, fiszki oraz tagi (zestawy) i relacje między nimi.
3.  **Ustanowienie strategii walidacji danych:** Należy zdefiniować i wdrożyć reguły walidacji dla danych wejściowych (np. limity znaków dla pytań i tekstu źródłowego).
4.  **Określenie logiki zarządzania zestawami:** Należy szczegółowo opisać historyjki użytkownika (user stories) dla tworzenia i przypisywania tagów (zestawów) do fiszek.
5.  **Zmapowanie stanów błędów interfejsu:** Należy przygotować listę potencjalnych błędów (API, sieć) i zdefiniować odpowiadające im komunikaty dla użytkownika.
</matched_recommendations>

<prd_planning_summary>
Na podstawie sesji planistycznej zdefiniowano wymagania dla MVP aplikacji do nauki z fiszkami. Głównym celem jest rozwiązanie problemu czasochłonnego tworzenia fiszek poprzez automatyzację tego procesu za pomocą AI.

**Główne wymagania funkcjonalne:**
- System uwierzytelniania użytkowników (email/hasło) oparty na Supabase.
- Funkcja generowania fiszek (pytanie/odpowiedź) z wklejonego przez użytkownika tekstu przy użyciu API GPT-4.
- Interfejs do przeglądania, edycji i akceptacji/odrzucenia fiszek wygenerowanych przez AI.
- Pełna obsługa manualnego tworzenia i zarządzania fiszkami (CRUD).
- Możliwość tagowania fiszek w celu ich grupowania w zestawy.
- Moduł do nauki oparty na integracji z zewnętrzną biblioteką open-source implementującą algorytm Spaced Repetition.
- Funkcja eksportu fiszek do formatu JSON.

**Kluczowe historie użytkownika:**
1.  Jako użytkownik, mogę założyć konto i zalogować się do aplikacji.
2.  Jako użytkownik, mogę wkleić fragment tekstu, aby AI wygenerowało dla mnie propozycje fiszek.
3.  Jako użytkownik, mogę przejrzeć każdą propozycję, edytować ją i zdecydować o jej dodaniu do mojej kolekcji.
4.  Jako użytkownik, mogę tworzyć i edytować własne fiszki od zera.
5.  Jako użytkownik, mogę tworzyć tagi i przypisywać je do fiszek, aby tworzyć zestawy do nauki.
6.  Jako użytkownik, mogę rozpocząć sesję nauki dla wybranego zestawu fiszek.
7.  Jako użytkownik, mogę pobrać wszystkie moje fiszki w postaci pliku JSON.

**Kryteria sukcesu:**
Dla wersji MVP kryterium sukcesu jest dostarczenie stabilnie działającej aplikacji realizującej powyższe funkcjonalności. Pierwotne metryki ilościowe (np. odsetek akceptacji fiszek AI) zostały odłożone na późniejszy etap rozwoju.
</prd_planning_summary>

<unresolved_issues>
1.  **Specyfikacja promptu AI:** Koncepcja "dobrze wycraftowanego promptu" jest ogólna. Należy stworzyć, przetestować i udokumentować jego dokładną treść i strukturę, aby zapewnić optymalną jakość generowanych fiszek.
2.  **Persystencja stanu algorytmu powtórek:** Decyzja o braku konieczności zapisywania stanu algorytmu w głównej bazie danych jest niejasna. Stan powtórek (np. interwały, daty następnych powtórek) musi być gdzieś trwale przechowywany dla każdego użytkownika i fiszki. Należy wyjaśnić, jak i gdzie te dane będą zapisywane.
3.  **Zależności od dokumentacji zewnętrznej:** Kluczowe informacje o stacku technologicznym, implementacji Supabase oraz wybranej bibliotece do powtórek znajdują się w osobnych dokumentach. Stanowią one krytyczną zależność i muszą być sfinalizowane.
</unresolved_issues>
</conversation_summary>

Końcowy wynik powinien zawierać tylko treść w formacie markdown. Upewnij się, że Twoje podsumowanie jest jasne, zwięzłe i zapewnia cenne informacje dla następnego etapu tworzenia PRD.