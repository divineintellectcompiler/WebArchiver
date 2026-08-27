# WebArchiver

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT) [![Python 3.10+](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/downloads/) [![PyQt6](https://img.shields.io/badge/GUI-PyQt6-green.svg)](https://www.riverbankcomputing.com/software/pyqt/)

A desktop web-scraping and research archiving application for searching, extracting, and organizing web pages, text, images, and videos.

## Features

* Search the web using multiple search terms
* Automatically fall back to alternative search providers when a provider fails
* Retrieve and extract readable text from web pages
* Collect page titles, descriptions, URLs, and search-result snippets
* Discover images and videos embedded in pages
* Optionally download discovered media locally
* Configure request delays and timeouts
* Configure result and page limits
* Run scraping tasks in the background without freezing the interface
* Monitor live progress and activity logs
* Stop an active scraping session
* Generate a searchable HTML research archive

## Requirements

* Python 3.10+
* PyQt6
* Requests
* BeautifulSoup4
* DDGS

## Installation

Clone the repository:

```bash
git clone https://github.com/USERNAME/WebArchiver.git
cd WebArchiver
```

Install the required dependencies:

```bash
pip install PyQt6 requests beautifulsoup4 ddgs
```

## Usage

Start WebArchiver:

```bash
python scraper.py
```

Enter one search term per line, select an output directory, configure the scraping options, and click **Start Scrape**.

WebArchiver processes the search terms, collects unique URLs, retrieves the pages, extracts their content, discovers available media, and stores the results in a local research archive.

## Output

Each research session creates an archive containing the collected research:

```text
web_archive/
├── archive.txt
├── index.html
├── images/
└── videos/
```

### HTML Archive

`index.html` provides an interactive interface for browsing the collected research.

It includes:

* Full-text search
* Search-query filters
* Source links
* Extracted page text
* Archived images
* Archived videos
* Failed-page indicators

### Text Archive

`archive.txt` contains a plain-text representation of the collected research.

Each archived page includes:

* Search query
* Page title
* URL
* Description
* Extracted text
* Downloaded media information

## Media

When media downloading is enabled, discovered images and videos are saved locally:

```text
images/
videos/
```

Downloaded files are assigned unique names derived from their source URLs to reduce filename collisions and prevent duplicate downloads.

## Search Backend Fallback

WebArchiver is designed to remain usable when an individual search provider is unavailable.

Search providers are attempted sequentially. If a provider times out, returns an error, or produces no usable results, WebArchiver automatically attempts the next available provider.

This allows a scraping session to continue even when one search backend is temporarily unavailable.

## Configuration

| Setting                        | Description                                                     |
| ------------------------------ | --------------------------------------------------------------- |
| **Results / search**           | Maximum number of search results requested for each search term |
| **Maximum pages**              | Maximum number of unique pages processed during a session       |
| **Delay**                      | Delay between HTTP requests                                     |
| **Timeout**                    | Maximum time allowed for an individual request                  |
| **Download images and videos** | Enables or disables local media downloading                     |

## How It Works

```text
Search terms
     │
     ▼
Search providers
     │
     ▼
Search results
     │
     ▼
URL deduplication
     │
     ▼
Page retrieval
     │
     ▼
HTML extraction
     │
     ├──────────────────┐
     ▼                  ▼
Text extraction    Media discovery
     │                  │
     │                  ▼
     │             Media download
     │                  │
     └────────┬─────────┘
              ▼
       Archive records
              │
        ┌─────┴─────┐
        ▼           ▼
   archive.txt  index.html
```

## Limitations

Not every website can be successfully archived.

Some websites may:

* Block automated requests
* Require JavaScript to render content
* Require authentication
* Generate content dynamically
* Restrict access to images or videos
* Return incomplete or unusual HTML
* Apply rate limits
* Depend on browser-specific behavior

WebArchiver does **not** attempt to bypass authentication, access controls, paywalls, or other technical restrictions.

## Responsible Use

WebArchiver is intended for legitimate research, archival, and information-gathering purposes.

When using the application, respect:

* Website terms of service
* Copyright and licensing restrictions
* Applicable privacy laws
* Server rate limits
* Robots policies where applicable
* Access restrictions

Only collect, download, and store content that you are permitted to access and archive.

## Project Structure

```text
WebArchiver/
├── scraper.py
├── README.md
├── LICENSE
└── screenshots/
```

The main application is currently contained in `scraper.py`.

## License

This project is licensed under the MIT License.

See `LICENSE` for the full license text.

## Disclaimer

WebArchiver is provided for legitimate research and archival purposes. The author is not responsible for how the software is used or for the content collected through it. Users are responsible for complying with applicable laws, website terms, copyright restrictions, privacy requirements, and access policies.
