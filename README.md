# codziennik
# Codziennik – aplikacja do monitorowania codziennych nawyków

## Opis projektu

Celem projektu jest stworzenie aplikacji internetowej umożliwiającej użytkownikom tworzenie, organizowanie oraz monitorowanie codziennych nawyków.

Aplikacja ma wspierać użytkowników w budowaniu systematyczności, utrzymywaniu dobrych przyzwyczajeń oraz analizowaniu postępów w realizacji wyznaczonych celów.

System powinien umożliwiać definiowanie nawyków o różnej częstotliwości, rejestrowanie ich wykonania oraz prezentowanie historii i statystyk aktywności.

## 1. Wymagania funkcjonalne

### 1.1. Zarządzanie kontem użytkownika

- Rejestracja i logowanie użytkowników.
- Edytowanie podstawowych danych profilu.
- Zmiana hasła.
- Wyświetlanie indywidualnego panelu użytkownika.
- Zapewnienie dostępu wyłącznie do własnych nawyków i statystyk.

### 1.2. Zarządzanie nawykami

- Dodawanie, edytowanie i usuwanie nawyków.
- Definiowanie parametrów nawyku:
  - nazwa,
  - opis,
  - kategoria,
  - data rozpoczęcia,
  - częstotliwość realizacji,
  - opcjonalna data zakończenia.
- Określanie harmonogramu realizacji:
  - codziennie,
  - w wybrane dni tygodnia,
  - określoną liczbę razy w tygodniu.
- Przypisywanie nawyków do kategorii, np. zdrowie, sport, nauka, rozwój osobisty.
- Wstrzymywanie i ponowne aktywowanie nawyków.
- Archiwizowanie zakończonych nawyków.
- Filtrowanie i sortowanie nawyków według kategorii, statusu i częstotliwości.

### 1.3. Codzienna realizacja nawyków

- Wyświetlanie listy nawyków zaplanowanych na bieżący dzień.
- Oznaczanie nawyków jako wykonanych.
- Cofanie oznaczenia wykonania nawyku.
- Prezentowanie nawyków zrealizowanych i oczekujących na wykonanie.
- Wyświetlanie dziennego podsumowania aktywności.
- Zapisywanie daty realizacji każdego nawyku.
- Możliwość uzupełniania historii wykonania nawyków za wcześniejsze dni.

### 1.4. Kalendarz aktywności

- Wyświetlanie kalendarza w widoku miesięcznym.
- Oznaczanie dni, w których użytkownik zrealizował zaplanowane nawyki.
- Przeglądanie szczegółów aktywności dla wybranego dnia.
- Przechodzenie pomiędzy miesiącami.
- Prezentowanie historii realizacji wybranego nawyku.

### 1.5. Statystyki i analiza postępów

- Wyświetlanie liczby wykonanych nawyków w wybranym okresie.
- Obliczanie procentowej skuteczności realizacji nawyków.
- Prezentowanie statystyk tygodniowych i miesięcznych.
- Wyznaczanie aktualnej oraz najdłuższej serii regularnych realizacji (*streak*).
- Prezentowanie postępów za pomocą wykresów.
- Porównywanie skuteczności realizacji nawyków w różnych okresach.
- Wyświetlanie podsumowania aktywności według kategorii.

## 2. Wymagania dotyczące monitorowania nawyków

System powinien zapewniać prawidłową obsługę harmonogramów oraz historii realizacji nawyków.

- Każdy nawyk należy do konkretnego użytkownika.
- Jeden nawyk może zostać oznaczony jako wykonany tylko raz dla danego dnia.
- Nawyki powinny pojawiać się na liście dziennej zgodnie ze zdefiniowanym harmonogramem.
- Zmiana statusu wykonania nawyku powinna aktualizować odpowiednie statystyki.
- Zmiana harmonogramu nie powinna powodować utraty zapisanej historii realizacji.
- Nawyki zarchiwizowane nie powinny pojawiać się na bieżącej liście zadań, ale ich historia powinna pozostać dostępna.
- System powinien rozróżniać dni, w których nawyk był zaplanowany, od dni, w których nie wymagał realizacji.
- Skuteczność realizacji nawyku powinna być obliczana jako stosunek liczby wykonanych realizacji do liczby wymaganych realizacji w analizowanym okresie.
- Sposób obliczania serii powinien uwzględniać harmonogram nawyku. Dni, w których wykonanie nie było wymagane, nie powinny automatycznie przerywać serii.
- Dla nawyków realizowanych określoną liczbę razy w tygodniu system powinien oceniać wykonanie celu tygodniowego, a nie wymagać aktywności każdego dnia.

