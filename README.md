# Pinterest_YouTube_Scraping

## 📌 Overview
This repository contains two Jupyter notebooks for collecting and analyzing social media data:
- One for scraping **images from Pinterest**
- Another for analyzing **YouTube bumper ads** based on clarity, motion, and aesthetic scores.

---

## 📒 Notebooks

### 1. `Pinterest_Image_Scraping.ipynb`
- Scrapes images from Pinterest using **Selenium** for web automation.
- Saves the collected image data to a specified directory or file format.

### 2. `YouTube_Bumper_Ads_Analysis_Small.ipynb`
- Analyzes **five YouTube bumper ads** (4–12 seconds long).
- Calculates **clarity, motion, and aesthetic scores** using computer vision techniques.
- Outputs results as `ads_yt.json`.

---

## ⚙️ Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/Pinterest_YouTube_Scraping.git
cd Pinterest_YouTube_Scraping
````

### 2. Install Dependencies

Install the required Python libraries:

```bash
pip install -r requirements.txt
```

**Key dependencies include:**

* `yt_dlp==2024.12.13`
* `google-api-python-client==2.155.0`
* `isodate==0.7.2`
* `pandas`, `matplotlib`, `seaborn`, `wordcloud`
* `selenium`
* `pydotmap`, `python-dotenv`
* `opencv-python` (for YouTube video processing)

---

## 🔑 YouTube API Configuration

1. Obtain a YouTube Data API key from the **Google Cloud Console**.
2. Create a `.env` file in the project root:

```
YOUTUBE_API_KEY=your_youtube_api_key_here
```

> The notebook uses `python-dotenv` to load this key securely.

---

## 📌 Pinterest Scraping Configuration

* Install **ChromeDriver** compatible with your browser for Selenium.
* If login is required, configure credentials in `.env`:

```
PINTEREST_USERNAME=your_username_here
PINTEREST_PASSWORD=your_password_here
```

> Alternatively, modify the notebook to prompt for login interactively.

---

## ☁️ AWS S3 Integration (Optional)

The YouTube notebook includes optional S3 upload support.

### Steps:

1. Install and configure AWS CLI:

```bash
pip install awscli
aws configure
```

2. Create the bucket and upload:

```bash
aws s3 mb s3://marketing-dataset
aws s3 cp youtube_ads.json s3://marketing-dataset/
```

> Ensure your AWS credentials have proper permissions.

---

## 🚀 Usage Notes

### 📌 Pinterest\_Image\_Scraping.ipynb

* Outputs scraped images or metadata to a user-specified folder.
* Requires **ChromeDriver** for Selenium.
* Make sure to comply with **Pinterest’s terms of service and robots.txt**.

### 📌 YouTube\_Bumper\_Ads\_Analysis\_Small.ipynb

* Processes five bumper ads.
* Generates `ads_yt.json` with:

  * Video ID, title, duration
  * Clarity, motion, aesthetic, and suitability scores
* Requires a valid **YouTube Data API key**.

---

## 📊 YouTube API Quota Tips

* Default quota: **10,000 units/day**
* Larger datasets may exceed this limit.

**To avoid quota exhaustion:**

* Run the notebook across multiple days.
* Request quota increase from Google Cloud Console.
* Cache results to reduce redundant API calls.

---

## 📁 Outputs

| Notebook                                  | Output Format       | Description                           |
| ----------------------------------------- | ------------------- | ------------------------------------- |
| `YouTube_Bumper_Ads_Analysis_Small.ipynb` | `ads_yt.json`       | Metadata of analyzed bumper ads       |
| `Pinterest_Image_Scraping.ipynb`          | Images / CSV / JSON | Format depends on your implementation |

