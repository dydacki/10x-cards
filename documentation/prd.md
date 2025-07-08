# Dokument wymagań produktu (PRD) - AI Fiszki

## 1. Przegląd produktu
Celem projektu jest stworzenie aplikacji internetowej "AI Fiszki", która usprawnia proces nauki poprzez automatyczne generowanie fiszek edukacyjnych. Aplikacja wykorzystuje model AI (GPT-4) do analizy tekstu dostarczonego przez użytkownika i tworzenia na jego podstawie propozycji fiszek (pytanie-odpowiedź). Użytkownicy mogą zarządzać swoimi fiszkami, organizować je w zestawy (tagi) i korzystać z wbudowanego modułu nauki opartego na algorytmie powtarzania w czasie (Spaced Repetition). MVP koncentruje się na dostarczeniu kluczowych funkcjonalności w prostym i wydajnym interfejsie webowym.

## 2. Problem użytkownika
Manualne tworzenie wysokiej jakości fiszek edukacyjnych jest procesem czasochłonnym i monotonnym. Wielu potencjalnych użytkowników rezygnuje z tej efektywnej metody nauki z powodu bariery wejściowej, jaką jest konieczność samodzielnego przygotowywania materiałów. Aplikacja "AI Fiszki" ma na celu zniwelowanie tego problemu poprzez zautomatyzowanie i znaczne przyspieszenie procesu tworzenia fiszek.

## 3. Wymagania funkcjonalne
- *System uwierzytelniania:* Użytkownicy mogą tworzyć konta i logować się za pomocą adresu e-mail i hasła. Integracja będzie oparta o usługę Supabase.
- *Generowanie fiszek przez AI:* Aplikacja umożliwia wklejenie tekstu (do 500 znaków), na podstawie którego API GPT-4 generuje listę fiszek-kandydatów w formacie pytanie-odpowiedź.
- *Zarządzanie kandydatami AI:* Użytkownik może przejrzeć każdą wygenerowaną fiszkę, indywidualnie ją zaakceptować (dodając do swojej kolekcji), edytować przed akceptacją lub odrzucić.
- *Manualne zarządzanie fiszkami (CRUD):* Użytkownicy mają pełną kontrolę nad swoimi fiszkami, w tym możliwość ich ręcznego tworzenia, przeglądania, edycji i usuwania.
- *System zestawów (tagowanie):* Fiszki mogą być grupowane w zestawy. System ten jest zaimplementowany jako elastyczny mechanizm tagowania, gdzie jedna fiszka może należeć do wielu zestawów (posiadać wiele tagów) lub do żadnego.
- *Moduł nauki (Spaced Repetition):* Aplikacja integruje się z gotową biblioteką open-source implementującą algorytm powtórek w czasie, aby optymalizować proces nauki.
- *Sesja nauki:* Użytkownik może rozpocząć sesję nauki dla wybranego zestawu. W trakcie sesji ocenia swoją odpowiedź ("wiedziałem" / "nie wiedziałem"), co wpływa na kolejne powtórki. Użytkownik ma również możliwość wyboru kolejności prezentacji fiszek.
- *Eksport danych:* Użytkownik może wyeksportować wszystkie swoje fiszki do pliku w formacie JSON.
- *Paginacja:* Widok listy fiszek w ramach zestawu jest paginowany i wyświetla 20 fiszek na stronę.

## 4. Granice produktu
Następujące funkcjonalności są świadomie wyłączone z zakresu MVP:
- Zaawansowany, autorski algorytm powtórek (jak SuperMemo).
- Import plików w formatach innych niż czysty tekst (np. PDF, DOCX).
- Funkcje społecznościowe, takie jak współdzielenie zestawów fiszek.
- Integracje z zewnętrznymi platformami edukacyjnymi.
- Dedykowane aplikacje mobilne (projekt jest wyłącznie webowy).
- Zaawansowana analityka produktu i zbieranie feedbacku od użytkowników.
- Limity użycia API AI.
- Tryb offline.
- Zaawansowane funkcje dostępności (accessibility).

