# Amelia-Hari-Fauziah_Hands-on-1-MLOps_Data-Scraping
# Course Recommendation System  
**Project Overview**  
This project aims to develop a course and certification recommendation system using machine learning based on text similarity. The dataset was collected through web scraping from a public online course website and preprocessed to be suitable for training a simple recommendation model using TF-IDF and cosine similarity.  

> Scraping Process

- **Tools Used:**  
  - `requests` (HTTP request to page)  
  - `BeautifulSoup` (HTML parsing)  

- **Scraping Flow:**  
  1. Request HTML content from target URL  
  2. Parse HTML using BeautifulSoup  
  3. Select course elements (`<article>`, `<h2>`, `<p>`, etc.)  
  4. Extract and save title, description, and URL  

**1. Data Scraping**
- - **Source:** Publicly listed content from the [FreeCodeCamp News](https://www.freecodecamp.org/news/) website, specifically pages under topical tags (e.g., Data Science).

- BeautifulSoup was used for parsing HTML and extracting course information.

- The scraping targeted key elements such as:

  - Course title

  - Course description

  - Course link

- The result was stored in a .csv file named preprocessed_courses.csv.  

**Note**: The scraping process is limited to the static content available on the initial HTML page. Websites that use lazy loading or dynamically load data via JavaScript (e.g., loading more courses as the user scrolls) may not be fully captured using BeautifulSoup.  

**2. Preprocessing**

- Basic text preprocessing steps were applied to the course descriptions:

- Lowercasing

- Removing non-alphabetical characters

- Stopword removal using scikit-learn's built-in stopword list

- Tokenization (optional)

- Optionally, lemmatization or stemming can be added using nltk or spaCy

  **Example:**

> 🔸 Before:  
> `"Learn the basics of data science, including Python, statistics, and more!"`

> 🔸 After:  
> `"learn basics data science including python statistics"`

- A new column clean_description was created and saved into the dataset.  

**3. Vectorization and Similarity**
   
- TF-IDF (TfidfVectorizer) was used to convert course descriptions into numerical feature vectors.

> **Reflection: Challenges & Limitations**

- **Challenge:** The website uses **lazy loading**, meaning only a portion of courses appear in the raw HTML.
- **Impact:** Only ~25 courses could be extracted using BeautifulSoup.
- **Solution Options:**
  - Use **Selenium** to automate scrolling and trigger JavaScript-rendered content.
  - Explore whether the site offers a **REST API** to access full data programmatically.

- Cosine similarity was calculated to measure the closeness between course contents.

- Based on these similarities, a function was implemented to recommend the top N most similar courses.
