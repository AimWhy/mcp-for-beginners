<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "e25bc265a51244a7a2d93b3761543a1f",
  "translation_date": "2025-06-13T02:12:55+00:00",
  "source_file": "03-GettingStarted/08-testing/README.md",
  "language_code": "hr"
}
-->
## Testiranje i otklanjanje pogrešaka

Prije nego što započnete s testiranjem vašeg MCP servera, važno je razumjeti dostupne alate i najbolje prakse za otklanjanje pogrešaka. Učinkovito testiranje osigurava da vaš server radi kako se očekuje i pomaže vam brzo identificirati i riješiti probleme. Sljedeći odjeljak prikazuje preporučene pristupe za provjeru vaše MCP implementacije.

## Pregled

Ova lekcija obuhvaća kako odabrati pravi pristup testiranju i najučinkovitiji alat za testiranje.

## Ciljevi učenja

Do kraja ove lekcije moći ćete:

- Opisati različite pristupe testiranju.
- Koristiti različite alate za učinkovito testiranje vašeg koda.

## Testiranje MCP servera

MCP pruža alate koji vam pomažu testirati i otkloniti pogreške na vašim serverima:

- **MCP Inspector**: Alat naredbenog retka koji se može koristiti kao CLI alat i kao vizualni alat.
- **Ručno testiranje**: Možete koristiti alat poput curl za izvođenje web zahtjeva, ali bilo koji alat sposoban za HTTP će također poslužiti.
- **Jedinično testiranje**: Moguće je koristiti vaš omiljeni testni okvir za testiranje značajki i servera i klijenta.

### Korištenje MCP Inspectora

Opisali smo korištenje ovog alata u prethodnim lekcijama, ali hajdemo ga malo ukratko predstaviti. To je alat izgrađen u Node.js-u i možete ga koristiti pozivom izvršne datoteke `npx` koja će privremeno preuzeti i instalirati alat te se nakon izvršavanja vašeg zahtjeva očistiti.