## 5. Historyjki użytkowników

### Uwierzytelnianie i Zarządzanie Kontem
- ID: US-001
- Tytuł: Rejestracja nowego użytkownika
- Opis: Jako nowy użytkownik, chcę móc założyć konto w aplikacji przy użyciu mojego adresu e-mail i hasła, aby móc zapisywać swoje fiszki.
- Kryteria akceptacji:
  1. Formularz rejestracji zawiera pola na adres e-mail i hasło.
  2. System waliduje poprawność formatu adresu e-mail.
  3. Hasło musi spełniać podstawowe wymogi bezpieczeństwa.
  4. Po pomyślnej rejestracji jestem automatycznie zalogowany i przekierowany do głównego panelu aplikacji.

- ID: US-002
- Tytuł: Logowanie do aplikacji
- Opis: Jako zarejestrowany użytkownik, chcę móc zalogować się na moje konto, aby uzyskać dostęp do moich fiszek.
- Kryteria akceptacji:
  1. Formularz logowania zawiera pola na adres e-mail i hasło.
  2. Po poprawnym wprowadzeniu danych jestem zalogowany i przekierowany do głównego panelu.
  3. W przypadku błędnych danych wyświetlany jest odpowiedni komunikat.

### Generowanie i Zarządzanie Fiszkami
- ID: US-003
- Tytuł: Generowanie propozycji fiszek z tekstu
- Opis: Jako użytkownik, chcę wkleić tekst w dedykowane pole i uruchomić proces generowania fiszek przez AI, aby szybko stworzyć materiały do nauki.
- Kryteria akceptacji:
  1. Na stronie znajduje się pole tekstowe (textarea) z limitem 500 znaków.
  2. Przycisk "Generuj fiszki" jest aktywny, gdy pole tekstowe zawiera tekst.
  3. Po kliknięciu przycisku system wysyła zapytanie do API AI i wyświetla wskaźnik ładowania.
  4. Po zakończeniu procesu, pod polem tekstowym pojawia się lista fiszek-kandydatów.
  5. W przypadku błędu API, wyświetlany jest komunikat "Wystąpił błąd, spróbuj ponownie lub dodaj fiszkę manualnie".

- ID: US-004
- Tytuł: Recenzja i akceptacja wygenerowanych fiszek
- Opis: Jako użytkownik, chcę przejrzeć listę propozycji od AI i zaakceptować te, które mi odpowiadają, aby dodać je do mojej kolekcji.
- Kryteria akceptacji:
  1. Każda propozycja na liście ma widoczne pytanie i odpowiedź.
  2. Przy każdej propozycji znajduje się przycisk "Akceptuj".
  3. Kliknięcie "Akceptuj" powoduje zapisanie fiszki w mojej kolekcji i usunięcie jej z listy kandydatów.

- ID: US-005
- Tytuł: Odrzucenie wygenerowanej fiszki
- Opis: Jako użytkownik, chcę mieć możliwość odrzucenia propozycji fiszki od AI, jeśli jest ona niepoprawna lub nieprzydatna.
- Kryteria akceptacji:
  1. Przy każdej propozycji znajduje się przycisk "Odrzuć".
  2. Kliknięcie "Odrzuć" usuwa fiszkę z listy kandydatów bez zapisywania jej.

- ID: US-006
- Tytuł: Edycja propozycji fiszki przed akceptacją
- Opis: Jako użytkownik, chcę móc edytować treść pytania lub odpowiedzi w propozycji od AI przed jej zaakceptowaniem, aby dostosować ją do swoich potrzeb.
- Kryteria akceptacji:
  1. Przy każdej propozycji znajduje się przycisk "Edytuj".
  2. Kliknięcie "Edytuj" zamienia tekst pytania i odpowiedzi w edytowalne pola.
  3. Po edycji mogę zapisać zmiany i zaakceptować fiszkę w nowej formie.
  4. Pytanie po edycji nie może przekraczać 200 znaków.

