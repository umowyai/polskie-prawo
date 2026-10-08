# polskie-prawo — plugin (Claude Code, ChatGPT, Codex)

Polska baza prawna z Dziennika Ustaw (serwer MCP `https://mcp.umowy.ai/mcp`) plus trzy skille:

- `przepis` — cytuj przepis ze źródła (`list_legal_acts` → `get_article` → `check_provision_status`), nigdy z pamięci;
- `stan-prawny-na-dzien` — brzmienie na wskazany dzień i porównanie wersji (`effective_as_of_date`);
- `klauzula` — analiza klauzuli umownej z przepisami pobranymi z bazy.

Instalacja i dostęp: https://umowy.ai/mcp/ · Privacy Policy: https://umowy.ai/polityka-prywatnosci/ ·
Terms: https://umowy.ai/regulamin/ · wsparcie: serwis@umowy.ai

Polish law database (Journal of Laws) as MCP tools plus skills that teach the assistant to quote provisions
from the source, read a provision as of a given date and review contract clauses against the statute.