## 3. Proponowany model danych

Przykładowe encje:

| Encja | Opis |
|---|---|
| `User` | Dane użytkowników i informacje potrzebne do uwierzytelniania |
| `Habit` | Definicje nawyków, ich nazwy, opisy i statusy |
| `Category` | Kategorie służące do grupowania nawyków |
| `HabitSchedule` | Harmonogramy i częstotliwości realizacji nawyków |
| `HabitCompletion` | Historia wykonania nawyków wraz z datami |
| `HabitScheduleHistory` | Historia zmian harmonogramów, umożliwiająca prawidłowe obliczanie statystyk |

Model danych może zostać rozszerzony w zależności od przyjętej architektury aplikacji.

## 4. Funkcjonalności dodatkowe

Funkcjonalności przeznaczone do realizacji po ukończeniu podstawowej wersji aplikacji:

- **Przypomnienia** – automatyczne powiadomienia o nawykach zaplanowanych na dany dzień.
- **Cele ilościowe** – definiowanie nawyków wymagających osiągnięcia określonej wartości, np. wypicie 2 litrów wody lub przeczytanie 20 stron książki.
- **System osiągnięć** – przyznawanie odznak za regularność i osiągnięcie określonych celów.
- **Wizualizacja aktywności** – prezentacja historii realizacji w postaci mapy aktywności (*heatmap*), podobnej do kalendarza aktywności GitHub.
- **Eksport danych** – pobieranie historii nawyków i statystyk w formacie CSV.
- **Wyzwania** – definiowanie celów czasowych, np. realizacja nawyku przez 30 dni.
- **Notatki** – dodawanie komentarzy do poszczególnych realizacji nawyków.
- **Personalizacja** – wybór motywu kolorystycznego, ikon oraz kolejności wyświetlania nawyków.
- **Panel administratora** – zarządzanie użytkownikami i podgląd zbiorczych statystyk działania systemu.

## 5. Wymagania techniczne

- Aplikacja internetowa z responsywnym interfejsem użytkownika.
- Relacyjna baza danych.
- Mechanizm rejestracji i uwierzytelniania użytkowników.
- Kontrola dostępu do danych należących do poszczególnych użytkowników.
- Walidacja danych po stronie serwera.
- Obsługa operacji CRUD dla nawyków i kategorii.
- Obsługa dat, harmonogramów oraz historii realizacji.
- Automatyczne obliczanie statystyk na podstawie zapisanych danych.
- Prezentowanie danych statystycznych w formie wykresów.
- Bezpieczne przechowywanie haseł.
- Obsługa błędów i odpowiednie komunikaty dla użytkownika.
- Testy wybranych elementów logiki biznesowej, w szczególności obliczania regularności i skuteczności realizacji nawyków.
- Dokumentacja instalacji i uruchomienia aplikacji.

## 6. Oczekiwany rezultat

Rezultatem projektu powinna być działająca aplikacja internetowa, w której:

1. Użytkownik może utworzyć konto i zalogować się do systemu.
2. Może dodawać własne nawyki, przypisywać je do kategorii i określać harmonogram realizacji.
3. Każdego dnia widzi listę zaplanowanych nawyków i może oznaczać je jako wykonane.
4. Może przeglądać historię aktywności w kalendarzu.
5. System automatycznie oblicza statystyki realizacji nawyków.
6. Użytkownik może analizować swoją regularność, skuteczność oraz długość serii realizacji.
7. Może archiwizować nieaktualne nawyki bez utraty historii ich wykonania.

**Najważniejszym elementem projektu jest poprawne zaimplementowanie mechanizmu harmonogramowania i rejestrowania realizacji nawyków oraz obliczania statystyk, uwzględniającego różne częstotliwości wykonywania czynności.**


# Codziennik – struktura bazy danych

Proponowany model relacyjnej bazy danych dla aplikacji **Codziennik – aplikacja do monitorowania codziennych nawyków**.

Przyjęto następujące założenia:

