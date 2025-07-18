# Automatic Company Name Standardization Tool

A Streamlit-based web application for standardizing company names using fuzzy matching and AI (Google Gemini).

## Key Features

- **Fuzzy Matching**: Matches company names against a reference database.
- **AI Standardization**: Uses the Google Gemini API to standardize names.
- **Double Check**: Second fuzzy matching for AI results.
- **Batch Processing**: Processes multiple files simultaneously.
- **Location-aware**: Special handling based on location (e.g., Shopee Singapore vs. Indonesia).

## Installation

### 1. Clone or Download Files
Ensure you have the following files:
- `app.py` (main application file)
- `requirements.txt` (dependencies)

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Get Google Gemini API Key
1. Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Create a new API key
3. Store your API key securely
   
### 4. Run the Application
```bash
streamlit run app.py
```

## How to Use

### 1. Upload Files
- **Main Data File**: An Excel file containing company names to be standardized.
- **Reference Files**: Excel files containing pre-standardized company names (optional).

### 2. Configuration
- Enter **Gemini API Key** in the sidebar
- Select the column containing **company names**
- Select the **address** column (optional, helps with location-based matching)
- Set the **rate limit** for API calls

### 3. Process
1. Click "Start Processing"
2. The application will perform 3 stages:
   - **Fuzzy Matching 1**: Matches against the reference database.
   - **AI Standardization**: Uses Gemini for unmatched names.
   - **Fuzzy Matching 2**: Double-checks AI results.

### 4. Download
- Download the results in Excel format.
- View statistics and names that could not be standardized.
  
## Format File Input

### Main Data File
Must contain columns for:
- Company name (can be any column name).
- Address (optional).

### Reference Files
Must contain columns for:
- `company_name_standardized`: The standardized company name.
- `company_name`: The original company name (optional).

## Example Standardization Results

| Input | Output |
|-------|--------|
| BCA | PT Bank Central Asia Tbk |
| Mandiri | PT Bank Mandiri (Persero) Tbk |
| Shopee Indonesia | PT Shopee Internasional Indonesia |
| Shopee (Singapore) | Shopee Pte. Ltd. |

## Troubleshooting

### Error: "API connection failed"
- Ensure the API key is valid
- Check internet connection
- Ensure API quota has not been exceeded

### Error: "File loading failed"
- Ensure the file is in Excel format (.xlsx or .xls)
- Check if the file is corrupted
- Ensure the file has the necessary columns

### Performance Issues
- Reduce the rate limit if there are too many errors
- Process files in smaller batches
- Ensure a stable internet connection

## Rate Limiting

- Default: 10 requests per minute
- Can be adjusted in the sidebar
- Setting it too high can cause quota errors
- Setting it too low will slow down the process

## Catatan Penting

1. **API Cost**: Each request to the Gemini API is free for up to 1000 requests
2. **Data Privacy**: Data is processed locally in the browser and is not stored on a server
3. **File Size**: For large files, processing may take a long time
4. **Backup**: Always back up your original data before processing
   
## Support

If you encounter issues:
1. Check the browser console for error messages
2. Ensure all dependencies are installed
3. Verify the input file format
4. Check your API key and quota

---

**Based on the idea and innovation by Kerlyn Deslia Andeskar**
