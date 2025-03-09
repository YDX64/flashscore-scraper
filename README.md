# Flashscore Odds Scraper

A robust web scraper designed to extract match odds data from Flashscore with enhanced resilience against website changes and anti-scraping measures.

## Features

- Extracts match details and odds from Flashscore
- Supports multiple odds types (1X2, Over/Under, Asian Handicap, Both Teams to Score, etc.)
- Reliable decimal format setting with multiple fallback methods
- Advanced error handling with retry mechanisms
- Variable wait times to appear more human-like
- Comprehensive debugging with screenshots and HTML source saving
- Stores data in CSV files or PostgreSQL database (optional)
- Multiple running modes with direct API support

## Key Improvements

- Fixed invalid CSS selector errors
- Added connection error handling with retry mechanism (3 retries with increasing wait times)
- Implemented browser restart capability when connection issues persist
- Increased wait times between actions to avoid being blocked
- Added comprehensive debugging capabilities
- Improved JavaScript-based decimal format setting
- Implemented variable wait times between matches (5-9 seconds)

## Requirements

- Python 3.9+
- Internet connection
- PostgreSQL database (optional)

## Installation

1. Clone this repository:
```
git clone https://github.com/YDX64/flashscore-scraper.git
cd flashscore-scraper
```

2. Create a virtual environment and install dependencies:
```
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

3. Set up PostgreSQL database (optional):
- Install PostgreSQL if not already installed
- Create a new database named `flashscore`
- The tables will be created automatically when the script runs

4. Configure environment variables:
- Copy the `.env.example` file to `.env`
- Update the database connection details in the `.env` file

## Usage

### Running the scraper

You can use one of the provided batch files to run the scraper:

```
run_scraper.bat             # Run the default scraper
run_selenium_scraper.bat    # Run the Selenium-based scraper
run_direct_api_scraper.bat  # Run the direct API-based scraper
test_fixes.bat              # Test browser tools integration
```

Or run Python scripts directly:

```
python main.py              # Main entry point with scheduling
python process_matches_file.py # Process matches from file
```

### Configuration

You can configure the following settings in the `.env` file:

- `DB_HOST`: PostgreSQL host (default: localhost)
- `DB_PORT`: PostgreSQL port (default: 5432)
- `DB_NAME`: Database name (default: flashscore)
- `DB_USER`: Database username (default: postgres)
- `DB_PASSWORD`: Database password
- `UPDATE_INTERVAL`: Time between updates in minutes (default: 15)
- `ODDS_UPDATE_INTERVAL`: Time between odds updates in minutes (default: 30)

## Project Structure

- `flashscore_crawler.py`: Core crawler implementation for browser interactions
- `process_matches_file.py`: Script to process matches from file
- `main.py`: Entry point with scheduling capabilities
- `match_collector.py`: URL management
- `debug_tools.py`: Browser debugging tools
- `database.py`: Optional database storage
- `yeni_oran.py`: Enhanced odds scraper with improved resilience
- `requirements.txt`: Dependencies including crawl4ai, selenium, undetected-chromedriver, and pandas
- `run_*.bat`: Batch files to run the scraper in different modes

## Troubleshooting

If you encounter any issues:

1. Check the debug files in the `debug_info/` directory
2. Look for saved screenshots for visual debugging
3. Ensure your internet connection is stable
4. Verify that the website structure hasn't changed dramatically

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [Crawl4AI](https://docs.crawl4ai.com/) - Web crawling library
- [Selenium](https://www.selenium.dev/) - Browser automation
- [undetected-chromedriver](https://github.com/ultrafunkamsterdam/undetected-chromedriver) - Anti-detection for Selenium
- [Flashscore](https://www.flashscore.com/) - Data source