[Coursera Scraper](https://apify.com/fatihtahta/coursera-scraper?fpr=data)

# Coursera Scraper | All In One

**Slug:** `fatihtahta/coursera-scraper`

## Overview

Coursera Scraper collects structured course details and optional learner reviews from [Coursera](https://www.coursera.org), including titles, partners, ratings, skills, durations, and availability signals. Coursera is a leading destination for online learning, and this actor turns its catalog into consistent, structured data for analysis and automation. Automated runs save time, keep filtering rules consistent, and reduce manual effort to keep catalogs and dashboards current. The actor keeps inputs flexible so you can target searches, categories, or specific courses without extra setup.

## Why Use This Actor

- **Market researchers and analysts:** Track catalog coverage, ratings, and partner presence to benchmark trends over time.
- **Product and content teams:** Validate demand by topic, level, and language to prioritize new programs or translations.
- **Developers and data engineering pipelines:** Feed normalized course data into catalogs, recommendation engines, or enrichment workflows without manual cleanup.
- **Lead generation and enrichment:** Identify partners, brands, and programs aligned to your audience with ratings and skills included for targeting.
- **Monitoring and competitive tracking:** Watch new or updated courses, durations, and ratings within selected topics or difficulty bands.

## Input Parameters

Provide any combination of URLs, queries, and filters. Leave optional fields empty to collect broader results.

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| `startUrls` | `string[]` | Coursera search pages, category pages, or specific course URLs to collect directly. | – |
| `queries` | `string[]` | Search phrases that will be converted into Coursera search pages. | – |
| `difficultyLevel` | `string[]` | Course difficulty levels to include. Allowed values: `Beginner`, `Intermediate`, `Advanced`, `Mixed`. | – |
| `duration` | `string[]` | Expected study lengths to include. Allowed values: `Less Than 2 Hours`, `1–4 Weeks`, `1–3 Months`, `3–6 Months`, `1–4 Years`. | – |
| `topic` | `string[]` | Subject areas to include. Allowed values: `Business`, `Computer Science`, `Information Technology`, `Data Science`, `Health`, `Physical Science and Engineering`, `Social Sciences`, `Arts and Humanities`, `Personal Development`, `Language Learning`, `Math and Logic`. | – |
| `language` | `string[]` | Course content languages to include. Allowed values: Afrikaans, Albanian, Amharic, Arabic, Azerbaijani, Bengali, Bulgarian, Burmese, Catalan, Chinese, Croatian, Czech, Danish, Dutch, English, Estonian, Finnish, French, Georgian, German, Greek, Hebrew, Hindi, Hungarian, Indonesian, Italian, Japanese, Javanese, Kannada, Kazakh, Khmer, Kinyarwanda, Korean, Latvian, Lithuanian, Macedonian, Marathi, Mongolian, Nepali, Oriya, Persian, Polish, Portuguese, Pushto, Romanian, Russian, Serbian, Slovak, Slovenian, Somali, Spanish, Swahili, Swedish, Tagalog, Tamil, Telugu, Thai, Turkish, Ukrainian, Urdu, Uzbek, Vietnamese. | – |
| `subtitles` | `string[]` | Subtitle languages to include. Allowed values match the `language` options above. | – |
| `getComments` | `boolean` | When true, also capture course reviews. | `false` |
| `commentLimit` | `integer` | Maximum number of reviews to collect per course. | `50000` |
| `limit` | `integer` | Maximum number of listings to collect overall. | `50000` |
| `proxyConfiguration` | `object` | Connection settings. Uses Apify residential proxy by default (group `RESIDENTIAL`). | `{"useApifyProxy": true, "apifyProxyGroups": ["RESIDENTIAL"]}` |

## Example Input

```
{
  "queries": ["data analytics", "machine learning"],
  "startUrls": ["https://www.coursera.org/search?query=cloud"],
  "difficultyLevel": ["Beginner", "Intermediate"],
  "duration": ["1–3 Months", "3–6 Months"],
  "getComments": true,
  "limit": 500
}
```

## Output

### 6.1 Output destination

The actor writes results to an Apify dataset as JSON records.

### 6.2 Record envelope (all items)

- **type** *(string, required)*
- **id** *(number, required)*
- **url** *(string, required)*

**Recommended idempotency key:** `type + ":" + id`.
Use this key for deduplication and upserts when combining multiple runs.

### 6.3 Examples

**Example: review (`type = "review"`)**

```
{
  "type": "review",
  "id": 902001,
  "url": "https://www.coursera.org/learn/excel-basics-data-analysis-ibm",
  "datePublished": "2020-11-11",
  "reviewBody": "There are problems with the peer-reviewed project grading rubrics.  Other learners who, of course, are not subject experts do not always grade properly - sometimes completely wrong.  Although you can send a message to your peer reviewer, I have never received a follow-up explanation or response.  There is no practical recourse to appeal the unfairly peer graded assignment, other than to re-do and re-submit the assignment - which is time consuming and wasteful!  I think there needs to be a robust process in place to have subject experts, such as the course instructors, to review disputed peer reviewed and graded assignments.  Not once have I received a response from the Help Desk when I have reported a problem - this, too, is a big disappointment!",
  "author": "Steve Carpenter",
  "ratingValue": 5,
  "courseUrl": "https://www.coursera.org/learn/excel-basics-data-analysis-ibm",
  "courseId": "course~3bkTOtzVEequVRKuqBsDQw",
  "courseSlug": "excel-basics-data-analysis-ibm",
  "courseTitle": "Excel Basics for Data Analysis",
  "recordType": "review"
}
```

**Example: course (`type = "course"`)**

```
{
  "type": "course",
  "id": 120345,
  "url": "https://www.coursera.org/professional-certificates/ibm-data-analyst-r-excel",
  "title": "IBM Data Analytics with Excel and R",
  "brand": "IBM",
  "description": "Prepare for a career in data analytics\nOffered by IBM",
  "avgProductRating": 4.729850746268659,
  "numProductRatings": 30820,
  "skills": [
    "Data Storytelling",
    "Data Presentation",
    "Data Visualization",
    "Interactive Data Visualization",
    "Data Visualization Software",
    "Database Design",
    "Shiny (R Package)",
    "Dashboard",
    "Data Wrangling",
    "Exploratory Data Analysis",
    "Relational Databases",
    "Data Analysis",
    "Statistical Visualization",
    "Big Data",
    "Microsoft Excel",
    "IBM Cognos Analytics",
    "Analytical Skills",
    "Excel Formulas",
    "Data Manipulation",
    "Web Scraping"
  ],
  "productDifficultyLevel": "BEGINNER",
  "productDuration": "THREE_TO_SIX_MONTHS",
  "productType": "PROFESSIONAL_CERTIFICATE",
  "imageUrl": "https://d15cw65ipctsrr.cloudfront.net/a0/6bda7e8f7245b3ada2915a88e5ad65/DataAnalyticswith-ExcelandR-PC.jpg",
  "isCourseFree": false,
  "isCreditEligible": true,
  "isNewContent": false,
  "isPartOfCourseraPlus": true,
  "partnerLogos": [
    "http://coursera-university-assets.s3.amazonaws.com/bb/f5ced2bdd4437aa79f00eb1bf7fbf0/IBM-Logo-Blk---Square.png"
  ],
  "partners": [
    "IBM"
  ],
  "tagline": "Prepare for a career in data analytics\nOffered by IBM",
  "fullyTranslatedLanguages": [
    "English"
  ],
  "subtitlesOnlyLanguages": [
    "Arabic",
    "Azerbaijani",
    "Bengali",
    "Chinese",
    "Dutch",
    "French",
    "German",
    "Greek",
    "Hindi",
    "Hungarian",
    "Indonesian",
    "Italian",
    "Japanese",
    "Kazakh",
    "Korean",
    "Oriya",
    "Polish",
    "Portuguese",
    "Pushto",
    "Russian",
    "Spanish",
    "Swedish",
    "Thai",
    "Turkish",
    "Ukrainian",
    "Urdu",
    "Uzbek",
    "Vietnamese"
  ],
  "productCard": {
    "id": "QQGg65luEeugtw5wj3v7iQ",
    "canonicalType": "SPECIALIZATION",
    "marketingProductType": "PROFESSIONAL_CERTIFICATE",
    "badges": [
      "Free Trial"
    ],
    "productTypeAttributes": {
      "isPathwayContent": true,
      "__typename": "ProductCard_Specialization"
    },
    "__typename": "ProductCard_ProductCard"
  },
  "cobrandingEnabled": false
}
```

## Field reference

### Review fields (`type = "review"`)

- **type** *(string, required)*: Record category identifier (`review`).
- **id** *(number, required)*: Stable numeric identifier for the review.
- **url** *(string, required)*: Canonical link associated with the review (course page).
- **datePublished** *(string, optional)*: Review date (ISO `YYYY-MM-DD`).
- **reviewBody** *(string, optional)*: Free-text review content.
- **author** *(string, optional)*: Reviewer display name when available.
- **ratingValue** *(number, optional)*: Star rating value.
- **courseUrl** *(string, optional)*: Course link the review references.
- **courseId** *(string, optional)*: Coursera course identifier.
- **courseSlug** *(string, optional)*: Course slug.
- **courseTitle** *(string, optional)*: Course title at the time of collection.
- **recordType** *(string, optional)*: Source label for the review record.

### Course fields (`type = "course"`)

- **type** *(string, required)*: Record category identifier (`course`).
- **id** *(number, required)*: Stable numeric identifier for the course.
- **url** *(string, required)*: Canonical course URL.
- **title** *(string, required)*: Course or program title.
- **brand** *(string, optional)*: Publishing brand or institution.
- **description** *(string, optional)*: Summary text shown with the course.
- **avgProductRating** *(number, optional)*: Average rating value.
- **numProductRatings** *(number, optional)*: Count of ratings.
- **skills** *(array[string], optional)*: Key skills highlighted.
- **productDifficultyLevel** *(string, optional)*: Difficulty level (e.g., `BEGINNER`).
- **productDuration** *(string, optional)*: Duration bucket (e.g., `THREE_TO_SIX_MONTHS`).
- **productType** *(string, optional)*: Product category (e.g., `PROFESSIONAL_CERTIFICATE`).
- **imageUrl** *(string, optional)*: Primary image URL.
- **isCourseFree** *(boolean, optional)*: Whether the course is free.
- **isCreditEligible** *(boolean, optional)*: Credit eligibility flag.
- **isNewContent** *(boolean, optional)*: Whether marked as new content.
- **isPartOfCourseraPlus** *(boolean, optional)*: Coursera Plus availability.
- **partnerLogos** *(array[string], optional)*: Logo URLs for partners.
- **partners** *(array[string], optional)*: Partner names.
- **tagline** *(string, optional)*: Promotional tagline.
- **fullyTranslatedLanguages** *(array[string], optional)*: Languages with full translations.
- **subtitlesOnlyLanguages** *(array[string], optional)*: Subtitle-only languages.
- **productCard.id** *(string, optional)*: Product card identifier.
- **productCard.canonicalType** *(string, optional)*: Canonical product type.
- **productCard.marketingProductType** *(string, optional)*: Marketing product category.
- **productCard.badges** *(array[string], optional)*: Badge labels applied to the product.
- **productCard.productTypeAttributes.isPathwayContent** *(boolean, optional)*: Pathway content flag.
- **productCard.__typename** *(string, optional)*: Internal typename label.
- **cobrandingEnabled** *(boolean, optional)*: Cobranding availability flag.

## Data guarantees & handling

- **Best-effort extraction:** Available fields can vary by region, session state, and on-site experiments.
- **Optional fields:** Null-check and guard for missing fields in downstream code.
- **Deduplication:** Use `type + ":" + id` to merge or upsert records across runs.

## Notes & Limitations

- Respect Coursera terms of service and applicable laws when using the data.
- Avoid excessive request frequency to keep runs reliable and courteous.
- Pricing, availability, and ratings can change by region, time, or session; treat them as snapshots.
- Validate collected data for your compliance, storage, and retention requirements.

## Support

For help, open an issue on the actor page with the input used (redacted as needed), the run ID, expected vs. actual behavior, and a small sample of the output if available. This information speeds up troubleshooting and ensures accurate guidance.