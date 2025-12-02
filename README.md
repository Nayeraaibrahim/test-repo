
# 🎬 Best Movies Scraper + Visualizer

This project scrapes a list of top-rated movies (title, year, Rotten Tomatoes score), saves the dataset as a CSV file, and visualizes the top results using a simple bar chart.

---

## ✅ Features

* Scrape movie data:

  * **Movie title**
  * **Release year**
  * **Rotten Tomatoes score**
* Store results in a Pandas DataFrame
* Export results to:

  * `best_movies_all_time.csv`
* Plot a **Top 10 Movies by Score** chart

---

## 🧰 Requirements

Install the needed libraries:

```bash
pip install requests beautifulsoup4 pandas matplotlib
```

---

## 🚀 How to Run

1. Open the notebook:

   * `GitHub_activity_code.ipynb`

2. Run all cells in order.

3. The notebook will:

   * scrape the data
   * build a DataFrame
   * show the first rows
   * generate a bar chart
   * save a CSV file

---

## 📊 Chart Output

After scraping and building the DataFrame, this section plots the **Top 10 movies** by Rotten Tomatoes score.

Example chart code (already in the notebook):

```python
top10 = data.sort_values("Score", ascending=False).head(10)

plt.figure(figsize=(10,5))
plt.barh(top10["Movie"], top10["Score"])
plt.gca().invert_yaxis()
plt.title("Top 10 Movies by Rotten Tomatoes Score")
plt.xlabel("Score (%)")
plt.ylabel("Movie")
plt.show()
```

---

## 📁 Project Structure

```
├── GitHub_activity_code.ipynb     # main scraper notebook + chart
├── best_movies_all_time.csv       # generated output after running notebook
└── top_movies_stats.py            # optional quick analysis script
```

---

## 🧪 Optional Extra Script

You can run the stats script after the CSV is created:

```bash
python top_movies_stats.py
```

It prints:

* total movies scraped
* oldest & newest year
* top 5 movies
* average score per decade

---

## 🛠 Troubleshooting

### **Length mismatch error**

If you see:

```
ValueError: Length of values (...) does not match length of index (...)
```

It means one scraped list is shorter than the others (common in scraping).
Fix by truncating to the smallest list:

```python
min_len = min(len(movies), len(years), len(scores))
movies, years, scores = movies[:min_len], years[:min_len], scores[:min_len]
```

---

## 📌 Notes

Scraping depends on the website structure.
If the site updates its HTML layout, the selectors may need adjustment.
