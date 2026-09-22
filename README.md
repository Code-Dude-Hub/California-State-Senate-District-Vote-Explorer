# California State Senate — District & Vote Explorer

An interactive, single-page California State Senate district explorer designed as a public civic-information demo.

The site lets visitors explore all 40 California State Senate districts on an interactive map, view district and senator information, filter districts by party, inspect recent floor-vote information, and look up a California street address to determine which Senate district contains that location.

## Features

- Interactive map of California's 40 State Senate districts
- Official district boundary data loaded from California public GIS services
- Esri topographic basemap beneath transparent district overlays
- Mouse, touch, drag, pinch, and wheel zoom controls
- District selector for Districts 1–40
- Party filter for Democratic, Republican, and vacant seats
- Senator name, district region, official portrait, office contacts, and official links
- Recent Senate floor-vote summaries with links to California Legislative Information
- California street-address lookup using the U.S. Census Geocoder
- Responsive desktop and mobile layouts
- Keyboard-accessible district interactions
- Content Security Policy and outbound-link allowlisting
- Runtime error logging and validation for remote map geometry
- No framework, package manager, build process, or backend required

## Tech

This project intentionally stays small and portable:

- HTML5
- CSS
- Vanilla JavaScript
- SVG for district rendering
- Public GeoJSON/GIS services
- U.S. Census Geocoder
- Esri raster map tiles

Everything required to run the application is contained in `index.html`; the map and public-data resources are loaded at runtime from the allowed external sources.

## Repository Layout

```text
.
├── index.html                 # Complete application / GitHub Pages entry point
├── README.md                  # Project overview
├── DEPLOYMENT.md              # GitHub Pages deployment instructions
├── DATA_SOURCES.md            # External public-data sources used by the app
├── PRIVACY.md                 # Address-lookup and third-party request disclosure
├── SECURITY.md                # Security design and vulnerability reporting
├── CONTRIBUTING.md            # Contribution and data-quality rules
├── .nojekyll                  # Serve the repo as a plain static site
├── .gitignore
└── .github/
    └── ISSUE_TEMPLATE/
        └── bug_report.yml


## Data Freshness

The application contains a dated roster/contact/vote snapshot in the JavaScript source. District geometry is fetched at runtime from public GIS endpoints.

Before publishing a new snapshot:

1. Verify the California Senate roster against the official Senate website.
2. Verify district links and contact information.
3. Verify any displayed bill title, vote date, vote result, and member vote against California Legislative Information.
4. Update the snapshot date shown by the application.
5. Test all 40 districts on desktop and mobile.

See [DATA_SOURCES.md](DATA_SOURCES.md) for the source policy.

## Privacy

The application does not require an account. Address lookup sends the entered address to the U.S. Census Geocoder so that coordinates can be returned and matched against the district geometry in the browser.

The current application does not intentionally use cookies, browser local storage, or analytics. External services used for GIS data, map tiles, official images, and address geocoding may receive normal request metadata such as IP address, user agent, referrer behavior allowed by the page, and requested resource.

## Neutrality / Civic Information

This project is intended to present public legislative information in a neutral, factual format. Contributions should not add endorsements, candidate advocacy, persuasion, fundraising, partisan slogans, or subjective ratings of legislators or political parties.

Corrections to public records are welcome when accompanied by an official source.

## Known Limitations

- The application depends on several third-party public services. A service outage, CORS policy change, URL change, or rate limit can temporarily affect map geometry, tiles, portraits, or address lookup.
- Senator/contact/vote data embedded in the HTML is a snapshot and must be updated manually unless a future data pipeline is added.
- The address lookup identifies the district using returned coordinates and the currently loaded district geometry; users should use official election/local-government resources when they need authoritative voter-registration or election-administration information.
- A static GitHub Pages deployment cannot replace server-side monitoring or a backend data-validation pipeline.

## License

 Apache-2.0

## Disclaimer

This is an independent civic-information project and is not an official website of the California State Senate, the California Legislature, the U.S. Census Bureau, Esri, or the State of California.

Always follow the linked official sources for authoritative legislative records and current office information.
