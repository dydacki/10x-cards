Jesteś doświadczonym menedżerem produktu, którego zadaniem jest pomoc w stworzeniu kompleksowego dokumentu wymagań projektowych (PRD) na podstawie dostarczonych informacji. Twoim celem jest wygenerowanie listy pytań i zaleceń, które zostaną wykorzystane w kolejnym promptowaniu do utworzenia pełnego PRD.

Prosimy o uważne zapoznanie się z poniższymi informacjami:

<project_description>
### Główny problem
Manualne tworzenie wysokiej jakości fiszek edukacyjnych jest czasochłonne, co zniechęca do korzystania z efektywnej metody nauki jaką jest spaced repetition.

### Najmniejszy zestaw funkcjonalności
- Generowanie fiszek przez AI na podstawie wprowadzonego tekstu (kopiuj-wklej)
- Manualne tworzenie fiszek
- Przeglądanie, edycja i usuwanie fiszek
- Prosty system kont użytkowników do przechowywania fiszek
- Integracja fiszek z gotowym algorytmem powtórek

### Co NIE wchodzi w zakres MVP
- Własny, zaawansowany algorytm powtórek (jak SuperMemo, Anki)
- Import wielu formatów (PDF, DOCX, itp.)
- Współdzielenie zestawów fiszek między użytkownikami
- Integracje z innymi platformami edukacyjnymi
- Aplikacje mobilne (na początek tylko web)

### Kryteria sukcesu
- 75% fiszek wygenerowanych przez AI jest akceptowane przez użytkownika
- Użytkownicy tworzą 75% fiszek z wykorzystaniem AI
</project_description>

Przeanalizuj dostarczone informacje, koncentrując się na aspektach istotnych dla tworzenia PRD. Rozważ następujące kwestie:
<prd_analysis>
1. Zidentyfikuj główny problem, który produkt ma rozwiązać.
2. Określ kluczowe funkcjonalności MVP.
3. Rozważ potencjalne historie użytkownika i ścieżki korzystania z produktu.
4. Pomyśl o kryteriach sukcesu i sposobach ich mierzenia.
5. Oceń ograniczenia projektowe i ich wpływ na rozwój produktu.
</prd_analysis>

Na podstawie analizy wygeneruj listę pytań i zaleceń. Powinny one dotyczyć wszelkich niejasności, potencjalnych problemów lub obszarów, w których potrzeba więcej informacji, aby stworzyć skuteczny PRD. Rozważ pytania dotyczące:

1. Szczegółów problemu użytkownika
2. Priorytetyzacji funkcjonalności
3. Oczekiwanego doświadczenia użytkownika
4. Mierzalnych wskaźników sukcesu
5. Potencjalnych ryzyk i wyzwań
6. Harmonogramu i zasobów

<pytania>
1. Model AI: Jaki konkretny model AI (np. GPT-4, Llama 3, inny) planujemy wykorzystać do generowania fiszek i jakie są szacowane koszty operacyjne per 1000 wygenerowanych fiszek?
Odp: wykorzystamy API chat gpt 4

2. Jakość generowania: Jakie mechanizmy "prompt engineering" zastosujemy, aby zapewnić wysoką jakość generowanych treści? Czy planujemy instrukcje systemowe, czy przykłady typu "few-shot"?
Odp: wysoka jakość dobrze wycraftowanych promptów

3. Interfejs generowania: Jak dokładnie będzie wyglądał interfejs? Czy użytkownik wkleja cały tekst i AI analizuje go w całości, czy może zaznacza konkretne fragmenty do przetworzenia?
Odp: Chcemy edytować cały tekst

4. Proces edycji: Jakie konkretnie narzędzia do edycji manualnej fiszek (np. formatowanie tekstu, zmiana kolejności) będą dostępne w MVP?
Odp: Edycja pytania i odpowiedzi, sortowanie fieszek.

