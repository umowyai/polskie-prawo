---
name: klauzula
description: Analiza klauzuli umownej (kara umowna, odstąpienie, wypowiedzenie, zakaz konkurencji, rękojmia, płatności, poufność) pod kątem polskiego prawa z przepisami pobranymi z bazy MCP polskie-prawo. Use when the user pastes a contract clause or asks whether a clause is valid, abusive, enforceable or compliant with the Polish Civil Code or other Polish statutes, or asks what the law says about a contractual mechanism.
---

# Klauzula umowna z przepisami ze źródła

Użytkownik wkleja klauzulę albo pyta o mechanizm umowny. Twoim zadaniem jest zestawić ją
z przepisami pobranymi z bazy Umowy.AI, nie z pamięci, i jasno oddzielić to, co mówi przepis,
od własnej oceny.

## Procedura

1. **Nazwij mechanizm** klauzuli (np. kara umowna, zastrzeżenie odstąpienia, zakaz konkurencji
   po ustaniu umowy, ograniczenie rękojmi, termin zapłaty) i wskaż, w którym akcie szukać
   (najczęściej `KC`; umowy pracownicze `KP`; spółki `KSH`; transakcje handlowe terminy
   zapłaty `UoPNOT` lub szukaj po nazwie przez `list_legal_acts`).
2. **Znajdź przepisy:** `search_legal_provisions(query="…", legal_act_code="KC")` z opisem
   mechanizmu, potem `get_article` dla każdego artykułu, na który chcesz się powołać.
   Dla klauzul konsumenckich pobierz art. 385¹–385³ KC (`"385^1"`, `"385^3"`); dla nieważności
   art. 58 KC; dla kar umownych art. 483–484 KC; dla odstąpienia art. 395 KC.
3. **Sprawdź status** każdego cytowanego przepisu: `check_provision_status`.
4. **Oceń w trzech koszykach**, osobno dla każdego zarzutu:
   - zgodna z przepisami (ważna),
   - sprzeczna z przepisem bezwzględnie obowiązującym (nieważność z mocy prawa, art. 58 KC),
   - niekorzystna lub potencjalnie abuzywna, ale technicznie ważna (w obrocie konsumenckim
     art. 385¹ KC; między przedsiębiorcami swoboda umów, art. 353¹ KC).
5. **Zaproponuj poprawkę** brzmienia, gdy użytkownik o to prosi, i wskaż, który przepis ją
   uzasadnia.

## Jak pisać

- Każdy wniosek łącz z artykułem i jego treścią z bazy: „art. 484 § 2 KC: …, dlatego …”.
- Odróżniaj treść przepisu (cytat z bazy) od oceny (Twoje zdanie). Oceny opatruj zastrzeżeniem,
  że zależą od okoliczności i rodzaju stron (konsument / przedsiębiorca).
- Gdy przepis ma `content_warning` lub `version_note`, przekaż to użytkownikowi.
- Zakończ listą przepisów ze źródłami (`source_act`).

## Granice

To nie jest porada prawna ani zastępstwo prawnika. Umowa, strony i kontekst mogą zmieniać
wnioski. Powiedz to raz, na końcu, bez powtarzania przy każdym zdaniu.