- Klucze główne `id` mają typ `BIGINT`.
- Klucze obce oznaczono jako `FK`.
- Pola `created_at` i `updated_at` przechowują daty utworzenia i modyfikacji rekordów.
- Pola opcjonalne mogą przyjmować wartość `NULL`.
- Daty przechowywane są jako `DATE`, a znaczniki czasu jako `TIMESTAMP`.
- Nazwy tabel i kolumn zapisano w konwencji `snake_case`.
- Statystyki obliczane są na podstawie historii realizacji i harmonogramów, bez konieczności przechowywania ich w osobnej tabeli.

# 1. Tabele podstawowe

## 1.1. `user` – użytkownicy

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator użytkownika |
| `email` | VARCHAR(180), UNIQUE | Adres e-mail |
| `password_hash` | VARCHAR(255) | Hash hasła |
| `first_name` | VARCHAR(100) | Imię |
| `last_name` | VARCHAR(100) | Nazwisko |
| `roles` | JSON | Role użytkownika |
| `timezone` | VARCHAR(50) | Strefa czasowa, np. Europe/Warsaw |
| `is_active` | BOOLEAN | Czy konto jest aktywne |
| `created_at` | TIMESTAMP | Data rejestracji |
| `updated_at` | TIMESTAMP | Data aktualizacji |

## 1.2. `category` – kategorie nawyków

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator kategorii |
| `user_id` | BIGINT, FK, NULL | Właściciel kategorii; NULL dla kategorii systemowej |
| `name` | VARCHAR(100) | Nazwa kategorii |
| `description` | TEXT, NULL | Opis kategorii |
| `color` | VARCHAR(7), NULL | Kolor w formacie HEX |
| `icon` | VARCHAR(50), NULL | Nazwa ikony |
| `created_at` | TIMESTAMP | Data utworzenia |

Przykładowe kategorie: Zdrowie, Sport, Nauka, Rozwój osobisty, Praca, Odpoczynek.

## 1.3. `habit` – nawyki użytkowników

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator nawyku |
| `user_id` | BIGINT, FK | Właściciel nawyku |
| `category_id` | BIGINT, FK, NULL | Kategoria |
| `name` | VARCHAR(150) | Nazwa nawyku |
| `description` | TEXT, NULL | Opis |
| `start_date` | DATE | Data rozpoczęcia |
| `end_date` | DATE, NULL | Planowana data zakończenia |
| `status` | VARCHAR(20) | Status nawyku |
| `color` | VARCHAR(7), NULL | Kolor nawyku |
| `icon` | VARCHAR(50), NULL | Ikona nawyku |
| `sort_order` | INTEGER | Kolejność wyświetlania |
| `created_at` | TIMESTAMP | Data utworzenia |
| `updated_at` | TIMESTAMP | Data aktualizacji |

Przykładowe statusy:

- `active` – aktywny,
- `paused` – wstrzymany,
- `archived` – zarchiwizowany.

## 1.4. `habit_schedule` – harmonogramy nawyków

Tabela przechowuje definicję częstotliwości realizacji nawyku. Jeden nawyk może posiadać kolejne wersje harmonogramu obowiązujące w różnych okresach.

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator harmonogramu |
| `habit_id` | BIGINT, FK | Nawyk |
| `frequency_type` | VARCHAR(30) | Typ częstotliwości |
| `weekly_target` | SMALLINT, NULL | Wymagana liczba realizacji w tygodniu |
| `monday` | BOOLEAN | Realizacja w poniedziałek |
| `tuesday` | BOOLEAN | Realizacja we wtorek |
| `wednesday` | BOOLEAN | Realizacja w środę |
| `thursday` | BOOLEAN | Realizacja w czwartek |
| `friday` | BOOLEAN | Realizacja w piątek |
| `saturday` | BOOLEAN | Realizacja w sobotę |
| `sunday` | BOOLEAN | Realizacja w niedzielę |
| `valid_from` | DATE | Początek obowiązywania |
| `valid_to` | DATE, NULL | Koniec obowiązywania |
| `created_at` | TIMESTAMP | Data utworzenia |

Przykładowe wartości `frequency_type`:

- `daily` – codziennie,
- `selected_days` – wybrane dni tygodnia,
- `weekly_count` – określona liczba razy w tygodniu.

Przykłady:

