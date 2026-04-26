# Future You Simulator

> Enter your skills today. See your salary in 1, 3, and 5 years.
> Change one habit — watch your future change.

Built for the Prophecy Virtual Hackathon Spring 2026.

## What it does

Uses Prophecy AI agents to analyse 65,000+ Stack Overflow 2024 
Survey responses and simulate career trajectories based on real 
developer data. Includes a what-if engine that shows how changing 
one skill or habit shifts your projected salary.

## Key findings

- Full-stack developers at 21 years experience: $117,043 median
- Python only ($79,481) beats JavaScript only ($68,389) at median
- Bash/Shell is the #1 hidden skill gap for Developer Advocates
- Rust + cloud skills = 13.3% LOWER salary (counterintuitive!)
- Indian full-stack devs adding cloud skills: +32.1% salary premium

## Prophecy Pipelines

### Prompt 1 — Data cleaning
"Filter rows where MainBranch = 'I am a developer by profession' 
and Employment = 'Employed, full-time' and ConvertedCompYearly 
is not null and ConvertedCompYearly > 5000 and 
ConvertedCompYearly < 300000. Keep only these columns: 
ResponseId, Age, DevType, YearsCode, YearsCodePro, 
LanguageHaveWorkedWith, Country, EdLevel, WorkExp, 
ConvertedCompYearly, JobSat, Industry."

### Prompt 2 — Salary simulation
"Group the cleaned data by DevType and YearsCodePro. Calculate 
median ConvertedCompYearly, average JobSat, most frequent 
Industry, and count of respondents. Filter out groups with fewer 
than 20 respondents. Sort by median ConvertedCompYearly descending."

### Prompt 3 — Skill gap analysis
"Split respondents into high earners (above 75th percentile) and 
low earners (below 50th percentile). For each DevType, find top 5 
most common LanguageHaveWorkedWith values per band. Show languages 
in high band but not low band."

### Prompt 4 — What-if engine
"Compare median ConvertedCompYearly for: Python only, JavaScript 
only, and both. Break down by YearsCodePro ranges 0-2, 3-5, 6-10."

### Prompt 5 — India cloud premium
"For developers in India with DevType containing full-stack and 
YearsCodePro 0-5, show median ConvertedCompYearly grouped by 
LanguageHaveWorkedWith. Re-run filtering those with cloud skills 
from PlatformHaveWorkedWith. Show salary delta."

## Data source

Stack Overflow Annual Developer Survey 2024  
https://www.kaggle.com/datasets/berkayalan/stack-overflow-annual-developer-survey-2024?resource=download
65,437 respondents — free and open

## Author

Aditya Patel — Prophecy Virtual Hackathon Spring 2026