[MCP Inspector](https://github.com/modelcontextprotocol/inspector) vam pomaže:

- **Otkriti mogućnosti servera**: Automatski detektira dostupne resurse, alate i upite
- **Testirati izvršenje alata**: Isprobajte različite parametre i vidite odgovore u stvarnom vremenu
- **Pregledati metapodatke servera**: Istražite informacije o serveru, sheme i konfiguracije

Tipično pokretanje alata izgleda ovako:

```bash
npx @modelcontextprotocol/inspector node build/index.js
```

Gornja naredba pokreće MCP i njegov vizualni sučelje te otvara lokalno web sučelje u vašem pregledniku. Možete očekivati nadzornu ploču koja prikazuje vaše registrirane MCP servere, njihove dostupne alate, resurse i upite. Sučelje vam omogućuje interaktivno testiranje izvršenja alata, pregled metapodataka servera i gledanje odgovora u stvarnom vremenu, što olakšava provjeru i otklanjanje pogrešaka u implementacijama vašeg MCP servera.

Evo kako to može izgledati: ![Inspector](../../../../translated_images/connect.141db0b2bd05f096fb1dd91273771fd8b2469d6507656c3b0c9df4b3c5473929.hr.png)

Također možete pokrenuti ovaj alat u CLI načinu rada dodavanjem atributa `--cli`. Evo primjera pokretanja alata u "CLI" načinu rada koji prikazuje sve alate na serveru:

```sh
npx @modelcontextprotocol/inspector --cli node build/index.js --method tools/list
```

### Ručno testiranje

Osim pokretanja inspectora za testiranje mogućnosti servera, sličan pristup je pokretanje klijenta koji može koristiti HTTP, poput curl.

Pomoću curl-a možete izravno testirati MCP servere koristeći HTTP zahtjeve:

```bash
# Example: Test server metadata
curl http://localhost:3000/v1/metadata

# Example: Execute a tool
curl -X POST http://localhost:3000/v1/tools/execute \
  -H "Content-Type: application/json" \
  -d '{"name": "calculator", "parameters": {"expression": "2+2"}}'
```

Kao što vidite u gornjem primjeru korištenja curl-a, koristite POST zahtjev za pozivanje alata s payloadom koji sadrži ime alata i njegove parametre. Koristite pristup koji vam najviše odgovara. CLI alati su općenito brži za korištenje i lako se mogu automatizirati, što može biti korisno u CI/CD okruženju.

### Jedinično testiranje

Izradite jedinične testove za vaše alate i resurse kako biste osigurali da rade kako se očekuje. Evo primjera testnog koda.

```python
import pytest

from mcp.server.fastmcp import FastMCP
from mcp.shared.memory import (
    create_connected_server_and_client_session as create_session,
)

# Mark the whole module for async tests
pytestmark = pytest.mark.anyio


async def test_list_tools_cursor_parameter():
    """Test that the cursor parameter is accepted for list_tools.

    Note: FastMCP doesn't currently implement pagination, so this test
    only verifies that the cursor parameter is accepted by the client.
    """

 server = FastMCP("test")

    # Create a couple of test tools
    @server.tool(name="test_tool_1")
    async def test_tool_1() -> str:
        """First test tool"""
        return "Result 1"

    @server.tool(name="test_tool_2")
    async def test_tool_2() -> str:
        """Second test tool"""
        return "Result 2"

    async with create_session(server._mcp_server) as client_session:
        # Test without cursor parameter (omitted)
        result1 = await client_session.list_tools()
        assert len(result1.tools) == 2

        # Test with cursor=None
        result2 = await client_session.list_tools(cursor=None)
        assert len(result2.tools) == 2

        # Test with cursor as string
        result3 = await client_session.list_tools(cursor="some_cursor_value")
        assert len(result3.tools) == 2

        # Test with empty string cursor
        result4 = await client_session.list_tools(cursor="")
        assert len(result4.tools) == 2
    
```

Prethodni kod radi sljedeće:

- Koristi pytest framework koji vam omogućuje stvaranje testova kao funkcija i korištenje assert izjava.
- Kreira MCP server s dva različita alata.
- Koristi `assert` izjavu za provjeru ispunjenosti određenih uvjeta.

Pogledajte [cijelu datoteku ovdje](https://github.com/modelcontextprotocol/python-sdk/blob/main/tests/client/test_list_methods_cursor.py)

Na temelju ove datoteke možete testirati vlastiti server kako biste osigurali da su mogućnosti kreirane onako kako treba.

Svi glavni SDK-ovi imaju slične odjeljke za testiranje pa ih možete prilagoditi vašem odabranom runtime-u.

## Primjeri

- [Java Calculator](../samples/java/calculator/README.md)
- [.Net Calculator](../../../../03-GettingStarted/samples/csharp)
- [JavaScript Calculator](../samples/javascript/README.md)
- [TypeScript Calculator](../samples/typescript/README.md)
- [Python Calculator](../../../../03-GettingStarted/samples/python)

## Dodatni resursi

- [Python SDK](https://github.com/modelcontextprotocol/python-sdk)

## Što slijedi

- Sljedeće: [Deployment](/03-GettingStarted/09-deployment/README.md)

**Odricanje od odgovornosti**:  
Ovaj dokument preveden je pomoću AI usluge za prevođenje [Co-op Translator](https://github.com/Azure/co-op-translator). Iako nastojimo osigurati točnost, imajte na umu da automatski prijevodi mogu sadržavati pogreške ili netočnosti. Izvorni dokument na izvornom jeziku treba smatrati autoritativnim izvorom. Za kritične informacije preporučuje se profesionalni ljudski prijevod. Ne snosimo odgovornost za bilo kakva nesporazuma ili pogrešna tumačenja proizašla iz korištenja ovog prijevoda.