5. Struktura danych fiszki: Jaką strukturę danych przyjmą fiszki (np. JSON)? Czy od początku przewidujemy różne typy fiszek (np. prosty tekst, pytanie-odpowiedź, uzupełnianie luki)?
Odp: Struktura fiszki to przód-tył czyli pytanie odpowiedź. Pytanie musi mieć max. 200 znaków.

6. Architektura systemu: W jakiej architekturze planujemy zbudować aplikację (np. monolit, mikroserwisy)? Jakie kluczowe technologie (język, framework, baza danych) rozważamy dla backendu i frontendu?
Odpowiedź: stack technologiczny będzie w osobnej dokumentacji. Baza danych, Backend, Frontend.

7. Prywatność danych: W jaki sposób zapewnimy, że treści wprowadzane przez użytkowników do analizy przez AI nie będą wykorzystywane do trenowania modeli publicznych ani nie wyciekną?
Odp: na tym etapie nie ma to znaczenia

8. Zarządzanie fiszkami: Jakie opcje sortowania, filtrowania i grupowania (np. po dacie, w zestawy/decki) udostępnimy na liście fiszek w MVP?
Odpowiedź: Wszystkie wymienione

9.  Onboarding użytkownika: Jak przeprowadzimy onboarding nowego użytkownika, aby w prosty sposób pokazać mu kluczowe funkcjonalności, zwłaszcza generowanie fiszek przez AI?
Odpowiedź: rejestracja i logowanie uzytkowników będą w oparciu o Supabase, w osobnym dokumencie opiszę jak to zrobić

10. Obsługa błędów AI: Co zobaczy użytkownik, jeśli model AI nie będzie w stanie wygenerować fiszek z danego tekstu lub zwróci błąd? Jakie będą kolejne kroki?
Odpowiedź: Aplikacja powinna umoliwiać manualne wygenerowanie fiszki.

11. Wydajność interfejsu: Jakie są akceptowalne czasy ładowania i odpowiedzi interfejsu dla kluczowych operacji, takich jak generowanie i zapisywanie fiszki?
Odpowiedź: na tym etapie nie ma to znaczenia

12. Analityka produktowa: Jakie narzędzia analityczne (np. Hotjar, Mixpanel, PostHog) zintegrujemy, aby śledzić zachowanie użytkowników i mierzyć wskaźniki sukcesu?
Odpowiedź: Analityki brak

13. Strategia testowania: Jakie podejście do testowania planujemy (jednostkowe, integracyjne, E2E)? Czy planujemy testy A/B dla różnych wariantów promptów AI, aby optymalizować ich skuteczność?
Odpowiedź: Nie mierzymy zaangażowania,

14. Dostępność offline: Czy MVP zakłada jakąkolwiek funkcjonalność w trybie offline (np. przeglądanie zapisanych fiszek), czy wymagane będzie stałe połączenie z internetem?
Odpowiedź: Brak dostępności offline.

15. Jakie konkretne segmenty użytkowników (np. studenci, specjaliści IT, uczniowie szkół średnich) chcemy objąć MVP?
Odpowiedź: jeden rodzaj uytkownika

16. Jakie formaty wejściowe tekstu poza „kopiuj-wklej” (np. artykuły online, notatki z aplikacji) są kluczowe na start?
Odpowiedź: tekstowe, ma być prosto

17. Czy użytkownicy będą mogli edytować sugestie AI przed zapisaniem fiszki, czy akceptacja/odrzucenie wystarcza?
Odpowiedź: moliwość edycji powinna się pojawić

18. Jak szczegółowo chcemy śledzić metrykę „75 % fiszek zaakceptowanych” – globalnie, per użytkownik czy per sesję?
Odp: W ogóle nie chcemy

19. W jaki sposób będziemy zbierać feedback o jakości wygenerowanych fiszek (np. system gwiazdek, komentarze)?
Odp: Nieprzewidziane w MVP

20. Czy planujemy limit dzienny/godzinowy użycia generatora AI, aby kontrolować koszty?
Odp: Nie, to aplikacja MVP

