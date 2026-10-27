# Flowcraft — n8n Workflow Templates

Flowcraft is a polished static portfolio and download library for practical [n8n](https://n8n.io/) workflow templates, created by [Nirav Gajera](https://niravgajera.indevs.in/).

The collection focuses on useful automations for AI support, finance, operations, sales, hospitality, and hiring.

## Included workflows

| Workflow | Category | What it does |
| --- | --- | --- |
| Telegram E-commerce Support | AI & support | Handles order tracking, cancellations, and support tickets through Telegram, Gemini, and Google Sheets. |
| AI Expense Tracker | AI & finance | Parses natural-language expenses, categorises them, and stores monthly totals in Google Sheets. |
| Jira Worklog Automation | Operations | Moves worklog entries from Google Sheets into Jira with validation and duplicate protection. |
| AI Real Estate Lead Qualifier | Sales & growth | Scores Typeform property leads, saves them to Airtable, and routes follow-up emails. |
| AI Restaurant Orders | Hospitality | Accepts conversational restaurant orders, updates Google Sheets, and notifies staff. |
| AI Resume Screener | Hiring & HR | Scores job applications with Gemini, updates the response sheet, and sends candidate emails. |

## Features

- Responsive Flowcraft portfolio UI
- Search and category filtering
- Workflow preview images with fullscreen lightbox
- Detailed workflow guides inside a modal
- Direct JSON downloads for every template
- Download behavior that works even when opening `index.html` locally
- Structured SEO metadata and JSON-LD
- Open Graph and Twitter preview metadata
- `robots.txt`, `sitemap.xml`, and web app manifest
- Mobile-friendly guide pages with consistent tables, steps, code blocks, and callouts

## Project structure

```text
.
├── index.html                         # Main portfolio and template catalogue
├── robots.txt                          # Search crawler rules
├── sitemap.xml                         # SEO sitemap
├── site.webmanifest                    # Web app metadata
├── templates/                          # Original n8n workflow JSON files
│   ├── ecom-support.json
│   ├── expense-tracker.json
│   ├── jira-worklog.json
│   ├── real-estate-lead.json
│   ├── restaurant-orders.json
│   └── screen-job-app.json
├── info/                               # Standalone workflow documentation
│   ├── ecom-support-info.html
│   ├── expense-tracker-info.html
│   ├── jira-worklog-info.html
│   ├── real-estate-lead-info.html
│   ├── restaurant-orders-info.html
│   └── screen-job-app-info.html
└── info/images/                        # Workflow preview images
```

## Run locally

The site has no build step or framework dependency. A local server is recommended because browser security rules can restrict local iframe and file behavior when opening an HTML file directly.

Using `npx`:

```bash
npx serve .
```

Then open the local URL shown by the server, usually `http://localhost:3000`.

Using Python:

```bash
python -m http.server 8000
```

Then visit `http://localhost:8000`.

## Adding a workflow

1. Add the n8n export to `templates/`.
2. Add a matching guide page to `info/` using the existing document structure.
3. Add the workflow screenshot to `info/images/`.
4. Add a metadata object to the `templates` array in `index.html`:

```js
{
  id: 'my-workflow',
  title: 'My Workflow',
  category: 'ai',
  tag: 'AI & automation',
  image: 'info/images/my-workflow.png',
  file: 'templates/my-workflow.json',
  guide: 'info/my-workflow-info.html',
  desc: 'A short, useful description of the workflow.',
  chips: ['n8n', 'AI', 'Google Sheets'],
  nodes: 12
}
```

5. Add the JSON content to the `embeddedWorkflows` download map in `index.html` so local downloads continue to work.
6. Add the guide URL to `sitemap.xml` and the workflow to the JSON-LD `ItemList`.
7. Test the card, image lightbox, Details modal, guide scrolling, and JSON download.

## Download implementation

The cards link to the matching files in `templates/`. The page also includes embedded workflow payloads so the download button creates a real `.json` download instead of navigating to a local `file:///` URL when the site is opened directly from disk.

When a workflow JSON changes, update both:

- The source file in `templates/`
- Its embedded payload in `index.html`

## SEO and deployment

The current SEO files assume this public URL:

```text
https://niravgajera.indevs.in/n8n-templates/
```

If the site is deployed elsewhere, update the URL in:

- `index.html` canonical metadata
- Open Graph URL and image metadata
- JSON-LD URLs
- `robots.txt`
- `sitemap.xml`
- `site.webmanifest` `start_url`

The project can be deployed to GitHub Pages, Netlify, Vercel static hosting, or any standard web server.

## Creator

- Portfolio: [niravgajera.indevs.in](https://niravgajera.indevs.in/)
- n8n Creator profile: [n8n.io/creators/niravgajera](https://n8n.io/creators/niravgajera/)

## License

No license file is currently included. Add a `LICENSE` file before distributing these workflow JSON files under an explicit open-source license.
