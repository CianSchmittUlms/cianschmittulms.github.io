# My Zurich Map

A personal map for showing visitors around Zurich. Add your favorite spots, hiking trails, and local tips.

## File Structure

```
zurich-map/
├── index.html          ← The map (don't edit unless you want to change features)
├── README.md           ← You're reading it
└── data/
    ├── places.json     ← ✏️ EDIT THIS to add/change places
    └── trails/
        └── *.gpx       ← 📂 DROP GPX FILES HERE for hiking trails
```

---

## How to Add a New Place

Open `data/places.json` and add a new entry to the `"places"` array:

```json
{
  "name": "Restaurant Name",
  "category": "restaurant",
  "lat": 47.3750,
  "lng": 8.5400,
  "description": "Short description for popup",
  "rating": 4,
  "notes": "Your personal tips"
}
```

### Required Fields
| Field | Description |
|-------|-------------|
| `name` | Display name |
| `category` | One of: `hiking`, `restaurant`, `transport`, `grocery`, `activity` |
| `lat` | Latitude (get from Google Maps - right click → "What's here?") |
| `lng` | Longitude |

### Optional Fields
| Field | Description |
|-------|-------------|
| `description` | Shows in popup |
| `notes` | Your personal tips (shows as "Note: ...") |
| `rating` | 1-5 stars |
| `website` | URL - adds "Visit website" link |
| `gpxFile` | Filename of GPX track in `data/trails/` folder |

---

## How to Add a Hiking Trail

### Option 1: Link GPX to a place marker
1. Put your `.gpx` file in `data/trails/`
2. Add a place entry with `"gpxFile": "your-trail.gpx"`

```json
{
  "name": "Uetliberg Ridge",
  "category": "hiking",
  "lat": 47.3493,
  "lng": 8.4919,
  "description": "Ridge walk with views",
  "gpxFile": "uetliberg-ridge.gpx"
}
```

### Option 2: Import directly in browser
Use the "Import GPX file" button on the map (temporary, won't persist after reload).

---

## How to Get Coordinates

**Google Maps:**
1. Right-click on the location
2. Click "What's here?"
3. Copy the coordinates from the popup (lat, lng)

**OpenStreetMap:**
1. Right-click → "Show address"
2. Or check the URL which contains lat/lng

---

## Customization

### Change map center/zoom
Edit the `meta` section in `places.json`:

```json
"meta": {
  "title": "My Zurich Map",
  "center": [47.3769, 8.5417],
  "zoom": 13
}
```

### Add a new category
Edit `CATEGORIES` in `index.html`:

```javascript
const CATEGORIES = {
    hiking:     { color: '#2d5a27', icon: '🥾', name: 'Hiking' },
    restaurant: { color: '#e74c3c', icon: '🍽️', name: 'Restaurant' },
    // Add yours here:
    bar:        { color: '#8e44ad', icon: '🍺', name: 'Bars' },
};
```

---

## Hosting

### GitHub Pages (free)
1. Create a GitHub repo
2. Push these files
3. Go to Settings → Pages → Enable
4. Your map is live at `https://yourusername.github.io/reponame`

### Netlify (free, drag-and-drop)
1. Go to netlify.com
2. Drag the `zurich-map` folder onto the page
3. Done!

---

## Example places.json

```json
{
  "meta": {
    "title": "My Zurich Map",
    "center": [47.3769, 8.5417],
    "zoom": 13
  },
  "places": [
    {
      "name": "Hiltl",
      "category": "restaurant",
      "lat": 47.3727,
      "lng": 8.5365,
      "description": "World's oldest vegetarian restaurant",
      "rating": 4,
      "notes": "Great lunch buffet",
      "website": "https://hiltl.ch"
    },
    {
      "name": "Uetliberg Summit",
      "category": "hiking",
      "lat": 47.3493,
      "lng": 8.4919,
      "description": "Zurich's local mountain",
      "rating": 5,
      "gpxFile": "uetliberg-ridge.gpx"
    }
  ]
}
```
