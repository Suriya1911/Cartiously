# Cartiously

**Compare grocery prices across stores in seconds.**

Cartiously reads grocery store flyers using AI, pulls out every product and price, and shows you where each item is cheapest.

## 👉 https://cartiously-ezw5ulrdgnall262d5zn3y.streamlit.app/

No download or sign-up needed. It runs in your browser.

---

## How to Use It

1. **Upload:** drag your flyer images (PNG, JPG, JPEG, GIF, BMP), or one ZIP file of flyers, into the upload box.
2. **Analyze:** click **ANALYZE FLYERS**. Each flyer takes about 5 seconds. Leave the page open while it works.
3. **Review:** look through the three tabs:
   - **Stores Overview:** every store found, with contact details
   - **Products Catalog:** every product and price
   - **Price Comparisons:** products sold at more than one store
4. **Download:** click **DOWNLOAD EXCEL REPORT** to save everything as a spreadsheet.
5. **Search:** scroll to **Quick Product Search**, type items separated by commas (for example `milk, eggs, bread`), and click **SEARCH**.

**Tip:** use clear, high-resolution flyer images for the best results.

**Note:** the live app runs on a free AI plan with a daily limit. If flyers fail with a quota error, please try again the next day.

---

## Features

- Upload flyers one by one or all at once in a ZIP file
- AI extraction of store name, contact details, products, prices, and sizes
- Multi-item search with smart matching, so "car" does not match "Carrots" but "blueberry" still matches "Blueberries"
- Price comparison chart for each item, with the best deal, the highest price, and how much you save
- Excel report with three sheets: Stores, Products, and Price Comparisons

---

## How It Works

1. Each flyer image is sent to the Google Gemini vision model with a structured prompt.
2. The response is parsed into clean records. Prices and sizes are extracted in both metric and imperial units, placeholder values are removed, and product names are standardized so the same item always looks the same.
3. The cleaned data powers the search, the charts, and the Excel report.

### Built for reliability

Free AI services have strict limits, so the app is designed to handle them:

- Retries automatically when Google's servers are busy, waiting a little longer each time
- Does not retry when the daily limit is reached, since that would only waste the remaining allowance
- Retries failed flyers in up to 3 rounds
- Spaces requests 5 seconds apart to stay under the limit of 15 requests per minute
- Shows each failed flyer with the exact reason, instead of silently skipping it

### Tech stack

Python, Streamlit, Google Gemini API, pandas, Plotly, openpyxl, Pillow

---

## Planned Improvements

- **Smarter product grouping:** compare "Organic Milk" and "Organic Eggs" separately instead of grouping them by their first word
- **Unit-price comparison:** show price per litre or per kg, so a 1 L and a 4 L product are compared fairly
- **Stricter price detection:** make sure a size value is never read as a price when a flyer has no dollar sign

---

## Run It on Your Own Computer (Optional, for Developers)

<details>
<summary>Click to expand setup steps</summary>

**You will need:** Python 3.10 or newer and a free [Gemini API key](https://aistudio.google.com/app/apikey).

1. Clone the repository:
   ```
   git clone https://github.com/Suriya1911/Cartiously.git
   cd Cartiously
   ```
2. Install the dependencies:
   ```
   python -m pip install -r requirements.txt
   ```
3. Create your key file by copying the template:
   - Windows: `copy .env.template .env`
   - Mac: `cp .env.template .env`
4. Open `.env` and replace `your_api_key_here` with your own key.
5. Run the app:
   ```
   python -m streamlit run app.py
   ```
6. It opens in your browser at **http://localhost:8501**.

Mac users: use `python3` instead of `python`.

</details>

---

## Author

Built by **Suriya Prabha**. [Connect on LinkedIn](https://www.linkedin.com/in/YOUR-PROFILE)
