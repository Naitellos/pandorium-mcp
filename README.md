# Pandorium MCP Server

**Pandorium** is a mystical AI platform for astrology, divination, and self-discovery. This MCP server exposes 11 professional-grade tools for astrology calculations, tarot readings, I Ching, rune casting, and quantum random number generation.

All divination tools use **quantum random numbers** from [ANU QRNG](https://qrng.anu.edu.au/) (Australian National University Quantum Random Number Generator) with cryptographic fallback. Astrology calculations use NASA-grade [astronomy-engine](https://github.com/cosinekitty/astronomy) ephemeris.

> **No API keys required. No database. No setup.** Just connect and use.

## Quick Start

### Remote Server (Recommended)

Connect to our hosted MCP server — no installation needed:

**Claude Desktop** (`claude_desktop_config.json`):
```json
{
  "mcpServers": {
    "pandorium": {
      "url": "https://pandorium.app/mcp"
    }
  }
}
```

**Cursor** (Settings → MCP → Add Server):
```
URL: https://pandorium.app/mcp
```

**Windsurf / Other MCP Clients**:
```
URL: https://pandorium.app/mcp
Transport: Streamable HTTP
```

## Available Tools (11)

### Astrology (7 tools)

| Tool | Description |
|------|-------------|
| `get_planet_positions` | Calculate positions of all 10 major planets for any date. Returns zodiac sign, degree, longitude, latitude, speed, and retrograde status. |
| `calculate_natal_chart` | Complete natal (birth) chart: planets in signs & houses, 12 house cusps, aspects (11 types), ascendant, midheaven, element/modality balance, Lilith, Lunar Nodes, Chiron. Supports 7 house systems. |
| `calculate_synastry` | Astrological compatibility between two people. Inter-chart aspects with weighted scoring (0-100), house overlays, relationship strengths/challenges. |
| `get_current_transits` | Current planetary transits against a natal chart. Aspect type, orb, applying/separating status, interpretation. |
| `get_lunar_phase` | Moon phase for any date: phase name, illumination percentage, description. |
| `get_lunar_calendar` | Lunar calendar for 1-90 days: daily phases, Vedic lunar days (Tithi) with energy ratings, upcoming events. |
| `get_astro_events` | Astronomical events for a date range: lunar phases, planetary ingresses, retrogrades, eclipses, major aspects, equinoxes/solstices. |

### Divination (3 tools)

| Tool | Description |
|------|-------------|
| `draw_tarot` | Draw tarot cards with quantum RNG. Spreads: single (1 card), triplet (3 cards: past/present/future), celtic (10-card Celtic Cross). Card names, positions, upright/reversed, meanings. |
| `cast_iching` | I Ching reading with quantum RNG using traditional yarrow stalk probabilities (1:5:7:3). Returns hexagram, trigrams, judgment, image, six lines with changing status. |
| `cast_runes` | Elder Futhark runes with quantum RNG. Spreads: single, norns (3 runes: past/present/future), cross (5 runes). Names, unicode symbols, meanings, deity/element/tree associations. |

### Utility (1 tool)

| Tool | Description |
|------|-------------|
| `quantum_random` | Generate 1-100 quantum random numbers from ANU QRNG. True quantum vacuum fluctuation randomness. |

## Example Usage

Once connected, just ask your AI assistant naturally:

- *"What's the current Moon phase?"*
- *"Calculate my natal chart — I was born on March 15, 1990 at 14:30 in Moscow"*
- *"Draw a three-card tarot spread about my career"*
- *"Cast runes for guidance about my relationship"*
- *"What are the major astrological events this month?"*
- *"Check compatibility between me and my partner"*
- *"What transits are affecting my chart right now?"*

## Tool Details

### Natal Chart Input

```json
{
  "birthData": {
    "date": "1990-03-15",
    "time": "14:30",
    "location": {
      "latitude": 55.7558,
      "longitude": 37.6173,
      "timezone": "Europe/Moscow",
      "city": "Moscow"
    }
  },
  "houseSystem": "placidus"
}
```

Supported house systems: `placidus` (default), `koch`, `regiomontanus`, `equal`, `whole_sign`, `campanus`, `porphyry`.

### Tarot Spreads

| Spread | Cards | Description |
|--------|-------|-------------|
| `single` | 1 | Quick oracle — one card guidance |
| `triplet` | 3 | Past / Present / Future |
| `celtic` | 10 | Full Celtic Cross reading |

### I Ching Types

| Type | Description |
|------|-------------|
| `iching_simple` | Primary hexagram only |
| `iching_full` | Primary + changing lines + nuclear hexagram |

### Rune Spreads

| Spread | Runes | Description |
|--------|-------|-------------|
| `rune_single` | 1 | Single rune guidance |
| `rune_norns` | 3 | Urd / Verdandi / Skuld (Past / Present / Future) |
| `rune_cross` | 5 | Five-rune cross spread |

## Technical Details

- **Transport**: Streamable HTTP (JSON-RPC over HTTP POST with SSE responses)
- **Endpoint**: `https://pandorium.app/mcp`
- **Mode**: Stateless (no session tracking)
- **Authentication**: None required
- **Randomness**: ANU Quantum Random Number Generator with `crypto.randomBytes` fallback
- **Ephemeris**: [astronomy-engine](https://github.com/cosinekitty/astronomy) — NASA JPL-grade calculations
- **Protocol**: [Model Context Protocol](https://modelcontextprotocol.io/) (MCP)

## Full Platform

Want AI-powered interpretations, reading history, gamification, and more?

- **Web App**: [pandorium.app](https://pandorium.app)
- **Telegram Mini App**: [t.me/pandorium_app_bot/app](https://t.me/pandorium_app_bot/app)

The MCP server provides raw mystical data. The full Pandorium platform adds:
- Deep AI-powered Jungian interpretations
- Reading history and Grimoire (card catalog)
- Oracle AI chat with memory
- Gamification: XP, levels, achievements, streaks
- Natal chart with interactive visualization
- Weekly Mirror and daily forecasts

## License

MIT