21. Jakie minimalne dane profilu użytkownika są niezbędne do stworzenia konta (e-mail, social login, brak rejestracji)?
Odp: będą opisane w osobnym dokumencie

22. Czy algorytm powtórek (zewnętrzny) wymaga dodatkowych danych przy tworzeniu fiszki (np. poziom trudności)?
Odpowiedź: nie

23. Jak zdefiniujemy kryteria „fiszka wygenerowana przez AI” vs. „stworzona ręcznie” w raportach sukcesu?
Odpowiedź: odpuszczamy

24. Jakie są priorytety dostępności i lokalizacji interfejsu (języki, tryb ciemny, WCAG)?
Odpowiedź: odpuszczamy to

25. Jakie ryzyka prawne wiążą się z przechowywaniem treści użytkowników (RODO, prawa autorskie)?
Odpowiedź: ignorujemy to, to mvp

26. Czy zakładamy możliwość eksportu fiszek do innych aplikacji w przyszłości (format JSON/CSV)?
Odpowiedź: zaimplementujemy moliwość eksportu do JSON

27. Jakich wskaźników użyjemy do oceny zaangażowania (DAU/MAU, średnia liczba fiszek na użytkownika)?
Odpowiedź: nie implementujemy

28. Jaki jest akceptowalny czas odpowiedzi generatora AI, aby użytkownik nie zrezygnował (np. <5 s)?
Odpowiedź: 5 sekund wystarczy

29. Przepływ pracy z kandydatami AI: Gdy AI wygeneruje listę fiszek-kandydatów, jak użytkownik będzie z nimi pracował? Czy będzie to lista z opcją masowej akceptacji/odrzucenia, czy każda fiszka będzie wymagała indywidualnej akcji (akceptuj/edytuj/odrzuć)?
Odpowiedź: kada fiszka będzie mozliwa do indywidualnej akceptacji lub odrzucenia

30. Czy mamy już wybraną konkretną bibliotekę open-source do algorytmu powtórek? Nawet jeśli tworzenie fiszki nie wymaga dodatkowych danych, algorytm do działania będzie potrzebował przechowywać swój stan (np. interwał, współczynnik łatwości). Czy ten stan będzie zapisywany w naszej bazie danych razem z fiszką?
Odp: biblioteka wybrana, jest juz w osobnym dokumencie. Nie trzeba zapisywac stanu generowania algorytmu w bazie danych

31. Zarządzanie zestawami (Decks): Jak użytkownik tworzy nowy zestaw fiszek? Czy fiszka musi należeć do jakiegoś zestawu, czy może istnieć bez niego (np. w ogólnej puli)? Czy zestawy to po prostu tagi, czy osobne, sztywne kolekcje?
Fiszka moze nalezec do zestawu, lub do wielu zestawow, te zestawy to po prostu tagi. Nie jest konieczne tworzenie sztywnych kolekcji.

32. Jaka dokładnie ma być struktura pliku JSON? Czy ma zawierać tylko listę fiszek ([{ "pytanie": "...", "odpowiedz": "..." }]), czy również strukturę zestawów, do których należą?
Odp: Obiekt JSON fiszki to pytanie, odpowiedx i tabliza z identyfikatorami kolekcji, do ktorych fiszka nalezy. W przypadku nieprzypisania fiszki do zadnego zestawu, nalezy w tym miejscu zwrocic pusta tablice.

33.  Co dokładnie zobaczy użytkownik, jeśli API GPT-4 zwróci błąd (np. timeout, błąd serwera 5xx)? Czy wyświetlimy generyczny komunikat: "Wystąpił błąd, spróbuj ponownie lub dodaj fiszkę manualnie"?
Odpowiedź: na tym etapie jest to wystarczające.