| Nawyk | frequency_type | weekly_target | Wybrane dni |
|---|---|---|---|
| Picie wody | daily | NULL | — |
| Bieganie | selected_days | NULL | Pon., Śr., Pt. |
| Czytanie książek | weekly_count | 4 | — |
| Nauka języka | daily | NULL | — |

Dla typu `weekly_count` konkretne dni wykonania nie są narzucone. Użytkownik może sam zdecydować, kiedy zrealizuje nawyk.

## 1.5. `habit_completion` – historia realizacji nawyków

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator realizacji |
| `habit_id` | BIGINT, FK | Nawyk |
| `completion_date` | DATE | Dzień realizacji |
| `completed_at` | TIMESTAMP | Moment oznaczenia wykonania |
| `note` | TEXT, NULL | Notatka użytkownika |
| `created_at` | TIMESTAMP | Data utworzenia wpisu |
| `updated_at` | TIMESTAMP | Data aktualizacji |

Zalecane ograniczenie unikalności:

`UNIQUE(habit_id, completion_date)`

Oznacza to, że dany nawyk może posiadać maksymalnie jeden wpis realizacji dla konkretnego dnia.

Cofnięcie oznaczenia wykonania można zrealizować przez usunięcie wpisu. Jeżeli wymagane jest zachowanie historii zmian, należy dodatkowo wprowadzić tabelę zdarzeń lub audytu.

## 1.6. `habit_schedule_history` – historia zmian harmonogramów

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator zmiany |
| `habit_id` | BIGINT, FK | Nawyk |
| `old_schedule_id` | BIGINT, FK, NULL | Poprzedni harmonogram |
| `new_schedule_id` | BIGINT, FK | Nowy harmonogram |
| `changed_at` | TIMESTAMP | Data zmiany |
| `changed_by_id` | BIGINT, FK | Użytkownik dokonujący zmiany |
| `reason` | TEXT, NULL | Powód zmiany |

Tabela `habit_schedule` przechowuje wersje harmonogramów, natomiast `habit_schedule_history` rejestruje zdarzenia ich zmiany.

Dzięki temu można odtworzyć harmonogram obowiązujący w danym okresie i prawidłowo obliczyć historyczne statystyki.

# 2. Tabele dodatkowe

## 2.1. `habit_reminder` – przypomnienia

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator przypomnienia |
| `habit_id` | BIGINT, FK | Nawyk |
| `reminder_time` | TIME | Godzina przypomnienia |
| `channel` | VARCHAR(20) | E-mail / powiadomienie |
| `is_active` | BOOLEAN | Czy przypomnienie jest aktywne |
| `created_at` | TIMESTAMP | Data utworzenia |

## 2.2. `achievement` – definicje osiągnięć

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator osiągnięcia |
| `name` | VARCHAR(150) | Nazwa osiągnięcia |
| `description` | TEXT | Opis |
| `code` | VARCHAR(50), UNIQUE | Kod osiągnięcia |
| `condition_type` | VARCHAR(50) | Rodzaj warunku |
| `condition_value` | INTEGER | Wartość wymagana |
| `icon` | VARCHAR(50), NULL | Ikona osiągnięcia |

Przykładowe osiągnięcia:

- Pierwszy krok – pierwsza realizacja nawyku.
- Tydzień regularności – seria 7 realizacji.
- Mistrz systematyczności – seria 30 realizacji.
- Sto sukcesów – 100 wykonanych realizacji.

## 2.3. `user_achievement` – osiągnięcia użytkowników

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator wpisu |
| `user_id` | BIGINT, FK | Użytkownik |
| `achievement_id` | BIGINT, FK | Osiągnięcie |
| `habit_id` | BIGINT, FK, NULL | Nawyk, którego dotyczy osiągnięcie |
| `awarded_at` | TIMESTAMP | Data przyznania |

## 2.4. `habit_challenge` – wyzwania

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator wyzwania |
| `habit_id` | BIGINT, FK | Nawyk |
| `name` | VARCHAR(150) | Nazwa wyzwania |
| `description` | TEXT, NULL | Opis |
| `start_date` | DATE | Data rozpoczęcia |
| `end_date` | DATE | Data zakończenia |
| `target_count` | INTEGER | Wymagana liczba realizacji |
| `status` | VARCHAR(20) | Status wyzwania |
| `created_at` | TIMESTAMP | Data utworzenia |

Przykład: „Przeczytaj książkę przez 20 dni w ciągu miesiąca”.