- ID: US-007
- Tytuł: Manualne tworzenie nowej fiszki
- Opis: Jako użytkownik, chcę mieć możliwość ręcznego dodania nowej fiszki, wpisując własne pytanie i odpowiedź.
- Kryteria akceptacji:
  1. Istnieje dedykowany formularz do tworzenia fiszek z polami na pytanie (od 200 do 5000 znaków) i odpowiedź.
  2. Po wypełnieniu formularza i kliknięciu "Zapisz", nowa fiszka jest dodawana do mojej kolekcji.

- ID: US-008
- Tytuł: Edycja istniejącej fiszki
- Opis: Jako użytkownik, chcę móc edytować treść moich wcześniej zapisanych fiszek.
- Kryteria akceptacji:
  1. Na liście moich fiszek każda pozycja ma opcję "Edytuj".
  2. Po kliknięciu edycji mogę zmienić treść pytania i odpowiedzi, a następnie zapisać zmiany.

- ID: US-009
- Tytuł: Usuwanie istniejącej fiszki
- Opis: Jako użytkownik, chcę móc trwale usunąć fiszkę z mojej kolekcji.
- Kryteria akceptacji:
  1. Na liście moich fiszek każda pozycja ma opcję "Usuń".
  2. System prosi o potwierdzenie operacji usunięcia.
  3. Po potwierdzeniu fiszka jest trwale usuwana z bazy danych.

### Organizacja i Nauka
- ID: US-010
- Tytuł: Zarządzanie zestawami (tagami)
- Opis: Jako użytkownik, chcę móc przypisywać i usuwać tagi (zestawy) do moich fiszek, aby je kategoryzować.
- Kryteria akceptacji:
  1. Podczas edycji fiszki mogę dodać nowy tag lub wybrać istniejący z listy.
  2. Mogę usunąć tag przypisany do fiszki.
  3. Fiszka może mieć wiele tagów.

- ID: US-011
- Tytuł: Przeglądanie zestawów
- Opis: Jako użytkownik, chcę widzieć listę wszystkich moich zestawów (tagów), aby móc wybrać jeden z nich do nauki.
- Kryteria akceptacji:
  1. Na głównej stronie aplikacji wyświetlana jest lista unikalnych tagów.
  2. Kliknięcie na tag przenosi mnie do widoku listy fiszek w tym zestawie.

- ID: US-012
- Tytuł: Rozpoczynanie sesji nauki
- Opis: Jako użytkownik, chcę móc rozpocząć sesję nauki dla wybranego zestawu fiszek.
- Kryteria akceptacji:
  1. W widoku zestawu znajduje się przycisk "Rozpocznij naukę".
  2. Po kliknięciu uruchamiany jest interfejs sesji nauki, prezentujący pierwszą fiszkę (stronę z pytaniem).

- ID: US-013
- Tytuł: Przeprowadzanie sesji nauki
- Opis: Jako użytkownik, chcę w trakcie sesji nauki odkrywać odpowiedzi i oceniać swoją wiedzę.
- Kryteria akceptacji:
  1. Po wyświetleniu pytania mogę kliknąć przycisk, aby zobaczyć odpowiedź.
  2. Po odkryciu odpowiedzi mam do wyboru przyciski "Wiedziałem" i "Nie wiedziałem".
  3. Mój wybór jest zapisywany, a system prezentuje kolejną fiszkę zgodnie z logiką algorytmu powtórek.

### Funkcje dodatkowe

## 6. Metryki sukcesu
Dla wersji MVP głównym kryterium sukcesu jest pomyślne wdrożenie i stabilne działanie aplikacji oferującej wszystkie wymienione w tym dokumencie funkcjonalności. Celem jest dostarczenie działającego produktu, który rozwiązuje podstawowy problem użytkownika. Ilościowe metryki biznesowe i produktowe (np. retencja, wskaźniki adopcji AI) nie są częścią zakresu MVP i będą zdefiniowane w kolejnych iteracjach. 