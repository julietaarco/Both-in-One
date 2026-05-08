# Both in One
### Artworks as Epistemic Proxies of Inner States — An Artistic Research Project

*By Julieta Arco*

---

## Overview

**Both in One** is part of **Data Canvas** — the line of Data Studio dedicated to the painting process.

Data Canvas rests on two foundations: the conceptual framework of Data Studio — the four modes of knowledge across Science and Art — and an operational framework that translates that model into a structured method of inquiry.

The method runs in two parallel streams. Through **ArtTelling**, each painting is made intuitively and holistically, and the work itself becomes an artistic artifact. Through **DataTelling**, the emotional, physical, and psychological states that accompany each session are recorded, translated, and analysed as analytical artifacts.

Data science methods are used to analyse both the artistic and analytical material, and model the relationships between them.

The painting carries information the numbers do not capture; the numbers carry information the painting does not show. Reading them together opens a third territory.

---

## Research Question

> *How can personal information — our states across time and space — be accessed and revealed through the combined use of art and science?*

---

## The Paintings

The dataset covers a series of hand-drawn and hand-painted works rendered in **pastel pencil on white Canson Mi-Teintes paper (50 × 65 cm)**. The paintings were developed from reference photographs of the artist's hands, taken intuitively. The creative process was unscheduled and spontaneous, allowing artistic decisions to emerge in response to internal and external states.

| Painting | Image Metrics | Self-report Data | Role |
|---|---|---|---|
| Both in One 1 (BiO1) | ✓ | — | Test case |
| Both in One 2 (BiO2) | ✓ | ✓ | Proxy (training) |
| Both in One 3 (BiO3) | ✓ | — | Test case |
| Both in One 4 (BiO4) | ✓ | ✓ | Proxy (training)  |

BiO2 and BiO4 serve as the **training proxies** — paintings for which both image metrics and self-report data were collected. BiO1 and BiO3 are used as **test cases** to evaluate whether the model built from BiO2/BiO4 can estimate inner states from image metrics alone.

---

## Methodology

The methodology follows a three-stage pipeline:

**1. Image data collection**
Photographs were taken after each painting session under standardized conditions: artificial lighting after 22:00, iPhone 14 (ISO 500, 26 mm, f/1.5, EV 0), 50 cm distance, PNG format.

**2. Image analysis** — `01_Image_Analysis.ipynb` (Python / Google Colab)
Quantitative metrics extracted from each stage photograph:
- Dominant colors — K-means clustering (k=5) in RGB space
- Color harmony — mean hue and hue standard deviation (HSV space)
- Stroke density — Canny edge detection (raw and normalized)
- Texture complexity — Local Binary Patterns (LBP standard deviation)
- Fractal dimension — box-counting method
- Spatial painting density — edge-based heatmaps (20×30 grid)

**3. Contextual data collection** — `02_Form.pdf` (Jotform)
Self-report data collected per stage via questionnaire, assessing physical, emotional, and psychological states (quantitative scales 1–10; free-text notes in Spanish).

**4. Statistical and sentiment analysis** — `03_Data_Analysis/` (R)
- Word frequency analysis and word clouds per stage
- Sentiment and emotion analysis — NRC Emotion Lexicon (`syuzhet`)
- Exploratory data analysis — distributions and temporal trajectories
- Pearson correlation analysis
- Hierarchical cluster analysis and heatmaps
- Principal Component Analysis (PCA)
- Partial Least Squares Regression (PLSR) with leave-one-out cross-validation

---

## Repository Structure

```
Both-in-One/
│
├── 01_Image_Analysis.ipynb       — Image analysis notebook (Google Colab)
│
├── 02_Form.pdf                   — Jotform questionnaire documentation
│
├── 03_Data_Analysis/             — R project
│   ├── 03_Data_Analysis.Rproj    — R project file
│   └── R/
│       ├── 03a_Text_and_Emotion_Analysis.Rmd    — Text and emotion analysis
│       ├── 03a_Text_and_Emotion_Analysis.html   — Rendered HTML output
│       ├── 03b_Statistical_Analysis.Rmd         — Statistical analysis
│       └── 03b_Statistical_Analysis.html        — Rendered HTML output
│
├── Data/
│   ├── BiO_form.csv              — Raw questionnaire data (exported from Jotform)
│   └── BiO_image.csv             — Image metrics (exported from Google Colab)
│
├── README.md
└── LICENSE                       — CC BY 4.0
```

---

## How to Explore This Project

**Option A:**

**— Read the HTML reports** *(interactive, no software required)*

Open the following files in any web browser (Chrome, Firefox, Edge):

- `03_Data_Analysis/R/03a_Text_and_Emotion_Analysis.html` — text preprocess, word frequency, emotion analysis
- `03_Data_Analysis/R/03b_Statistical_Analysis.html` — EDA, correlations, clustering, PCA, PLSR

The HTML versions are interactive — code sections can be expanded or collapsed.

**— Read the Colab notebook** *(no software required)*

Open `01_Image_Analysis.ipynb` directly on GitHub. The notebook renders automatically, showing the image analysis code.

**Option B: Run or modify the analysis** *(Python and R required)*

For the Python analysis:
1. Open `01_Image_Analysis.ipynb` in Google Colab *(File → Open notebook → GitHub)*
2. Update the `folder_path` variable to point to your image folder in Google Drive
3. Run all cells in order

For the R analysis:
1. Install R and RStudio if not already installed:
   - R: https://cran.r-project.org
   - RStudio: https://posit.co/download/rstudio-desktop
2. Clone or download this repository
3. Open `03_Data_Analysis/03_Data_Analysis.Rproj` in RStudio
4. Run the notebooks in order: `03a` first, then `03b`

---

## Tools and Libraries

**Python** (Google Colab)

| Library | Use |
|---|---|
| `OpenCV` | Image loading, color conversion, edge detection |
| `scikit-learn` | K-means clustering for dominant color extraction |
| `scikit-image` | Local Binary Patterns |
| `NumPy` | Numerical computation |
| `Matplotlib` | Visualization |
| `seaborn` | Statistical plotting |

**R**

| Library | Use |
|---|---|
| `syuzhet` | NRC sentiment and emotion analysis |
| `tidytext` | Text tokenization and preprocessing |
| `pls` | Partial Least Squares Regression |
| `pheatmap` | Hierarchical clustering heatmaps |
| `factoextra` | PCA visualization |
| `corrplot` | Correlation matrix visualization |
| `ggplot2` | Statistical visualization |
| `wordcloud` | Word cloud generation |

---

## Status

This is an **ongoing research project**. Results are preliminary.

---

## Ethics and Privacy

The self-report data collected in this project include sensitive personal information about emotional, psychological, and physical states. Data are not publicly shared in this repository. Only the codes used for the analysis are included.

This project was conducted as personal artistic research. All data were self-reported by the artist.

---

## License

This project is licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/legalcode.txt). You are free to share and adapt the material with appropriate attribution.

---

## Contact

For questions about this project, please open an issue in this repository.

---

*Both in One — Julieta Arco*
