# 📊 Stock-Info-Scraper

## Overview

**Stock-Info-Scraper** is a lightweight Python tool for scraping real-time stock data from [Groww US Stocks](https://groww.in/us-stocks) pages. It extracts current price, daily change, and volume for a list of popular U.S. stocks and exports the results to a CSV file.

This tool is useful for retail investors, analysts, or hobbyists looking to collect stock market snapshots without relying on paid APIs.

---

## System Architecture

### Frontend Architecture

- **Interface**: Command-line interface (CLI)
- **User Interaction**: Terminal output with progress messages
- **Output**: Structured CSV file named `stocks.csv`

### Backend Architecture

- **Core Logic**: Python script using `requests` and `BeautifulSoup`
- **Scraping Engine**: HTML parsing with fallback handling
- **Data Export**: Uses `pandas` for data formatting and CSV export
- **Rate Limiting**: Random sleep between requests to reduce risk of blocking

---

## Key Components

### Target URLs

The script scrapes data from the following stock pages on Groww:

```

[https://groww.in/us-stocks/nke](https://groww.in/us-stocks/nke)
[https://groww.in/us-stocks/aapl](https://groww.in/us-stocks/aapl)
...

````

Modify or extend the `urls` list in the script to add more stocks.

### Scraping Fields

- **Company**: Name of the stock/brand
- **Price**: Current market price
- **Change**: Day's change in price and percentage
- **Volume**: Trading volume (if available)

### Rate Limiting

To mimic human-like behavior and avoid being blocked, a `sleep` delay is randomly chosen between 2 and 5 seconds after each request.

---

## Example Output

| Company       | Price  | Change       | Volume     |
|---------------|--------|--------------|------------|
| Apple Inc.    | $190.75| +1.56 (0.82%)| 42.1M      |
| Nike Inc.     | $103.20| -0.92 (0.88%)| 17.5M      |

All results are saved in a file named `stocks.csv` after the script finishes scraping.

---

## Setup Instructions

### ✅ Requirements

- Python 3.7+
- Internet connection (script scrapes live web pages)

### 📦 Installation

1. Clone this repository:

```bash
git clone https://github.com/yourusername/Stock-Info-Scraper.git
cd Stock-Info-Scraper
````

2. Install the dependencies:

```bash
pip install -r requirements.txt
```

> Sample `requirements.txt`:

```
requests
beautifulsoup4
pandas
```

3. Run the scraper:

```bash
python scraper.py
```

4. View the results in the generated `stocks.csv` file.

---

## Customization

* 🏦 Add or remove stocks by editing the `urls` list inside the script.
* ⏱️ Adjust delay times with `time.sleep(random.uniform(2, 5))` if needed.
* 🗂️ Change the output filename by modifying `df.to_csv('stocks.csv')`.

---

## Limitations

* Depends on the current Groww HTML structure — may break if they redesign.
* Not suitable for high-frequency or commercial scraping.
* Scrapes visible data only — no JavaScript-rendered content.

---

## License

This project is licensed under the **Apache License 2.0**.

