# Graph Schema

Use this file when the user asks for a relationship map, system graph, supply-chain graph, source graph, or 2.0-style output.

## Goal

Represent a Serenity-style thesis as a graph instead of a plain ticker list.

## Node Types

Use these five node groups:

- **End system**: AI factory, GB300 NVL72 rack, TPU pod, 1.6T optical link, robot platform, data-center power train.
- **Component or function layer**: laser, InP substrate, memory, CPO module, advanced packaging, liquid cooling, power distribution, materials, test.
- **Company**: supplier, customer, foundry, integrator, competitor, test vendor, distributor.
- **Evidence**: filing, earnings-call transcript, exchange document, company announcement, patent, standard, official order, regulator/project document, reputable industry article.
- **Catalyst**: earnings date, qualification finish, capacity expansion, first shipment, policy event, customer onboarding, supplier-list change.

## Edge Types

Keep the graph simple:

- `supplies`
- `depends_on`
- `competes_with`
- `confirmed_by`
- `likely_benefits_from`
- `catalyzed_by`
- `weakens_if`

## Minimum Graph Standard

A strong graph should include:

1. one end system or demand driver;
2. two to five critical component layers;
3. three to eight companies;
4. at least two evidence nodes;
5. at least one catalyst or failure-condition node.

## Evidence Tags

Tag major graph claims as:

- `Confirmed`: backed by filings, official documents, transcripts, IR materials, contracts, patents, standards, or regulator/project records.
- `Inferred`: logical cross-chain inference from multiple sources, but not directly disclosed.
- `Weak`: supported by reputable secondary reporting or limited evidence.
- `Needs verification`: social, forum, rumor, dated, or single-source lead.

## Text Output Shape

```text
End system:
- ...

Critical layers:
- ...

Companies:
- ...

Evidence links:
- Company A -> supplies -> Layer B [Confirmed]
- Layer B -> depends_on -> Component C [Inferred]
- Company A -> confirmed_by -> Q2 transcript [Confirmed]

Catalysts and failure checks:
- Company A -> catalyzed_by -> qualification milestone
- Thesis -> weakens_if -> customer dual-sources faster than expected
```

## JSON Shape

```json
{
  "nodes": [
    {"id": "ai_factory", "type": "end_system", "label": "AI factory"},
    {"id": "inp", "type": "component", "label": "InP substrate"},
    {"id": "axti", "type": "company", "label": "AXTI"},
    {"id": "filing", "type": "evidence", "label": "10-K supplier disclosure"},
    {"id": "qual", "type": "catalyst", "label": "customer qualification update"}
  ],
  "edges": [
    {"from": "ai_factory", "to": "inp", "type": "depends_on", "evidence": "Inferred"},
    {"from": "axti", "to": "inp", "type": "supplies", "evidence": "Confirmed"},
    {"from": "axti", "to": "filing", "type": "confirmed_by", "evidence": "Confirmed"},
    {"from": "axti", "to": "qual", "type": "catalyzed_by", "evidence": "Needs verification"}
  ]
}
```
