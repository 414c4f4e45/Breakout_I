# Google Maps Scraper

## Overview

This Python script uses Selenium to scrape data from Google Maps. It searches for businesses or places based on a specified keyword and geographic coordinates, then extracts information such as name, rating, address, phone number, website, hours, and top 9 reviews. The scraped data is saved into CSV and JSON files.

## Requirements

- Python 3.x
- Selenium
- ChromeDriver (compatible with your version of Chrome)

### Install Dependencies

Make sure you have the required Python packages installed. You can install them using pip:

```bash
pip install selenium
```
## Notes
- Headless Mode: The script runs Chrome in headless mode for background operation. You can remove --headless from self.options.add_argument if you need to see the browser window during execution.
- XPATHS: The script uses XPaths to select elements because Google Maps employs dynamic class names for its elements. By using XPaths, the script can access elements based on their hierarchical position and structure within the DOM. This approach ensures that even if the class names change, the script can still locate elements based on their position and relationship to other elements in the page's structure.

## How the Code Works

1. **Initialization**:
   - **Instantiated the Scraper**: An instance of `GoogleMapsScraper` was created with the search `keyword` and geographic coordinates (`lat`, `lon`).
   - **Generated URL**: The URL for the Google Maps search was constructed using the keyword and coordinates.
   - **Set Up Browser Options**: Chrome browser options were configured for headless mode, window size, and other settings.

2. **Scrolled Page**:
   - **Located Scrollable Div**: The element on the page that contained the scrollable results was identified.
   - **Executed Scrolling Script**: JavaScript was used to continuously scroll through the results until the end of the scrollable area was reached.

3. **Extracted Data**:
   - **Found Result Items**: All individual result items on the page were located.
   - **Iterated and Extracted**: For each item:
     - **Scrolled into View**: The item was scrolled into view if necessary.
     - **Clicked to Expand**: The item was clicked to reveal more details.
     - **Extracted Details**: Information such as the name, rating, address, phone number, website, hours, and reviews was collected using XPaths.

4. **Handled Errors**:
   - **Used Try-Except Blocks**: Error handling was employed to manage situations where elements might not be found or actions might fail.

5. **Compiled Results**:
   - **Stored Data**: The extracted information for each item was appended to a results list.

6. **Wrote Files**:
   - **Saved to CSV**: The results were written to a CSV file, with review lists converted into a single string for each item.
   - **Saved to JSON**: The results were saved to a JSON file, with each item keyed by its name.

7. **Closed Browser**:
   - **Quit Browser**: The browser was closed once the scraping and data saving were completed.

8. **Executed**:
   - **Ran the Scraper**: The `run` method was called to perform the entire scraping process.
   - **Wrote Results**: After running the scraper, the `write_files` method was called to save the data to CSV and JSON files.

This sequence ensured that the information from Google Maps was effectively navigated, extracted, and saved.

