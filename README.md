[Coursera Scraper](https://apify.com/antonionduarte/coursera-scraper?fpr=data)

Coursera Scraper is an Apify actor designed to extract comprehensive course data from the Coursera platform. Whether you’re conducting market analysis, tracking educational trends, or performing competitor research, this tool streamlines the data extraction process and allows you to harness Coursera’s vast catalog of courses. The scraper fetches course information, including course titles, ratings, partners, skill tags, and more, making it ideal for anyone analyzing the world of online education.

## Why scrape Coursera?

Coursera is a premier online learning platform that offers thousands of courses from leading universities and institutions. By scraping Coursera data, you can:

- Monitor course ratings and popularity to understand what learners value.
- Identify top universities and partners offering courses in your niche.
- Track industry trends in technology, business, data science, and more.
- Compare similar courses across different providers to gain insights into course structure, pricing, and market positioning.

## Features

- Scrapes detailed course information, including name, URL, ratings, difficulty level, partner institutions, and associated skills.
- Allows configurable input parameters to refine the search query and number of pages to scrape.
- Stores all extracted data into a single dataset for simplified analysis.

## How much will it cost to scrape Coursera?

The access to the scraper itself costs $20/month.

Apify provides $5 free usage credits every month on the Free plan. This means you can scrape a limited number of restaurants or categories for free each month. For higher-volume scraping, consider upgrading to an Apify subscription. The Starter plan at $49/month allows you to scrape more data, while the Scale plan offers higher quotas for professional use cases.

## Usage

### Input Parameters

The actor accepts the following input parameters:

- `query` (Required): A search term (e.g., "artificial intelligence") to find relevant courses.
- `pages` (Optional): The number of pages of search results to scrape. Defaults to 3 if not provided.

**Notes:**

- This scraper utilizes **Residential Proxies** for all requests to ensure reliable data extraction.
- The runtime may increase with larger page counts, as more requests are performed. Consider adjusting your parameters for optimal performance.

### Example Input

```
{
    "query": "artificial intelligence",
    "pages": 5
}
```

## Running the Actor

You can run the actor directly from the Apify platform or via API. Ensure you provide the necessary input parameters as specified above.

## Output

All scraped data is stored in a single dataset, accessible in the Storage section under Datasets. This dataset provides structured JSON records for each course, enabling easy integration into your analytics workflows.

### Data Fields

**Courses Dataset** (default dataset):

- `id`: Unique course identifier.
- `name`: Course title.
- `url`: Direct link to the course page.
- `avgProductRating`: Average user rating of the course.
- `numProductRatings`: Number of ratings.
- `isCourseFree`: Indicates if the course is free.
- `isCreditEligible`: Indicates if the course offers academic credit.
- `isPartOfCourseraPlus`: Indicates if the course is included in Coursera Plus.
- `productDifficultyLevel`: Difficulty level (e.g., BEGINNER, INTERMEDIATE).
- `productDuration`: Estimated duration (e.g., ONE_TO_FOUR_WEEKS).
- `productType`: Type of product (e.g., COURSE, SPECIALIZATION).
- `skills`: List of skills associated with the course.
- `partners`: List of partner institutions offering the course.
- `imageUrl`: URL of the course image.

**NOTE:** Apify datasets support multiple export formats including JSON, CSV, and XLSX, so you can easily integrate scraped Glovo data into your workflows.

## Is it legal to scrape Coursera?

Always ensure that your data collection activities adhere to local and international laws and respect Coursera’s terms and policies. Scrape only publicly available information, avoid personal data, and maintain a legitimate purpose for data collection. If in doubt, consult legal counsel.