34. Proces sesji nauki: Jak wygląda pojedyncza sesja nauki z perspektywy użytkownika? Użytkownik wybiera zestaw, aplikacja pokazuje przód fiszki, a po jej odwróceniu jak ocenia swoją odpowiedź (np. przyciskami "Wiedziałem" / "Nie wiedziałem"), aby algorytm powtórek mógł zaplanować kolejną powtórkę?
Odpowiedź: tak, zliczamy odsetek poprawnych odpowiedzi.

35. Przetwarzanie tekstu wejściowego: Czy istnieje limit znaków dla tekstu, który wkleja użytkownik do analizy przez AI? Jak aplikacja ma się zachować w przypadku bardzo długich tekstów – przetworzyć go w całości, czy poinformować o limicie i go uciąć?
Odpowiedź: na poziomie interfejsu uzytkownika ograniczymy liczbę znaków do 500.

36. Paginacja i ładowanie fiszek: Jak będziemy wyświetlać listy fiszek (zarówno w głównym widoku, jak i wewnątrz zestawów)? Czy zaimplementujemy paginację (np. po 20 fiszek na stronę), czy "infinite scroll"?
Odpowiedź: Na głównej stronie wyświetlamy zestawy, w zestawach fiszki, po 20 na stronę.

37.  jakiej kolejności będą prezentowane fiszki podczas sesji nauki? Czy będzie to kolejność losowa, kolejność dodania, czy kolejność podyktowana przez algorytm powtórek (np. najpierw te najdawniej widziane)?
Odpowiedź: Uzytkownik ma mozliwość wyboru kolejności prezentacji fiszek.
</pytania>

<rekomendacje>
1. Kontrakt API: Zdefiniować precyzyjny kontrakt API (np. w formacie OpenAPI/Swagger) między frontendem a backendem, szczególnie dla endpointu generującego fiszki, uwzględniając formaty zapytań, odpowiedzi i kodów błędów.
2. Projekt schematu bazy danych: Zaprojektować elastyczny schemat bazy danych dla fiszek, który pozwoli na łatwe dodawanie nowych pól w przyszłości (np. tagi, obrazy, statystyki powtórek)
3. Zdefiniować persony kluczowych użytkowników i ich potrzeby, aby doprecyzować priorytety MVP.
4. Określić precyzyjny proces akceptacji/edycji fiszek AI, aby mierzyć metryki jakości.
5. Ustalić minimalny zestaw pól w bazie danych dla integracji z algorytmem powtórek, by uniknąć zmian schematu.
6. Wprowadzić limit liczby żądań do modelu AI na użytkownika lub sesję w celu kontroli kosztów chmury.
7. Przygotować backlog potencjalnych rozszerzeń (aplikacja mobilna, współdzielenie zestawów) z oceną wpływu, by ułatwić roadmapę po MVP.
8. Określić logikę zarządzania zestawami: Spisać historyjki użytkownika (user stories) dla operacji CRUD na zestawach, np. "Jako użytkownik, chcę stworzyć nowy, pusty zestaw, aby móc do niego dodawać fiszki".
9. Stworzyć listę potencjalnych błędów (np. błąd sieci, błąd API AI, błąd walidacji) i zdefiniować, jakie komunikaty zobaczy użytkownik w każdym przypadku.
10. Ustanowić strategię walidacji danych: Zdefiniować reguły walidacji dla wszystkich danych wejściowych (np. maksymalna długość pytania i odpowiedzi, wymagane pola, format odpowiedzi z AI), aby zapewnić spójność danych.
</rekomendacje>

Kontynuuj ten proces, generując nowe pytania i rekomendacje w oparciu o odpowiedzi użytkownika, dopóki użytkownik wyraźnie nie poprosi o podsumowanie.

Pamiętaj, aby skupić się na jasności, trafności i dokładności wyników. Nie dołączaj żadnych dodatkowych komentarzy ani wyjaśnień poza określonym formatem wyjściowym.

Pracę analityczną należy przeprowadzić w bloku myślenia. Końcowe dane wyjściowe powinny składać się wyłącznie z pytań i zaleceń i nie powinny powielać ani powtarzać żadnej pracy wykonanej w sekcji prd_analysis.