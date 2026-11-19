**MCP Bridge – Custom Databases** łączy bazy Pages w Invision Community 4.7 z klientami AI obsługującymi MCP (Model Context Protocol), np. z Claude. Redakcja decyduje, które bazy i pola widzi AI, a wszystko, co AI zapisuje, przechodzi przez moderację, rewizje i uprawnienia samego IPS.

[In English](README.md) · [Changelog](CHANGELOG.md) · [iql.pl](https://iql.pl)

To repozytorium jest publicznym kanałem wersji: aktualna wersja i lista zmian. Nie ma tu kodu ani plików aplikacji.

## Aktualna wersja

| Aplikacja | Wersja | Dla |
| --- | --- | --- |
| MCP Bridge – Custom Databases | zobacz [`latest.json`](latest.json) | Invision Community 4.7 z Pages |

IPS sam sprawdza nowe wersje: aplikacja czyta [`latest.json`](latest.json) z tego repozytorium, a ACP pokazuje przy niej znaczek „nowa wersja”.

## Co robi

Klient AI podłączony do forum czyta rekordy wybranych baz Pages (artykuły, newsy, recenzje) i zapisuje nowe albo zmiany. Ma do tego 11 narzędzi MCP: lista i opis baz, wyszukiwanie i odczyt rekordów, wyszukiwanie powiązanych rekordów (marki, sklepy), wgrywanie zdjęć, tworzenie i edycja rekordów.

| Co ustawia administrator | Jak |
| --- | --- |
| Które bazy widzi AI | W ACP, osobno dla każdej bazy; domyślnie żadna |
| Które pola czyta i zapisuje oraz jak je wypełniać | Biała lista pól z instrukcjami, przykładami i limitami długości. Opisy i limity ustawione w Pages też są brane pod uwagę. |
| SEO | Meta opis, słowa kluczowe i własny adres URL rekordu, włączane osobno dla bazy |
| Jako kto pisze AI | Tokeny dostępu tworzone w ACP: autor domyślny i dozwoleni inni autorzy, bazy, odczyt albo zapis, ważność i adresy IP |
| Co trafia na stronę | Nowe rekordy zawsze czekają w natywnej kolejce moderacji IPS. Zmiany opublikowanych rekordów są propozycjami zatwierdzanymi w ACP (z powiadomieniem) albo wchodzą od razu z rewizją. |
| Historia | Każde wywołanie trafia do dziennika. Przed każdą zmianą zapisuje się natywna rewizja Pages, a zmianę cofa się jednym kliknięciem. |

## Jak zapisuje

- **Tylko przez modele IPS.** Żadnego SQL na tabelach baz, więc uprawnienia, moderacja, rewizje, indeks wyszukiwania, webhooki i synchronizacja tematu na forum działają tak jak przy treści dodanej ręcznie.
- **Zdjęcia jako natywne pliki forum.** Zdjęcia trafiają do treści jako załączniki, do głównego obrazka rekordu i do pól Upload. AI wgrywa pliki przez jednorazowy podpisany link, więc token dostępu nie wychodzi poza connector.
- **Pola relacyjne** (marka, sklep) wypełnia rekordami znalezionymi w powiązanych bazach; te bazy zostają tylko do odczytu.
- **Bez usuwania, zatwierdzania, przypinania i wyróżniania.** AI nie ma do tego narzędzi.

## Wymagania

| | |
| --- | --- |
| Invision Community | 4.7 z Pages |
| PHP | 8.0–8.4 |
| Klient MCP | Claude.ai (custom connector), Claude Desktop, Claude Code albo dowolny klient ze Streamable HTTP |
