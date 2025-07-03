# ChatGPT-GPT-Prompt-Scraper
A Python-based web scraping tool designed to extract detailed information from ChatGPT prompt pages. This tool features undetected Chrome WebDriver for stealth, dynamic user-agent rotation, advanced image and link extraction, and seamless data integration into Excel.




## Features
- **Stealth Browsing**: Uses `undetected_chromedriver` to bypass anti-bot detection.
- **Dynamic User-Agent Rotation**: Mimics real browser behavior with randomized user agents.
- **Image Extraction**: Captures images, including DALL·E-generated content, with creation dates and prompts.
- **Link Extraction**: Extracts creator-related links (Website, LinkedIn, GitHub, X).
- **Excel Integration**: Reads URLs from an Excel file and saves scraped data into a new sheet.
- **GUI Support**: Uses Tkinter for file selection and user-friendly messages.

## Prerequisites
- Python 3.8+
- Required packages:
  ```bash
  pip install undetected-chromedriver openpyxl beautifulsoup4 selenium requests pillow lxml
  ```
- Google Chrome browser (compatible with `undetected_chromedriver`).
- A valid ChatGPT account (username and password).

## Installation
1. Clone or download this repository.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Ensure Google Chrome is installed and up-to-date.
4. Update `USERNAME` and `PASSWORD` in the script:
   ```python
   USERNAME = 'your_email@example.com'
   PASSWORD = 'your_password'
   ```

## Usage
1. Prepare an Excel file (`.xlsx`) with ChatGPT prompt URLs (starting with `https://chatgpt.com`) in any column from B onward and any row from 2 onward.
2. Run the script:
   ```bash
   python scraper.py
   ```
3. Select the Excel file via the file dialog.
4. The script will:
   - Log in to ChatGPT.
   - Scrape data (title, description, creator details, images, sample messages) from each URL.
   - Save results to a new `ScrapedData` sheet in the Excel file.
5. A success or error message will appear upon completion.

## Output
The `ScrapedData` sheet contains:
- **Retrieved Date**: Scraping date (YYYY-MM-DD).
- **Retrieved Time**: Scraping time (HH:MM:SS).
- **URL**: Source URL.
- **Images**: Image URL (if any).
- **DALL-E**: `YES` or `NO` for DALL·E-generated images.
- **Image Creation**: Image creation date (MM-DD-YYYY, if applicable).
- **DALL-E Prompt**: DALL·E prompt text (if applicable).
- **Title**: Prompt page title.
- **Creator**: Creator’s name.
- **Creator Website**: Creator’s website link.
- **Creator LinkedIn**: Creator’s LinkedIn profile.
- **Creator GitHub**: Creator’s GitHub profile.
- **Creator X**: Creator’s X (Twitter) profile.
- **Description**: Prompt description.
- **Sample Message 1-3**: Sample messages.
- **Prompt**: Main prompt text.

## Notes
- **Headless Mode**: Set `options.headless = True` for background execution (default is `False`).
- **Delays**: Random delays (3-6 seconds) prevent detection. Adjust `time.sleep()` if needed.
- **Error Handling**: Handles login failures, image download issues, and scraping errors. Check console for details.
- **Proxy Support**: Add a proxy in `initialize_webdriver` if needed.

## Limitations
- Requires a valid ChatGPT account.
- Image extraction depends on filename patterns, which may not always be accurate.
- Assumes specific ChatGPT page structure; updates to the site may break the script.

## Troubleshooting
- **Login Issues**: Verify credentials and check for changes in the login page.
- **WebDriver Errors**: Ensure Chrome and `undetected_chromedriver` versions are compatible.
- **Excel Errors**: Close the Excel file in other programs before running.
- **Image Download Failures**: Check internet connection or increase delays.

## License
MIT License. See `LICENSE` file for details.

