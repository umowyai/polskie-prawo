# Polskie Prawo (Dziennik Ustaw) by Umowy.AI — plugin i serwer MCP

[English below](#english)

Baza polskiego prawa z Dziennika Ustaw jako narzędzia dla Twojego AI: ponad 600 ustaw
i rozporządzeń w pełnym brzmieniu, status obowiązywania sprawdzany codziennie w rejestrze ELI,
brzmienie przepisu na wskazany dzień, załączniki i tabele. Serwer MCP: `https://mcp.umowy.ai/mcp`.
Strona z instrukcjami dla wszystkich aplikacji: **https://umowy.ai/mcp/**

## Instalacja

**Claude Code** (plugin z tego repozytorium, ze skillami):
```
/plugin marketplace add umowyai/polskie-prawo
/plugin install polskie-prawo@umowy-ai
```
potem `/mcp` → `polskie-prawo` → logowanie e-mailem. Sam serwer bez skilli:
```
claude mcp add --transport http polskie-prawo https://mcp.umowy.ai/mcp --scope user
```

**claude.ai / Claude Desktop** — jedno kliknięcie:
https://claude.ai/customize/connectors?modal=add-custom-connector&connectorName=Polskie%20Prawo%20(Dziennik%20Ustaw)&connectorUrl=https%3A%2F%2Fmcp.umowy.ai%2Fmcp

**ChatGPT** (Business, Enterprise, Edu, Pro): Plugins → + → Add custom MCP server → adres
`https://mcp.umowy.ai/mcp`, OAuth.

**Cursor, VS Code, Codex, Kimi i inne klienty MCP**: konfiguracja z `plugins/polskie-prawo/.mcp.json`
albo instrukcje na https://umowy.ai/mcp/.

## Co jest w repozytorium

| Ścieżka | Co to |
|---|---|
| `plugins/polskie-prawo/.mcp.json` | wskazanie zdalnego serwera MCP (Streamable HTTP, OAuth 2.1) |
| `plugins/polskie-prawo/skills/przepis` | jak cytować przepis ze źródła, nie z pamięci |
| `plugins/polskie-prawo/skills/stan-prawny-na-dzien` | brzmienie na dzień i porównanie wersji |
| `plugins/polskie-prawo/skills/klauzula` | analiza klauzuli umownej z przepisami z bazy |
| `.claude-plugin/marketplace.json` | własny marketplace `umowy-ai` dla Claude Code |
| `server.json` | wpis w oficjalnym MCP Registry (`ai.umowy/polskie-prawo`) |

## Narzędzia serwera

`search_legal_provisions`, `get_article`, `get_related_provisions`, `check_provision_status`,
`get_attachment`, `list_legal_acts`. Wszystkie tylko czytają bazę. Opis na https://umowy.ai/mcp/#narzedzia.

## Dostęp i cena

Logowanie e-mailem (WorkOS). Bez konta: 20 zapytań na próbę. Konto Umowy.AI z aktywnym planem
(49 zł brutto / 30 dni, 500 zapytań, pierwsze 7 dni bezpłatnie) łączy się automatycznie, gdy
e-mail logowania jest ten sam. Szczegóły: https://umowy.ai/mcp/#cena.

## Prywatność i zasady

Serwer dostaje wyłącznie treść zapytania do bazy; nie ma dostępu do dokumentów ani historii
rozmów. Zapytania są zapisywane z identyfikatorem konta w celu rozliczenia limitu.
[Polityka prywatności](https://app.umowy.ai/legal/polityka-prywatnosci.pdf) ·
[Regulamin](https://app.umowy.ai/legal/regulamin.pdf) · wsparcie: serwis@umowy.ai

Baza wyszukuje i cytuje przepisy. Nie udziela porad prawnych i nie zastępuje prawnika.

## Licencja

Pliki w tym repozytorium: MIT (patrz `LICENSE`). Usługa bazy prawnej pod `mcp.umowy.ai` jest
odrębną, własnościową usługą Vorna sp. z o.o. objętą regulaminem.

---

## English

Polish law from the Journal of Laws (Dziennik Ustaw) as tools for your AI: 600+ statutes and
regulations in full text, in-force status checked daily against the official ELI register,
wording of a provision as of any date, annexes and tables. MCP server: `https://mcp.umowy.ai/mcp`.
Setup for every app: **https://umowy.ai/en/mcp/**

**Claude Code**: `/plugin marketplace add umowyai/polskie-prawo`, then
`/plugin install polskie-prawo@umowy-ai`, then `/mcp` → sign in with e-mail.
**claude.ai / Claude Desktop**: one click — see the link above.
**ChatGPT** (Business, Enterprise, Edu, Pro): Plugins → + → Add custom MCP server →
`https://mcp.umowy.ai/mcp`, OAuth.

Tools: `search_legal_provisions`, `get_article`, `get_related_provisions`,
`check_provision_status`, `get_attachment`, `list_legal_acts` — all read-only.
Access: e-mail sign-in; 20 trial queries without an account; an Umowy.AI account with an active
plan (PLN 49 incl. VAT / 30 days, 500 queries, first 7 days free) links automatically when the
e-mail matches. Privacy policy and terms linked above (Polish). Support: serwis@umowy.ai.
Repository files: MIT. The database service is proprietary.
