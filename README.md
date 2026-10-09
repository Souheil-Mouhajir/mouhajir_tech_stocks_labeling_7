# Labels, annotations and tables: five technology share prices, 2000 to 2010

This project follows the monthly share prices of five technology companies (Apple, Amazon, Google, IBM, Microsoft) from January 2000 to March 2010, a decade with two crashes: the end of the dot-com boom and the 2008 financial crisis. It is the Week 7 assignment of DATS 2102 Data Visualization, on titles, annotations, direct labels and formatted tables. The data is the stocks file of the vega-datasets collection.

Author: Souheil Mouhajir, The George Washington University, Elliott School of International Affairs. October 2026.

[View the rendered report](https://souheil-mouhajir.github.io/mouhajir_tech_stocks_labeling_7/) · [View the notebook](https://github.com/Souheil-Mouhajir/mouhajir_tech_stocks_labeling_7/blob/main/tech_stocks_labeling.ipynb)

## Findings

- Apple's share price fell 79 percent in the first crash, from $33.95 in March 2000 to $7.07 in March 2003. It reached $223.02 in March 2010, more than thirty times the 2003 low.
- The 2008 crisis took Apple from $198.08 in December 2007 to $85.35 in December 2008, a fall of 57 percent in twelve months. By March 2010 the price was above the 2007 peak.
- Indexed to August 2004 = 100, the five companies ended March 2010 at 1,293 (Apple), 547 (Google), 338 (Amazon), 161 (IBM) and 128 (Microsoft).
- Amazon had the deepest fall of the five, 91 percent to September 2001, and still doubled its January 2000 price by March 2010.
- Microsoft is the only company that ended below where it started, at $28.80 against $39.81 in January 2000. Its peak, $43.22, dates from March 2000.
- Google's worst fall, 59 percent to November 2008, is the only one recorded entirely inside the financial crisis.

## Charts

The core of the report is two charts and one table. The first chart is Apple's price over the whole decade, with three annotations: the March 2003 low, the iPhone release in June 2007 and the Lehman Brothers bankruptcy in September 2008. The second chart indexes the five companies to August 2004 on a log scale and labels each line at its right end with the company name and its March 2010 value, with no legend. The table, built with great_tables, gives the first and last prices, the change over the series, the peak and the worst drawdown of each company. Three optional extensions follow. The first plots Amazon with `matplotlib.offsetbox` callouts (`AnnotationBbox` and `AnchoredText`) and a source line placed in axes coordinates. The second plots Microsoft on a grey line and ranks its annotations by color and font weight, with a band over the financial crisis. The third rebuilds the summary table as a styled pandas DataFrame and exports it to LaTeX in `summary_table.tex`. A reflection of 192 words on the labeling and table choices closes the report.

## Repository contents

| File | Content |
|---|---|
| `tech_stocks_labeling.ipynb` | Jupyter notebook of the analysis, saved with its outputs |
| `tech_stocks_labeling.html` | Rendered report, self-contained |
| `summary_table.tex` | Summary table exported to LaTeX from a styled pandas DataFrame; compiles with `\usepackage[table]{xcolor}` |
| `stocks.csv` | Monthly share prices of the five companies, January 2000 to March 2010 |
| `requirements.txt` | Python packages with pinned versions |
| `theme.scss`, `theme-dark.scss` | Light and dark themes for the HTML output, with the Source Sans Pro font embedded |
| `index.html` | Redirects the GitHub Pages address to the rendered report |
| `.gitattributes` | Marks the HTML as generated, so GitHub lists the repository as a Jupyter Notebook project |

## Data

`stocks.csv` is the stocks file of the vega-datasets collection, published as vega/vega-datasets on GitHub (<https://github.com/vega/vega-datasets/blob/main/data/stocks.csv>). It has 560 rows in three columns, `symbol`, `date` and `price`, each row the share price in US dollars of one company in one month. Apple, Amazon, IBM and Microsoft have 123 months each. Google has 68, from August 2004, the month of its initial public offering.

The copy in this folder was written from the version bundled with the `vega_datasets` Python package, with dates in ISO format.

## Reproducing the report

The notebook reads `stocks.csv` from the same folder and has no manual steps or random numbers, so rendering works offline. The LaTeX extension writes `summary_table.tex` next to the notebook. The steps below need Python 3 and Quarto (the run that produced the HTML used Python 3.13.16 and Quarto 1.10.19).

```
pip install -r requirements.txt
quarto render tech_stocks_labeling.ipynb --execute
```

The notebook also runs on its own in Jupyter with `jupyter notebook tech_stocks_labeling.ipynb`. The HTML loads the Source Sans Pro font from Google Fonts and the jQuery and require.js scripts that Quarto adds to Jupyter pages. Without an internet connection the charts, the table and the table of contents still work, and the text falls back to the system sans serif font.

## Source

vega-datasets, `data/stocks.csv`, GitHub repository vega/vega-datasets, retrieved through the `vega_datasets` Python package, October 2026.
