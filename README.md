# Auto-Update Data Visualization

Automated bank stock visualizations using Python and AWS EC2/S3.

This project fetches historical stock data for 5 major US banks, generates visualizations, and automatically uploads them to AWS S3 on a scheduled basis.

## Banks Tracked

- JPMorgan Chase (JPM)
- Bank of America (BAC)
- Citigroup (C)
- Wells Fargo (WFC)
- Goldman Sachs (GS)

## Visualizations

The script generates a 2x2 subplot containing:

1. **Boxplot** - Distribution of stock prices across all banks
2. **Scatterplot** - Wells Fargo stock prices over time
3. **Scatterplot** - Bank of America stock prices over time
4. **Histogram** - Frequency distribution of stock prices for all banks

## Tech Stack

- **Python** - Core language
  - `pandas` - Data manipulation
  - `matplotlib` - Visualization
  - `yfinance` - Stock data
  - `boto3` - AWS SDK
- **AWS EC2** - Hosts and runs the script
- **AWS S3** - Stores the generated visualizations
- **Cron** - Schedules automated execution

## Setup

### Prerequisites

- Python 3.11+
- AWS account with EC2 and S3 configured
- AWS credentials configured locally or on EC2

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/auto-update-data-visualization.git
   cd auto-update-data-visualization
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Update the S3 bucket name in `bank_stock_data.py`:
   ```python
   s3.meta.client.upload_file('bank_data.png', 'your-bucket-name', 'bank_data.png')
   ```

### Running Locally

```bash
python3.11 bank_stock_data.py
```

### Scheduling with Cron (on EC2)

Add a cron job to run the script automatically:

```bash
crontab -e
```

Example (runs daily at midnight):
```
0 0 * * * /usr/bin/python3 /path/to/bank_stock_data.py
```

## Future Plans

- Build a simple website to display the graphs
- Show historical changes over time