## 2.5. `user_settings` – ustawienia użytkownika

| Pole | Typ | Opis |
|---|---|---|
| `id` | BIGINT, PK | Identyfikator ustawień |
| `user_id` | BIGINT, FK, UNIQUE | Użytkownik |
| `theme` | VARCHAR(20) | Motyw jasny / ciemny |
| `language` | VARCHAR(10) | Język interfejsu |
| `week_starts_on` | SMALLINT | Pierwszy dzień tygodnia |
| `email_notifications` | BOOLEAN | Powiadomienia e-mail |
| `updated_at` | TIMESTAMP | Data aktualizacji |

# 3. Podsumowanie

| Obszar | Tabele |
|---|---|
| Użytkownicy | `user`, `user_settings` |
| Kategorie | `category` |
| Nawyki | `habit` |
| Harmonogramy | `habit_schedule`, `habit_schedule_history` |
| Realizacje | `habit_completion` |
| Przypomnienia | `habit_reminder` |
| Osiągnięcia | `achievement`, `user_achievement` |
| Wyzwania | `habit_challenge` |

**Łącznie: 11 tabel (6 podstawowych i 5 dodatkowych).**

# 4. Najważniejsze relacje

| Relacja | Krotność |
|---|---|
| User → Habit | 1:N |
| User → Category | 1:N dla kategorii własnych |
| Category → Habit | 1:N |
| Habit → HabitSchedule | 1:N |
| Habit → HabitCompletion | 1:N |
| Habit → HabitScheduleHistory | 1:N |
| Habit → HabitReminder | 1:N |
| Habit → HabitChallenge | 1:N |
| User → UserSettings | 1:0..1 |
| User → UserAchievement | 1:N |
| Achievement → UserAchievement | 1:N |

# 5. Najważniejsze ograniczenia integralności

Przy implementacji należy uwzględnić:

1. Unikalność adresu `user.email`.
2. Każdy nawyk musi należeć do istniejącego użytkownika.
3. Użytkownik może modyfikować wyłącznie własne nawyki i realizacje.
4. Nawyk może zostać przypisany wyłącznie do kategorii systemowej lub kategorii należącej do jego właściciela.
5. Dla pary (`habit_id`, `completion_date`) może istnieć maksymalnie jeden wpis.
6. Data zakończenia nawyku nie może być wcześniejsza niż data rozpoczęcia.
7. Data realizacji powinna mieścić się w okresie obowiązywania nawyku.
8. Dla harmonogramu `weekly_count` wartość `weekly_target` musi należeć do zakresu 1–7.
9. Dla harmonogramu `selected_days` musi zostać wskazany co najmniej jeden dzień tygodnia.
10. Okresy obowiązywania kolejnych harmonogramów tego samego nawyku nie mogą się nakładać.
11. Zmiana harmonogramu nie może usuwać wcześniejszych realizacji.
12. Archiwizacja nawyku nie może usuwać jego historii.
13. Dla wyzwań `end_date` nie może być wcześniejsza niż `start_date`.
14. Wartości `target_count` i `condition_value` muszą być dodatnie.
15. Statystyki powinny uwzględniać wyłącznie dni lub okresy, w których realizacja nawyku była wymagana.
16. Dla nawyków tygodniowych skuteczność powinna być obliczana na podstawie liczby wymaganych realizacji w tygodniu.
17. Obliczanie serii regularności musi uwzględniać harmonogram i nie może traktować dni wolnych jako niepowodzeń.

# 6. Zasady obliczania statystyk

## 6.1. Skuteczność realizacji

Dla nawyków codziennych i realizowanych w wybrane dni tygodnia:

\[
S=\frac{W}{P}\cdot100\%
\]

gdzie:

- \(W\) – liczba wykonanych zaplanowanych realizacji,
- \(P\) – liczba zaplanowanych realizacji w analizowanym okresie.

Przykład:

Nawyk zaplanowano na 20 dni, a wykonano go 16 razy.

\[
S=\frac{16}{20}\cdot100\%=80\%.
\]

Jeśli \(P=0\), skuteczność powinna być oznaczona jako brak danych, a nie 0%.

## 6.2. Nawyki realizowane kilka razy w tygodniu

Dla nawyku z celem \(k\) realizacji tygodniowo, przy \(w\) wykonaniach w danym tygodniu:

\[
S=\frac{\min(w,k)}{k}\cdot100\%.
\]

