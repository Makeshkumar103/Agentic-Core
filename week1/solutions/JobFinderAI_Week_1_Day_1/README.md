Job Finder AI tool

# JobFinderAI

**AI-Powered Job Matching**: Extracts skills and experience from resumes using OpenAI, then queries job board APIs to find relevant positions in Bengaluru for senior backend developers.

## 🎯 Features

- **Resume Parsing**: OpenAI extracts skills, experience, location preferences from PDF/text resumes
- **Job Board Integration**: Fetches real-time listings from Workday, Greenhouse, Amazon Jobs, etc.
- **Smart Matching**: Filters senior Java/backend roles in Bengaluru, Karnataka
- **CSV Export**: Clean Excel-ready tables with clickable apply links
- **Jupyter Ready**: Interactive tables with hover effects and sorting

## 📋 Workflow

Resume (PDF/Text) → OpenAI Extraction → Job Board APIs → Clean CSV/Interactive Table

1. **Parse Resume**: Extract skills (Java, Spring Boot, AWS), years (6+), location (Bengaluru)
2. **API Calls**: Query job boards for matching senior backend roles
3. **Data Processing**: Handle JSON arrays → Pandas DataFrame → Clean CSV
4. **Output**: `job_listings_bengaluru.csv` with 9+ senior positions

## 🚀 Quick Start

install uv
install all required packages from requirements.txt
Set uv interpreter in Pycharm settings -> Project -> Python Interpreter, override the generated .venv
Run all cells in Jupyter Notebook `job_finder_ai.ipynb`

## 📊 Sample Output


| Title                                                | Organization  | Location                    | URL                                                                                                                     |
| ---------------------------------------------------- | ------------- | --------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Senior Software Developer in Test                    | Q2            | Bengaluru, Karnataka, India | [🔗 Apply](https://q2ebanking.wd5.myworkdayjobs.com/Q2/job/Bangalore-India/Senior-Software-Developer-in-Test_REQ-11519) |
| Software Development Engineer II (Backend)           | AppsForBharat | Bengaluru, Karnataka, India | [🔗 Apply](https://careers.kula.ai/appsforbharat/jobs/19566)                                                            |
| Software Development Engineer II, Amazon MGM Studios | Amazon        | Bengaluru, Karnataka, India | [🔗 Apply](https://www.amazon.jobs/en/jobs/3133217)                                                                     |


**Generated: Nov 29, 2025** - 9 Senior Backend/Java roles found

## 🛠️ Tech Stack

- **AI**: OpenAI GPT for resume parsing
- **Data**: Pandas, JSON processing
- **APIs**: Rapid API for job boards: [https://rapidapi.com/fantastic-jobs-fantastic-jobs-default/api/active-jobs-db/playground/endpoint_cb22369f-a718-452c-b4f2-32591bf058f8](https://rapidapi.com/fantastic-jobs-fantastic-jobs-default/api/active-jobs-db/playground/endpoint_cb22369f-a718-452c-b4f2-32591bf058f8)
- **Export**: CSV (Excel-compatible)
- **IDE**: PyCharm Professional, Jupyter Notebooks

## 📁 File Structure

JobFinderAI/
├── requirements.txt # openai, pandas, requests
├── resume_parser.py # OpenAI resume extraction
├── job_scraper.py # Job board API calls
├── data_processor.py # JSON → Clean CSV (your code)
├── job_listings_bengaluru.csv # ✅ OUTPUT
├── README.md # This file
└── .env # OPENAI_API_KEY

## 🔮 Next Steps

- [ ] Add support for salary estimates
- [ ] Email notifications for new matches
- [ ] Visa jobs (user's international goal)
- [ ] AWS Lambda deployment for daily runs
- [ ] Kafka integration for job stream processing

## 📄 License

MIT License - Feel free to use for job hunting! 🎯