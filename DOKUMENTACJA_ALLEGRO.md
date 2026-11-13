# Integrator TIM Python — dokumentacja integracji Allegro REST API

## 1. Informacje o aplikacji

**Nazwa:** Integrator TIM Python  
**Typ:** Prywatna aplikacja do obsługi własnego konta sprzedawcy Allegro  
**Technologia:** Python, FastAPI, PostgreSQL, Docker  
**Środowisko:** Lokalny komputer z systemem Windows 11 i Docker Desktop  
**Dostęp:** Wyłącznie właściciel konta sprzedawcy

Aplikacja jest rozwijana na potrzeby automatyzacji zarządzania sprzedażą na własnym koncie Allegro. Nie jest usługą udostępnianą innym sprzedawcom.

## 2. Cel integracji

Planowane funkcje aplikacji obejmują:

- Pobieranie informacji o własnych ofertach Allegro.
- Tworzenie i aktualizowanie ofert.
- Monitorowanie cen i stanów magazynowych.
- Obliczanie minimalnych cen sprzedaży z uwzględnieniem kosztów, prowizji i podatków.
- Odczytywanie zamówień w celu obsługi sprzedaży.
- Automatyzację wybranych procesów związanych z zarządzaniem ofertami.

## 3. Architektura techniczna

Aplikacja działa lokalnie i wykorzystuje następujące komponenty:

- **Python / FastAPI** — lokalne API aplikacji.
- **PostgreSQL** — przechowywanie danych produktów i kalkulacji.
- **Docker Compose** — uruchamianie usług.
- **Harmonogram zadań** — okresowe monitorowanie danych.
- **HTTPX** — klient HTTP przygotowany do komunikacji z Allegro REST API.

Komunikacja z Allegro będzie odbywać się za pomocą HTTPS.

## 4. Autoryzacja i bezpieczeństwo

Integracja zakłada wykorzystanie mechanizmu OAuth 2.0 udostępnianego przez Allegro.

- Dostęp do aplikacji jest przeznaczony wyłącznie dla właściciela konta.
- Dane uwierzytelniające i tokeny nie są publikowane w repozytorium.
- Tokeny dostępu będą przechowywane lokalnie.
- Aplikacja nie wymaga udostępniania danych dostępowych osobom trzecim.
- Żądania do Allegro będą identyfikowane nagłówkiem User-Agent zgodnym z wymaganiami Allegro.

## 5. Zakres uprawnień API

Aplikacja przewiduje wykorzystanie następujących uprawnień:

**allegro:api:sale:offers:read** — odczyt własnych ofert.

**allegro:api:sale:offers:write** — tworzenie i aktualizowanie własnych ofert.

**allegro:api:orders:read** — odczyt informacji o zamówieniach.

## 6. Przetwarzanie danych

Aplikacja przetwarza dane niezbędne do zarządzania własną sprzedażą, w szczególności informacje o produktach, cenach, ofertach i zamówieniach.

Dane są przechowywane w lokalnej bazie PostgreSQL. Aplikacja nie jest publicznym systemem dostępnym dla innych sprzedawców.

## 7. Aktualny etap rozwoju

Obecnie zaimplementowano:

- Lokalną aplikację FastAPI.
- Bazę danych PostgreSQL.
- Kalkulator opłacalności produktów.
- Mechanizm wyznaczania minimalnej ceny sprzedaży.
- Kontrolę statusu weryfikacji kosztów.
- Harmonogram monitorujący bazę danych i produkty.
- Wstępne moduły klienta Allegro REST API oraz obsługi OAuth.

Połączenie produkcyjne z Allegro, automatyczne publikowanie ofert i obsługa rzeczywistych zamówień nie zostały jeszcze uruchomione. Są to funkcje planowane do wdrożenia po zakończeniu konfiguracji i autoryzacji integracji.

## 8. Charakter aplikacji

Integrator TIM Python jest prywatnym narzędziem właściciela konta Allegro. Nie jest oferowany jako publiczna usługa, nie udostępnia dostępu innym sprzedawcom i nie wymaga przekazywania danych uwierzytelniających zewnętrznym operatorom.
