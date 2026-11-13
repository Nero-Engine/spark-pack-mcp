# Spark Pack

Free tools a UK electrician's AI assistant uses on the job: cable size, voltage drop and Zs with the working shown, Part P notification, EIC, Minor Works and EICR checks, and G98, G99, EV and heat pump connection rules.

**Endpoint:** `https://spark-pack.nerolabs.workers.dev/mcp` (MCP, Streamable HTTP)
**Sign-in:** None. No account, no key and no sign-in: add the address and use it.
**How to connect:** https://spark-pack.nerolabs.workers.dev/docs
**Privacy:** https://spark-pack.nerolabs.workers.dev/privacy
**Support:** founder@neroengine.com

## Tools

| Tool | What it does |
|---|---|
| `list_capabilities` | What Spark Pack can do. Lists Spark Pack's tools, the regulations edition it targets, what it covers (nations, circuit types, cable types, installation methods) and what it deliberately does not do. |
| `size_cable` | Cable size, voltage drop and earth fault loop check. Sizes a UK final circuit or sub-main and shows the working: design current (with cooker diversity), protective device rating, the smallest cable size that passes current-carrying capacity, voltage drop (3% lighting, 5% other) and earth... |
| `check_part_p` | Is this job notifiable under Part P?. Answers whether domestic electrical work in England or Wales must be notified to building control under Part P of the Building Regulations, with the reason and what to do next (self-certify through a competent person scheme within 30 days,... |
| `get_certificate_schema` | Certificate fields as a JSON schema. Returns the fields an Electrical Installation Certificate (eic), Minor Electrical Installation Works Certificate (minor_works) or Electrical Installation Condition Report (eicr) needs, as a JSON Schema the assistant fills from the job... |
| `check_certificate` | Check a filled certificate. Checks a filled EIC, Minor Works certificate or EICR (shape from get_certificate_schema) and returns `ready_to_transfer`, every missing required field by path, errors (readings that fail: insulation resistance under 1 megohm at 500 V,... |
| `check_grid_connection` | G98, G99 or EV and heat pump notification?. For solar PV, batteries, V2G chargers, EV chargers and heat pumps in Great Britain: says which network operator process applies and when. |
| `trade_profile` | Check the electrician's business details. Checks the electrician's own business details (Nero Trade Profile v1: trading name, Companies House number, competent person scheme and number, postcode, contact) and returns them cleaned, with a stable `nero_trade_ref` computed from the... |

Every tool carries a plain title and the read-only, destructive and open-world hints, so your AI app can ask before anything that changes data.

## Connect

- **Claude (web or desktop):** Settings, Connectors, Add custom connector, paste the endpoint.
- **ChatGPT:** Settings, Apps and connectors, Advanced settings, switch on Developer mode, then Create, paste the endpoint, No authentication.
- **Claude Code:** `claude mcp add --transport http spark-pack https://spark-pack.nerolabs.workers.dev/mcp`
- **Cursor, VS Code, Windsurf and others:**

```json
{ "mcpServers": { "spark-pack": { "type": "http", "url": "https://spark-pack.nerolabs.workers.dev/mcp" } } }
```

## Try asking

- "Size the cable for a 9.5 kW shower on an 18 metre run, clipped to the wall, with a 0.35 ohm Ze."
- "I'm adding a socket in a kitchen in Cardiff. Is that notifiable under Part P?"
- "Check this EICR before I send it: circuit 3 has an insulation reading of 0.6 megohms and I've marked it satisfactory."

## Good to know

- Built for UK electricians. Every answer shows its working and sources and lists what the trade must check. The trade doing the work stays responsible for it.
- Free forever: no sign-up, no key, no daily cap, no paid plan.

## Privacy

What is kept, what is never kept, and how to get data deleted: https://spark-pack.nerolabs.workers.dev/privacy. Usage counts log the tool name, time, AI app name, country and a one-way scrambled caller code; never your questions, the answers or IP addresses.

This repository holds the listing only (README and server.json). The server runs at the endpoint above.

Built by Nero Labs (Nero Engine Group Ltd, UK).
