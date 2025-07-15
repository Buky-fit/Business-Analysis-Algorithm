# Social Media Engagement Analysis

This project analyzes social media engagement data from a CSV file to uncover insights into user behavior and content performance across different platforms. The analysis is performed using Python with libraries such as Pandas, Matplotlib, and Seaborn in a Jupyter Notebook (`Analysis.ipynb`).

## Table of Contents

- [Social Media Engagement Analysis](#social-media-engagement-analysis)
  - [Table of Contents](#table-of-contents)
  - [Project Description](#project-description)
  - [Installation](#installation)
  - [Database Connection](#database-connection)
  - [Usage](#usage)
  - [Analysis and Visualizations](#analysis-and-visualizations)
    - [Platform Analysis](#platform-analysis)
    - [Temporal Analysis](#temporal-analysis)
    - [Content-Type Analysis](#content-type-analysis)
  - [Key Insights](#key-insights)
  - [Files in this Repository](#files-in-this-repository)
  - [Contributing](#contributing)
  - [License](#license)

## Project Description

The goal of this analysis is to understand the factors that drive social media engagement. By examining data on posts, likes, comments, and shares, this project aims to answer key questions such as:

- Which social media platform is the most effective for engagement?
- What are the best times and days to post content?
- Which types of content perform best?

The findings from this analysis can help businesses and content creators optimize their social media strategies for maximum impact.

## Installation

To run this analysis, you need to have Python and Jupyter Notebook installed. You can install the necessary libraries using pip:

```bash
pip install pandas matplotlib seaborn jupyter
```

## Database Connection

The analysis notebook (`Analysis.ipynb`) includes code to connect to a MySQL database using SQLAlchemy. Database credentials and connection details are managed securely using environment variables stored in a `.env` file. This approach keeps sensitive information out of your code and version control.

**To use the database connection:**

1. Create a `.env` file in the project root with the following content (update values as needed):
   ```
   DB_USER=root
   DB_PASSWORD=your_password
   DB_HOST=localhost
   DB_NAME=social_media_analysis
   ```
2. The notebook will load these variables and use them to connect to your MySQL server and create the database if it does not exist.
3. The connection is established using SQLAlchemy and the `python-dotenv` package. Make sure to install `python-dotenv` and `sqlalchemy`:
   ```bash
   pip install python-dotenv sqlalchemy pymysql
   ```
4. Example connection code in the notebook:
   ```python
   from sqlalchemy import create_engine
   from dotenv import load_dotenv
   import os, urllib

   load_dotenv()
   db_user = os.getenv('DB_USER')
   db_password = urllib.parse.quote_plus(os.getenv('DB_PASSWORD'))
   db_host = os.getenv('DB_HOST')
   db_name = os.getenv('DB_NAME')
   engine = create_engine(f"mysql+pymysql://{db_user}:{db_password}@{db_host}/{db_name}")
   ```
5. Do not commit your `.env` file to public repositories.

## Usage

1. Clone this repository to your local machine.
2. Place the `social_media_engagement.csv` file in the `social_data` directory.
3. Open and run the `Analysis.ipynb` notebook in Jupyter Notebook.

## Analysis and Visualizations

The notebook is structured into several sections, each focusing on a different aspect of the data.

### Platform Analysis

This section compares the engagement metrics across different social media platforms (Facebook, Instagram, Twitter).

- **Visualizations:**
  - Bar plot of average engagement per post per platform.

### Temporal Analysis

This section explores how engagement varies over time.

- **Questions Explored:**
  - What are the peak hours for engagement?
  - How does engagement differ between weekdays and weekends?
  - Are there monthly or seasonal trends?
- **Visualizations:**
  - Line plot of average engagement per post by time of day.
  - Bar plot of total engagement by day of the week.
  - Bar plot of total engagement by month.
  - Pie chart of the percentage of total engagement by time of day.

### Content-Type Analysis

This section analyzes the performance of different types of content (e.g., image, video, carousel, poll, text).

- **Visualizations:**
  - Bar plot of average engagement per post by content type.
  - Stacked bar chart of total posts by day of the week and post type.

## Key Insights

- **Video content** tends to generate the highest average engagement.
- Engagement is generally **higher on weekends** compared to weekdays.
- **Peak engagement times** vary by platform, but there are identifiable peak hours across all platforms.
- The distribution of post types varies across different days of the week, indicating potential content scheduling strategies.

## Files in this Repository

- `Analysis.ipynb`: The Jupyter Notebook containing the full analysis.
- `social_data/social_media_engagement.csv`: The raw data used for the analysis.
- `charts/`: A directory containing saved visualizations from the notebook.
- `README.md`: This file.

## Contributing

Contributions are welcome! If you have suggestions for improving this analysis, please feel free to create an issue or submit a pull request.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.
