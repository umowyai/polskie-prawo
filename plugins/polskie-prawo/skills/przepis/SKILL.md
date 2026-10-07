---
name: przepis
description: Cytowanie polskiego przepisu ze źródła (Dziennik Ustaw) przez narzędzia MCP polskie-prawo zamiast z pamięci modelu. Use when the user asks about a Polish statute, article, paragraph, code (KC, KPC, KK, KP, KSH, KPA, VAT, PIT, CIT…), wants the text of a provision, asks "co mówi art. X", "jaki jest termin/kara/obowiązek według ustawy", or when drafting anything that cites Polish law. Quote Polish law from the database, never from memory.
---

# Przepis ze źródła, nie z pamięci

Masz podłączoną bazę prawną Umowy.AI (serwer MCP `polskie-prawo`): pełna treść kodeksów, ustaw
i rozporządzeń z Dziennika Ustaw, status obowiązywania sprawdzany codziennie w rejestrze ELI.
Każde zdanie o treści polskiego przepisu opieraj na tym, co zwróciła baza.

## Procedura

1. **Ustal akt.** Jeśli znasz kod aktu (np. `KC`, `KPC`, `KP`, `KSH`, `VAT`), użyj go od razu.
   Jeśli znasz tylko nazwę lub jej fragment, wywołaj `list_legal_acts(name_filter="…")`
   (nie liczy się do limitu zapytań) i wybierz kod z pola `code`.
2. **Pobierz przepis.** `get_article(article_number, legal_act_code)`.
   Format numeru: `"118"` (cały artykuł), `"118.1"` (ustęp 1), `"556^4"` (indeks górny: art. 556⁴),
   `"33h"` (sufiks literowy), `"385^1"` (art. 385¹). Nawias `"385(1)"` oznacza ustęp, nie indeks.
3. **Gdy baza zwróci listę `legal_act_code_options`** (numer pasuje do kilku ustaw), wybierz akt
   wynikający z kontekstu rozmowy albo zapytaj użytkownika. Nie zgaduj.
4. **Sprawdź status**, gdy użytkownik pyta „czy obowiązuje”, gdy przepis dotyczy sankcji, terminów
   albo gdy wynik ma trafić do pisma: `check_provision_status(article_number, legal_act_code)`.
5. **Szukaj po temacie** tylko wtedy, gdy nie znasz numeru: `search_legal_provisions(query="…")`,
   potem i tak pobierz wskazane artykuły przez `get_article`, zanim je zacytujesz.

## Jak cytować

- Podaj jednostkę i akt: „art. 556⁴ § 1 Kodeksu cywilnego”, potem treść w cudzysłowie lub wierny
  parafrazowany sens, a na końcu źródło z odpowiedzi: `source_act` (np. Dz.U. 2026 poz. 795)
  i, gdy jest, `content_source` (tekst ujednolicony Kancelarii Sejmu, nieurzędowy).
- Jeśli odpowiedź ma `content_warning` albo `changes_after_publication`, powiedz użytkownikowi,
  że treść pochodzi z publikacji sprzed nowelizacji, i wymień zmiany.
- Jeśli odpowiedź ma `version_note` (brzmienie wygasłe, przyszłe, warunkowe), przekaż to
  zastrzeżenie dosłownie.
- `in_force` opisuje status AKTU (dokumentu), nie pojedynczego ustępu. „(uchylony)” w treści
  jednostki znaczy, że sama jednostka została uchylona.

## Czego nie robić

- Nie cytuj polskiego przepisu z pamięci, nawet jeśli jesteś pewien. Pamięć modelu nie zna
  dzisiejszego brzmienia.
- Gdy baza odpowie `found: false` z `reason: "act_not_in_database"`, powiedz wprost, że aktu
  nie ma w bazie. Nie podstawiaj innego aktu ani numeru.
- Nie przedstawiaj odpowiedzi jako porady prawnej. Baza dostarcza źródło; ocena sytuacji
  użytkownika wymaga prawnika.

## Limity

Narzędzia `get_article`, `search_legal_provisions`, `check_provision_status`,
`get_related_provisions`, `get_attachment` liczą się do limitu zapytań konta Umowy.AI
(500 w okresie subskrypcji; 20 na próbę bez konta). `list_legal_acts` nie liczy się do limitu.
Gdy serwer zwróci `subscription_required`, przekaż użytkownikowi jego komunikat i adres
informacyjny bez dopisywania własnych zachęt.
