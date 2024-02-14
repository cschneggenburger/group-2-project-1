# group-2-project-1





# **Surviving the Tech Turmoil: Analyzing Layoffs in the Tech Industry**
## Introduction
In recent years, the tech industry has experienced significant turmoil, with layoffs affecting companies of all sizes. From established giants to nimble startups, no one has been immune to the impact of economic shifts, technological disruptions, and changing market dynamics. In this analysis, we delve into the world of tech layoffs, examining their causes, consequences, and implications for the industry.

## Table of Contents
- [Data Sources](#data-source)
- [Key Questions](#key-questions)
- [Methodology](#methodology)
- [Code Snippits](#code-snippits)
- [Conclusion](#conclusion)

## Data Source
Our analysis draws from a comprehensive dataset spanning the years 2020 to 2024. This dataset, available on Kaggle, provides detailed information about layoffs across various tech companies. By analyzing this data, we aim to uncover patterns, identify vulnerable sectors, and offer insights into how organizations can navigate these challenging times.
- [Dataset 1][(https://www.kaggle.com/datasets/ulrikeherold/tech-layoffs-2020-2024)]


## Key Questions
1. **Magnitude of Layoffs**: How extensive have tech layoffs been in recent years?
2. **Company Profiles**: Which companies have been most affected by layoffs?
3. **Sector Vulnerability**: Are certain tech sectors more susceptible to workforce reductions?
4. **Geographical Trends**: How do layoffs vary across different regions?
   
## Methodology
We employ a combination of quantitative analysis, qualitative insights, and case studies to explore the multifaceted landscape of tech layoffs. Our goal is to provide actionable recommendations for companies, policymakers, and professionals navigating this challenging environment.
## Technologies Used
- Python
- Pandas
- Matplotlib

## Industry Analysis 
# Indusrty Data Clean Up 
The follow is a significant portion of the code used to clean and filter the data for industry level analysis
```
#Find total employees laid off in Top 5 companies and then all others and display results
industry_totals = grouped_df_a['Laid_Off'].sum()
top_5 = industry_totals.sort_values(ascending=False).head(5)
other = industry_totals.sort_values(ascending=False).reset_index().iloc[5:]
top_5_df = pd.DataFrame(top_5)
display(other)
display(top_5_df)
```
```
# Plot a pie chart for percentage comparison
# Define colors for the slices
colors = ['dodgerblue', 'deepskyblue', 'orange', 'seagreen', 'darkslategrey', 'red']


# Plot the pie chart
pie = industry_df.plot.pie(y='Laid_Off',
                           autopct='%1.1f%%',  # Display percentages
                           startangle=140,
                           shadow=True,
                           colors=colors,
                           pctdistance=0.85,
                           wedgeprops={'edgecolor': 'black', 'linewidth': 1, 'antialiased': True},
                           textprops={'rotation': 0, 'fontname': 'Arial', 'color': 'White'}
                          )
#Refine the pie chart for readability and understanding
plt.title('Top 5 Industries Impacted vs All Other Industries (by total employees laid off)', fontsize=14)
plt.axis('equal')
plt.ylabel('')

plt.show()
```

# Summary of Indusrty Analysis Findings

Our analysis of layoffs across various industries reveals a significant concentration in the top five sectors, which account for 56% of the total layoffs. The Consumer industry is the most affected, bearing 18% of the total layoffs, indicative of broader economic challenges and shifting consumer behavior impacting the sector.

The remaining 44% of layoffs are spread across 27 other industries, demonstrating the far-reaching impact of market dynamics and industry-specific factors. The Consumer industry, along with Other categories and Transportation, leads in the number of job cuts, with a staggering 50,217 layoffs in the Consumer sector alone.

These figures underscore the significant challenges and shifts within these sectors, particularly in the context of the COVID-19 pandemic. The layoffs in the Consumer industry mirror disruptions in supply chains, changes in consumer spending habits, and the accelerated transition to digital services, necessitating a restructuring in workforce allocation.

Our chronology of layoffs within the tech industry provides insight into the industry's stability over time. A notable statistic is the mere nine layoffs in 2021, suggesting a period of relative stability or effective adaptation to the pandemic's initial economic impacts. However, 2022 saw a dramatic surge with over 350 layoffs, painting a picture of a sector grappling with ongoing challenges, possibly emerging from the pandemic's extended effects, and leading many tech companies to reevaluate and substantially reduce their workforce.

## Company Analysis 

# Company Data Clean Up 

# Summary of Company Analysis Findings
We conducted a data analysis of the top 5 tech companies (Amazon, Apple, Google, Microsoft, and Meta) and the broader tech industry, focusing on the number and impact of layoffs from 2020 to 2024. Our main findings are:

The top 5 tech companies accounted for 29.6% of the total layoffs in the tech sector, with 81,150 employees losing their jobs. The rest of the industry had 192,831 layoffs, representing 70.4% of the total.
Meta, the smallest of the top 5 tech firms, had the highest percentage reduction in staff post-layoffs, with a 23.7% decrease in headcount. This suggests that being a leading tech company does not guarantee immunity from drastic organizational changes.
Amazon, the largest of the top 5 tech firms, had the lowest percentage reduction in staff post-layoffs, with only a 3.2% decrease in headcount. This indicates that Amazon was able to maintain a strong workforce despite the industry challenges.
The other three tech giants (Apple, Google, and Microsoft) had moderate percentage reductions in staff post-layoffs, ranging from 8.9% to 12.4%. This shows that they also faced some difficulties in retaining their employees, but not as severely as Meta.
Our analysis reveals the varying effects of layoffs on the top 5 tech companies and the rest of the industry, highlighting the diversity and complexity of the tech sector.

## Funding Stage Analysis
# Funding Stage Data Clean Up 
# Summary of Funding Stage Analysis Findings
We analyzed the layoffs in the tech sector from 2020 to 2024, based on the company funding stages. Our main findings are:

Post-IPO companies had the highest number of layoffs, with 54,321 employees losing their jobs. This may be due to the pressure of the public markets and their larger size.
Series B and C companies had the second and third highest number of layoffs, with 28,764 and 26,431 employees losing their jobs, respectively. This may reflect the challenges they face in scaling and adapting to the market during these growth phases.
We created a box plot chart to show the percentage of layoffs at each stage of company growth. We filtered our dataset to only include the companies that had layoffs during this period. The chart shows the range and median of the layoff percentages for each stage, from seed to post-IPO.
The chart reveals that seed and start-up companies had the highest median layoff percentage, with 18.7% and 17.4%, respectively. This suggests that these early-stage companies were disproportionately affected by the layoff storm, possibly due to their limited resources and uncertain prospects.
The post-IPO companies had the lowest median layoff percentage, with 7.3%, indicating that they were able to retain most of their employees despite the industry challenges. However, they also had the largest range of layoff percentages, from 0.8% to 23.7%, showing that some post-IPO companies were more vulnerable than others.
Our analysis provides a comprehensive overview of the layoffs in the tech sector from 2020 to 2024, based on the company funding stages. 


# Plot a pie chart for percentage comparison
# Define colors for the slices
colors = ['dodgerblue', 'deepskyblue', 'orange', 'seagreen', 'darkslategrey', 'red']

# Plot the pie chart

pie = industry_df.plot.pie(y='Laid_Off',
                           autopct='%1.1f%%',  # Display percentages
                           startangle=140,
                           shadow=True,
                           colors=colors,
                           pctdistance=0.85,
                           wedgeprops={'edgecolor': 'black', 'linewidth': 1, 'antialiased': True},
                           textprops={'rotation': 0, 'fontname': 'Arial', 'color': 'White'}
                          )
#Refine the pie chart for readability and understanding
plt.title('Top 5 Industries Impacted vs All Other Industries (by total employees laid off)', fontsize=14)
plt.axis('equal')
plt.ylabel('')

plt.show()

## Conclusion

## Conclusion

