# NYC High School Directory Exploration

Analysis of NYC high school directory data examining school counts, enrollment, and grade coverage patterns across boroughs.

**Source data:** `0. data/high-school-directory.csv`

## Tasks Performed
1. Loaded and cleaned high school directory data (standardized columns, fixed dtypes, handled nulls)
2. Filtered borough subsets and calculated unique school counts
3. Aggregated enrollment metrics (mean, sum) by borough
4. Analyzed grade coverage (`grade_span_max`) patterns
5. Created visualizations for school counts, total students, and average students per borough

## Key Insights

**School Distribution:**
- Brooklyn: 121 schools | Bronx: 118 | Manhattan: 106 | Queens: 80 | Staten Island: 10

**Enrollment Patterns:**
- Brooklyn serves most students (~83,197 total) with moderate school sizes
- Staten Island has highest average per school (~1,848 students) with fewest schools
- Bronx has smallest average size (~490 students), indicating many small, community-focused schools

**Grade Coverage:**
- Most boroughs consistently reach Grade 12 (means ~11.8–12.0)
- Staten Island schools uniformly serve through Grade 12
- Queens shows slightly more variation (some schools cap at Grades 10–11)

**Equity Implications:**
- Nearly 4x variance in school size between Bronx and Staten Island suggests different resource needs and operational models
- Trade-off between fewer large schools (Queens/Staten Island) vs. many smaller schools (Bronx/Manhattan) affects program breadth and local accessibility