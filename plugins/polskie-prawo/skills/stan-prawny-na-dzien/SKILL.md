---
name: stan-prawny-na-dzien
description: Brzmienie polskiego przepisu obowiązujące na wskazany dzień i porównanie wersji w czasie, przez narzędzia MCP polskie-prawo. Use when the user asks how a Polish provision read on a past date ("stan prawny na dzień", "brzmienie obowiązujące w 2023 r."), whether it changed, what an amendment introduced, which version applies to a contract signed on a given date, or when a court or tax matter depends on the law in force at a specific moment.
---

# Stan prawny na dzień

Przepis ma historię. Umowa, spór albo decyzja podlegają brzmieniu obowiązującemu w konkretnym
dniu, nie dzisiejszemu. Baza Umowy.AI przechowuje brzmienia czasowe i daty ich przejść.

## Procedura

1. **Ustal datę.** Z pytania (data umowy, zdarzenia, decyzji). Jeśli jej nie ma, zapytaj albo
   zaznacz, że odpowiadasz dla stanu dzisiejszego.
2. **Pobierz brzmienie na dzień:** `get_article(article_number, legal_act_code,
   effective_as_of_date="RRRR-MM-DD")`. Odpowiedź niesie pola `version_status`,
   `version_valid_from`, `version_valid_to` oraz `version_note` (zdanie dla użytkownika:
   do kiedy obowiązywało to brzmienie, od kiedy kolejne, czy data zależy od warunku).
3. **Porównaj z dzisiejszym**, gdy pytanie brzmi „czy się zmieniło”: drugie wywołanie
   `get_article` bez `effective_as_of_date` i zestaw różnice ustęp po ustępie.
4. **Sprawdź status aktu** na dzień: `check_provision_status(article_number, legal_act_code,
   effective_as_of_date="…")`. Pola `consolidation.superseded_by` i
   `consolidation.changes_after_publication` mówią, czy istnieje nowszy tekst jednolity
   i które nowelizacje weszły w życie po publikacji, z której pochodzi treść.
5. **Gdy baza ma tylko jedno brzmienie**, a data pytania jest wcześniejsza niż publikacja
   (`publication_date`), powiedz, że baza podaje brzmienie z tej publikacji, i wskaż
   `changes_after_publication` jako listę zmian do sprawdzenia.

## Jak odpowiadać

- Zacznij od zdania: „Na dzień … art. … brzmiał:” i podaj treść z bazy.
- Przekaż `version_note` dosłownie, jeśli występuje. To zastrzeżenia o brzmieniu wygasłym,
  przyszłym albo zależnym od warunku, których model nie powinien łagodzić.
- Zawsze podaj `source_act` (Dz.U. rok, poz.) obu wersji, gdy porównujesz.
- Nie wnioskuj o dacie zmiany z własnej pamięci. Jeśli baza nie podaje daty przejścia
  (`version_from_condition` / `version_to_condition`), powiedz, że data zależy od warunku
  opisanego w odnośniku, i zacytuj go.

## Granice

Ustalenie, które brzmienie stosuje się do konkretnej sprawy (przepisy przejściowe, zasady
intertemporalne), wymaga oceny prawnika. Baza daje brzmienie na dzień i daty przejść; nie
rozstrzyga, które z nich wiąże strony.
