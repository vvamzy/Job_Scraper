# Job Scraper with Clickable Links in Excel

This project is a web scraping tool that extracts job listings from
[Naukri.com](https://www.naukri.com), specifically targeting roles that match a
desired experience range. It uses **Selenium** to drive a real Chrome browser
(which Naukri's bot detection expects) and **BeautifulSoup** for HTML parsing.
The extracted data is saved in an **Excel workbook (.xlsx)** with clickable job
titles that link directly to each job posting.

## Features

✅ **Experience-Based Filtering:** Keeps only listings where your years of
experience (default: 4 Yrs) fits inside the advertised range — e.g. `2-5 Yrs`
passes, `6-11 Yrs` does not.  
✅ **Clickable Job Titles:** Every job title is a real hyperlink in Excel —
single click opens the posting.  
✅ **Comprehensive Data Extraction:** Captures job titles, company names,
ratings, experience requirements, locations, minimum requirements, and tech
stacks.  
✅ **Excel Export:** Neatly formatted `.xlsx` output with filters, frozen header
row, and border styling.  
✅ **Robust Error Handling:** Skips incomplete entries, dedupes listings, dumps
page HTML for debugging, and filters by experience.

## Installation

1. Clone the repository:

```
git clone https://github.com/vvamzy/Job_Scraper.git
cd Job_Scraper
```

2. Install dependencies:

```
pip install -r requirements.txt
```

3. Install **Google Chrome** (the script downloads a matching ChromeDriver
automatically via `webdriver-manager`).

## Usage

```
python job_scraper.py                          # python jobs, pages 1-5, 4 yrs exp
python job_scraper.py --query "data engineer" --pages 1 3 --experience 4
python job_scraper.py --query "devops" --pages 1 10 --experience 2 --output devops_jobs.xlsx
```

Options:

| Flag | Default | Description |
| --- | --- | --- |
| `--query` | `python` | Search keyword(s) |
| `--pages START END` | `1 5` | Page range to scrape |
| `--experience N` | `4` | Your years of experience; listings that don't cover this range are skipped |
| `--output FILE` | `filtered_jobs.xlsx` | Output Excel file |
| `--headless` | off | Run Chrome without a visible window |

Results are saved to the file given by `--output` (default
`filtered_jobs.xlsx`). Open it in Excel — the blue underlined job titles are
clickable links.

## How it works

- Naukri blocks plain HTTP requests and flags bare Selenium drivers, so the
  script launches real Chrome with anti-detection flags (hidden automation
  banner, neutralized `navigator.webdriver`, human-like scrolling pauses).
- Each page's job cards are parsed with fallback selectors for both the current
  and the classic Naukri markup.
- Experience check: `3-5 Yrs` with target `4` → kept; `6-11 Yrs` with target
  `4` → skipped. `Fresher`/`Entry level` listings only pass when the target is
  `0`.
- If a page yields no job cards, the raw HTML is dumped to
  `page_<n>_debug.html` for inspection.

## Dependencies

- **Selenium** (automated browser control)
- **BeautifulSoup** (HTML parsing)
- **WebDriver Manager** (automatic ChromeDriver management)
- **openpyxl** (Excel output with hyperlinks)

## Excel Output Columns

| Column | Example |
| --- | --- |
| Job Title (clickable) | Python Software Developer |
| Company Name | Capgemini |
| Rating | 3.6 |
| Experience | 6-11 Yrs |
| Location | Hyderabad, Pune, Bengaluru |
| Minimum Requirements | Strong experience with Python... |
| Tech Stack | API, Django, Cloud, FastAPI |
| Job Link | https://www.naukri.com/job-listings-... |

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an
issue.

## License

This project is licensed under the **MIT License**.