Przykład:

Użytkownik zaplanował bieganie 3 razy w tygodniu, a pobiegł 2 razy.

\[
S=\frac{2}{3}\cdot100\%\approx66{,}67\%.
\]

Jeśli użytkownik pobiegnie 4 razy, skuteczność wyniesie 100%, ponieważ wymagany cel został osiągnięty.

Dla niepełnych tygodni na początku lub końcu okresu obowiązywania nawyku należy zdefiniować spójną zasadę rozliczania celu, np. proporcjonalne zmniejszenie wymaganej liczby realizacji.

## 6.3. Serie regularności (streak)

Seria oznacza liczbę kolejnych wymaganych jednostek realizacji, w których użytkownik osiągnął cel.

- Dla nawyków codziennych – kolejne dni.
- Dla nawyków wykonywanych w wybrane dni – kolejne zaplanowane dni.
- Dla nawyków tygodniowych – kolejne tygodnie z osiągniętym celem.

Przykład:

Nawyk „Bieganie” zaplanowano na poniedziałki, środy i piątki.

Jeżeli użytkownik wykonał go w poniedziałek, środę, piątek i kolejny poniedziałek, seria wynosi 4 realizacje.

Wtorek, czwartek, sobota i niedziela nie przerywają serii, ponieważ nie były dniami wymaganymi.

Bieżący niezamknięty dzień lub tydzień nie powinien przerywać aktualnej serii, dopóki termin realizacji celu nie upłynął.

# 7. Proponowane etapy realizacji projektu

## Etap I – podstawowa wersja (MVP)

Tabele:

- `user`
- `category`
- `habit`
- `habit_schedule`
- `habit_completion`

Zakres:

- Rejestracja i logowanie.
- Zarządzanie kategoriami i nawykami.
- Definiowanie harmonogramów.
- Oznaczanie wykonania nawyków.
- Wyświetlanie dziennej listy nawyków.
- Przeglądanie historii realizacji.

## Etap II – logika biznesowa i statystyki

Dodatkowa tabela:

- `habit_schedule_history`

Zakres:

- Zmiana harmonogramów z zachowaniem historii.
- Obliczanie skuteczności realizacji.
- Wyznaczanie aktualnych i najdłuższych serii.
- Statystyki tygodniowe i miesięczne.
- Kalendarz aktywności.
- Wykresy postępów.
- Archiwizacja nawyków.

## Etap III – funkcjonalności dodatkowe

Tabele:

- `habit_reminder`
- `achievement`
- `user_achievement`
- `habit_challenge`
- `user_settings`

Zakres:

- Przypomnienia o nawykach.
- System osiągnięć i odznak.
- Wyzwania czasowe.
- Personalizacja interfejsu.
- Eksport danych do CSV.
- Rozbudowane statystyki i wizualizacje.

# 8. Możliwe rozszerzenie – nawyki ilościowe

Jeżeli aplikacja ma obsługiwać nawyki takie jak:

- wypicie 2 litrów wody,
- przeczytanie 20 stron książki,
- wykonanie 10 000 kroków,
- nauka przez 30 minut,

można rozszerzyć istniejące tabele.

### Dodatkowe pola w `habit`

| Pole | Typ | Opis |
|---|---|---|
| `tracking_type` | VARCHAR(20) | `binary` / `quantity` |
| `target_value` | DECIMAL(10,2), NULL | Wymagana wartość |
| `unit` | VARCHAR(30), NULL | Jednostka, np. ml, strony, minuty |

### Dodatkowe pole w `habit_completion`

| Pole | Typ | Opis |
|---|---|---|
| `actual_value` | DECIMAL(10,2), NULL | Wartość rzeczywiście osiągnięta |

Dla nawyku ilościowego można przyjąć, że realizacja jest zaliczona, gdy:

\[
\text{actual\_value}\geq\text{target\_value}.
\]

W bardziej rozbudowanej wersji warto przechowywać cele ilościowe w wersjonowanym harmonogramie `habit_schedule`, aby zmiana celu nie wpływała na ocenę historycznych realizacji.

**Najważniejszym elementem projektu jest poprawne modelowanie harmonogramów i historii realizacji nawyków. Szczególną uwagę należy poświęcić obliczaniu statystyk oraz serii regularności przy różnych częstotliwościach wykonywania czynności.**
