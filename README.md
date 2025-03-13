
# Job Scraper with Clickable Links in Excel

This project is a powerful web scraping tool designed to extract job listings from Naukri.com, specifically targeting roles that match a desired experience range. It leverages **Selenium** for dynamic content fetching and **BeautifulSoup** for HTML parsing. The extracted data is saved in a **CSV file** with clickable job titles that directly link to job postings for seamless navigation.

## Features
✅ **Experience-Based Filtering:** Filters job listings where 4 years of experience fits within the required range.  
✅ **Clickable Job Titles:** Each job title is formatted as a hyperlink in Excel for easy access.  
✅ **Comprehensive Data Extraction:** Captures job titles, company names, ratings, experience requirements, locations, minimum requirements, and tech stacks.  
✅ **CSV Export:** Neatly organized data saved as a `.csv` file for convenience.  
✅ **Robust Error Handling:** Skips incomplete entries and ensures data integrity.  

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/job-scraper.git
   cd job-scraper
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Install **Google Chrome** and **ChromeDriver** (matching your Chrome version).

## Usage
1. Run the script with:
   ```bash
   python job_scraper.py
   ```
2. The results will be saved in `filtered_jobs.csv`.
3. Open the file in **Excel** and ensure clickable links by following these steps:
   - Open Excel manually.
   - **File → Open → Select `filtered_jobs.csv`**

## Configuration
- The number of pages to scrape can be adjusted by modifying these lines in `job_scraper.py`:
  ```python
  start_page, end_page = 1, 5  # Change 5 to 400 for full scraping
  ```

## Dependencies
- **Selenium** (for automated browser control)
- **BeautifulSoup** (for HTML parsing)
- **WebDriver Manager** (to automatically manage ChromeDriver versions)

Install dependencies via:
```bash
pip install selenium beautifulsoup4 webdriver-manager
```

## CSV Output Format
The CSV file will include the following columns:
- **Job Title** (with clickable links)
- **Company Name**
- **Rating**
- **Experience**
- **Location**
- **Minimum Requirements**
- **Tech Stack**
- **Job Link** (for backup)

## Example CSV Output
| Job Title | Company | Rating | Experience | Location | Requirements | Tech Stack | Link |
|------------|---------|--------|-------------|-----------|----------------|-------------|--------|
| [DevOps Engineer](https://example.com) | XYZ Corp | 4.5/5 | 3-5 Yrs | Hyderabad | AWS, CI/CD | Python, Docker | https://example.com |

## Contributing
Contributions are welcome! Please feel free to submit a pull request or open an issue.

## License
This project is licensed under the **MIT License**.

## Contact
For questions, issues, or feature requests, feel free to reach out via GitHub Issues.
