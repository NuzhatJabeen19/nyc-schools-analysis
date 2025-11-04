# NYC Schools Analysis

A comprehensive data analysis project examining NYC public school safety, demographics, and academic performance using SQL, Python, and exploratory data analysis techniques.

## 📋 Project Overview

This project analyzes multiple datasets from New York City public schools to uncover insights about school safety incidents, student demographics, SAT performance, and geographic distribution patterns. The analysis combines exploratory data analysis, SQL database operations, and statistical reporting to provide actionable intelligence about the NYC school system.

## 🗂️ Project Structure
```
NYC-SCHOOLS-ANALYSIS/
├── 0_data/                          # Raw and reference data
├── 1_incident_analysis/             # School safety incident analysis
├── 2_schools_directory_exploration/ # School distribution and enrollment patterns
├── 3_database_queries/              # SQL-based data exploration
└── 4_database_population/           # SAT data cleaning and database integration
```

## 📊 Datasets

### School Safety Report (`school-safety-report.csv`)
Detailed safety incident data across NYC schools including:
- Incident categories: Major, Other, Non-Criminal, Property, Violent
- Geographic data (Borough, Latitude, Longitude)
- School enrollment (Register)
- Multi-year trends by School Year

### High School Directory (`high-school-directory.csv`)
Comprehensive directory of NYC high schools with:
- School identifiers (DBN, school name)
- Location and borough information
- Grade span coverage
- Enrollment figures

### School Demographics
Demographic data including:
- English Language Learner (ELL) percentages
- Special Education (SPED) percentages
- Multiple years of data per school

### SAT Results (`sat-results.csv`)
Academic performance metrics including:
- SAT scores (Reading, Math, Writing)
- Test-taker counts
- Percentage of students tested
- Academic tier ratings

## 🔍 Key Analyses

### 1. School Safety Incident Analysis
- **Total Records**: 6,310 incidents across 1,890 unique schools
- **Most Common Incident**: Non-criminal incidents (11,772 total)
- **Geographic Focus**: 28.24% of incidents occur in The Bronx
- **Critical Finding**: Identified extreme anomaly with per-student incident rates suggesting data quality issues

📊 [View Full Analysis](https://docs.google.com/spreadsheets/d/1_Vfm-bJgPJsfThlgo0MAIRe7PJIBy3OKE1J5yobvJlQ/edit?usp=sharing)

### 2. School Distribution & Enrollment Patterns
**School Counts by Borough:**
- Brooklyn: 121 schools
- Bronx: 118 schools
- Manhattan: 106 schools
- Queens: 80 schools
- Staten Island: 10 schools

**Key Insights:**
- Brooklyn serves the most students (~83,197 total)
- Staten Island has the highest average enrollment per school (~1,848 students)
- Bronx shows smallest average school size (~490 students), indicating community-focused models
- Nearly 4x variance in school size between boroughs suggests different operational models and resource needs

### 3. SQL Database Analysis
Executed comprehensive SQL queries to explore:
- School distribution patterns across boroughs
- Demographic metrics (ELL and SPED percentages)
- Window functions for ranking schools by demographic indicators
- Multi-year data handling and deduplication strategies

**Technical Stack:** PostgreSQL via psycopg2, pandas integration, secure credential management via python-dotenv

### 4. SAT Data Integration
Cleaned and standardized SAT performance data for database integration:
- Handled suppressed values and missing data
- Validated score ranges (200-800)
- Removed duplicates and standardized column names
- Created foreign key relationships with school directory

## 🛠️ Technical Implementation

### Technologies Used
- **Python**: pandas, NumPy, Matplotlib, psycopg2
- **Database**: PostgreSQL with schema `nyc_schools`
- **Environment**: Jupyter Notebooks, python-dotenv for secure credential management
- **Version Control**: Git/GitHub

### Database Schema
```sql
-- Main tables
nyc_schools.high_school_directory
nyc_schools.school_demographics
nuzhat_amna_sat_scores (with foreign key to high_school_directory)
```

## 📈 Key Findings

1. **Safety Patterns**: Non-criminal incidents dominate safety reports, with The Bronx showing disproportionate incident concentration
2. **Equity Implications**: Significant variance in school sizes and resources across boroughs affects program accessibility
3. **Data Quality**: Identified challenges with multi-year data, suppressed values, and DBN key alignment requiring careful handling
4. **Geographic Distribution**: School count and size inversely correlated—boroughs with more schools tend to have smaller average enrollments

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy matplotlib psycopg2-binary python-dotenv jupyter
```

### Database Connection
Create a `.env` file (not committed to repo):
```
DB_NAME=your_database
DB_USER=your_username
DB_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=5432
DB_SSLMODE=prefer
```

### Running Analyses
Navigate to respective folders and open Jupyter notebooks:
```bash
jupyter notebook 2_schools_directory_exploration/schools_directory_exploration.ipynb
jupyter notebook 3_database_queries/sql_analysis.ipynb
jupyter notebook 4_database_population/sat_modelling.ipynb
```

## 📝 Data Dictionary

Refer to `0_data/School_Safety_Report_Data_Dictionary.xlsx` for:
- Dataset metadata and source information
- Column definitions and data types
- Revision history and updates

## 🔐 Security Notes

- Database credentials stored in `.env` (included in `.gitignore`)
- Use `.env.example` template for team collaboration
- Never commit sensitive connection strings

## 🎯 Future Enhancements

- Time-series analysis of multi-year incident trends
- Predictive modeling for safety risk factors
- Interactive dashboards for real-time exploration
- Integration with additional demographic and performance datasets
- Automated data quality validation pipelines

## 👥 Contributors

Nuzhat Amna

---

📌 **Note**: This is an analytical project using publicly available NYC DOE data. All analyses are for educational and research purposes.