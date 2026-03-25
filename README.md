# FieldQuote Templates

Community job templates for the [FieldQuote](https://github.com/prodirt-llc/fieldquote) Android app.

Templates are JSON files that pre-populate a job's line items with common tasks. Import them directly from the app via **Task Library → Browse Templates**.

---

## Template Format

### `index.json`
Lists all available templates. The app fetches this first to show the browse list.

```json
[
  { "id": "template-id", "name": "Display Name", "category": "Category" }
]
```

### `templates/{id}.json`
Individual template file. Line item types: `TIME_BASED`, `MATERIAL`, `FLAT_FEE`.

```json
{
  "id": "excavation-trench",
  "name": "Trench Excavation",
  "category": "Excavation",
  "description": "Standard utility or drainage trench with backfill and cleanup",
  "lineItems": [
    { "description": "Excavation — trench dig", "type": "TIME_BASED", "defaultHours": 2.0, "usesEquipment": true },
    { "description": "Backfill & compact", "type": "TIME_BASED", "defaultHours": 1.0, "usesEquipment": true },
    { "description": "Debris removal", "type": "MATERIAL", "defaultQuantity": 1.0, "defaultUnitCost": 50.0 },
    { "description": "Mobilization", "type": "FLAT_FEE", "defaultFlatAmount": 75.0 }
  ]
}
```

### Line item fields by type

| Type | Required fields |
|------|----------------|
| `TIME_BASED` | `defaultHours`, `usesEquipment` |
| `MATERIAL` | `defaultQuantity`, `defaultUnitCost` |
| `FLAT_FEE` | `defaultFlatAmount` |

---

## Categories

| Category | Templates |
|----------|-----------|
| Excavation | Trench, Pond/Basin, Foundation |
| Land Clearing | Light, Heavy, Trail Cutting |
| Grading | Driveway, Lot/Rough Grade |
| Landscaping | Stump Removal (Small/Large), Brush Clearing |
| Pressure Washing | House, Driveway, Deck/Patio |
| Drainage | French Drain |
| Hauling | Debris Hauling, Fill Delivery |
| Site Prep | Fence Post Holes |
| General | Hourly Labor, Labor with Equipment |

---

## Contributing

Pull requests welcome. To add a template:

1. Add your template JSON to `templates/`
2. Add an entry to `index.json`
3. Open a PR with a brief description of the trade/job type

Keep `defaultHours` realistic for an average job — users adjust them per job anyway. Hours are a starting point, not a quote.
