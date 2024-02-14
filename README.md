# **Surviving the Tech Turmoil: Analyzing Layoffs in the Tech Industry**
## Introduction
In recent years, the tech industry has experienced significant turmoil, with layoffs affecting companies of all sizes. From established giants to nimble startups, no one has been immune to the impact of economic shifts, technological disruptions, and changing market dynamics. In this analysis, we delve into the world of tech layoffs, examining their causes, consequences, and implications for the industry.

## Project Team: 
- Abdul Dawson
- Casey Clayton
- Cassandra Griffin
- Cody Schneggenburger
- Dylan Ross
- Shantesh Dalal

## Table of Contents
- [Data Source](#data-source)
- [Key Questions](#key-questions)
- [Methodology](#methodology)
- [Technologies Used](#technologies-used)
- [Industry Analysis](#industry-analysis) 
- [Company Analysis](#company-analysis)
- [Funding Stage Analysis](#funding-stage-analysis)
- [Conclusion](#conclusion)

## Data Source
Our analysis draws from a comprehensive dataset spanning the years 2020 to 2024. This dataset, available on Kaggle, provides detailed information about layoffs across various tech companies. By analyzing this data, we aim to uncover patterns, identify vulnerable sectors, and offer insights into how organizations can navigate these challenging times.
- [Dataset 1][(https://www.kaggle.com/datasets/ulrikeherold/tech-layoffs-2020-2024)]

## Key Questions
1. **Magnitude of Layoffs**: How extensive have tech layoffs been in recent years?
2. **Company Profiles**: Which companies have been most affected by layoffs?
3. **Sector Vulnerability**: Are certain tech sectors more susceptible to workforce reductions?
4. **Company Maturity Vulnerability**: How do layoffs vary across different funding stages? 
   
## Methodology
Our research focused on three key areas: the hardest-hit industries, the companies with the most layoffs, and how company funding stages affect layoffs. We narrowed our data to USA firms for consistency and conducted a thorough initial analysis to eliminate anomalies. After refining the dataset for accuracy, we standardized all records to ensure reliable insights.

## Technologies Used
- Python
- Pandas
- Matplotlib

# Industry Analysis 
We analyzed the layoffs in the tech sector from 2020 to 2024, to determine what industrys were most effected and to identify any trends. 
## Code Snippits
The follow is a significant portion of the code used to clean, filter, and visualize the data for industry level analysis
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

## Summary of Industry Analysis Findings

Our analysis of layoffs across various industries reveals a significant concentration in the top five sectors, which account for 56% of the total layoffs. The Consumer industry is the most affected, bearing 18% of the total layoffs, indicative of broader economic challenges and shifting consumer behavior impacting the sector.

The remaining 44% of layoffs are spread across 27 other industries, demonstrating the far-reaching impact of market dynamics and industry-specific factors. The Consumer industry, along with Other categories and Transportation, leads in the number of job cuts, with a staggering 50,217 layoffs in the Consumer sector alone.

These figures underscore the significant challenges and shifts within these sectors, particularly in the context of the COVID-19 pandemic. The layoffs in the Consumer industry mirror disruptions in supply chains, changes in consumer spending habits, and the accelerated transition to digital services, necessitating a restructuring in workforce allocation.

Our chronology of layoffs within the tech industry provides insight into the industry's stability over time. A notable statistic is the mere nine layoffs in 2021, suggesting a period of relative stability or effective adaptation to the pandemic's initial economic impacts. However, 2022 saw a dramatic surge with over 350 layoffs, painting a picture of a sector grappling with ongoing challenges, possibly emerging from the pandemic's extended effects, and leading many tech companies to reevaluate and substantially reduce their workforce.

# Company Analysis 
We conducted a data analysis of the top 5 tech companies (Amazon, Apple, Google, Microsoft, and Meta) and the broader tech industry, focusing on the number and impact of layoffs from 2020 to 2024.


## Code Snippits  
The follow is a significant portion of the code used to clean, filter, and visualize the data for Company level analysis
```
# compare companies with most layoff
# take top 5 companies compared to rest of the industry

# rename SaleSan Franciscoorce
df_usa.loc[df_usa['Company'] == 'SaleSan Franciscoorce', 'Company'] = 'Salesforce'

# groupby Company Layoffs
company_layoffs = df_usa.groupby('Company')['Laid_Off'].sum()
company_size_before = df_usa.groupby('Company')['Company_Size_before_Layoffs'].sum()
company_size_after = df_usa.groupby('Company')['Company_Size_after_layoffs'].sum()
usa_top_5_layoffs = company_layoffs.nlargest(5)
rest_companies = company_layoffs.drop(usa_top_5_layoffs.index)
rest_layoffs = rest_companies.sum()

top_5_size_before = company_size_before.loc[usa_top_5_layoffs.index]
top_5_size_after = company_size_after.loc[usa_top_5_layoffs.index]

# Get median values for rest of the companies
rest_size_before = company_size_before.loc[rest_companies.index].median()
rest_size_after = company_size_after.loc[rest_companies.index].median()
```
```
# Plotting the bar chart
plt.figure(figsize=(10, 6))

# Width of each bar
bar_width = 0.25

# Position of bars on x-axis
r1 = np.arange(len(usa_top_5_layoffs))
r2 = [x + bar_width for x in r1]
r3 = [x + bar_width for x in r2]

# Plotting bars for top 5 companies' size before layoffs
bars1 = plt.bar(r1, top_5_size_before / 100000, color='dodgerblue', width=bar_width, label='Size Before Layoffs')

# Plotting bars for total layoffs
bars2 = plt.bar(r2, usa_top_5_layoffs / 100000, color='orange', width=bar_width, label='Total Layoffs')

# Plotting bars for top 5 companies' size after layoffs
bars3 = plt.bar(r3, top_5_size_after / 100000, color='green', width=bar_width, label='Size After Layoffs')

# Adding labels to the bars
plt.xlabel('Top 5 Companies', fontweight='bold')
plt.xticks([r + bar_width for r in range(len(usa_top_5_layoffs))], usa_top_5_layoffs.index, rotation=45)
plt.ylabel('Number of Employees (x 100k)', fontweight='bold')
plt.title('Company Size Before, Layoffs, and After for Top 5 Companies (2020-2024)', fontweight='bold')
plt.legend()

# Adding values above each bar
for bars in [bars1, bars2, bars3]:
    for bar in bars:
        height = bar.get_height()
        plt.text(bar.get_x() + bar.get_width() / 2, height, f'{height:.1f}', ha='center', va='bottom', fontsize=8)

plt.tight_layout()
plt.show()
```
## Summary of Company Analysis Findings
We conducted a data analysis of the top 5 tech companies (Amazon, Apple, Google, Microsoft, and Meta) and the broader tech industry, focusing on the number and impact of layoffs from 2020 to 2024. Our main findings are:

The top 5 tech companies accounted for 29.6% of the total layoffs in the tech sector, with 81,150 employees losing their jobs. The rest of the industry had 192,831 layoffs, representing 70.4% of the total.
Meta, the smallest of the top 5 tech firms, had the highest percentage reduction in staff post-layoffs, with a 23.7% decrease in headcount. This suggests that being a leading tech company does not guarantee immunity from drastic organizational changes.
Amazon, the largest of the top 5 tech firms, had the lowest percentage reduction in staff post-layoffs, with only a 3.2% decrease in headcount. This indicates that Amazon was able to maintain a strong workforce despite the industry challenges.
The other three tech giants (Apple, Google, and Microsoft) had moderate percentage reductions in staff post-layoffs, ranging from 8.9% to 12.4%. This shows that they also faced some difficulties in retaining their employees, but not as severely as Meta.
Our analysis reveals the varying effects of layoffs on the top 5 tech companies and the rest of the industry, highlighting the diversity and complexity of the tech sector.

# Funding Stage Analysis
We analyzed the layoffs in the tech sector from 2020 to 2024, to dertermine what effect company maturity had on layoffs. To do this we defined company maturity on the company funding stages.
## Code Snippits
The follow is a significant portion of the code used to clean, filter, and visualize the data for Funding Stage analysis
```
# Clean the data
# Check for duplicates in the Company column sorted by Date_layoffs
duplicated_df = df_a.duplicated(subset=['Company']).sum()

# List all duplicates in the Country column sorted by Date_layoffs

#duplicated = df_a[df_a.duplicated(subset=['Company'])]
duplicated_df = df_a[df_a.duplicated(subset=['Company'])].sort_values(by='Date_layoffs')
 # duplicated_df
# Show the duplicated data
print(duplicated_df)
```
```
# Show the average percentage of layoffs by company stage using a bar chart
df_sorted = df_a.sort_values(by='Stage')

bar_width = 0.35

plt.figure(figsize=(15, 12))
plt.bar(df_sorted['Stage'], df_sorted['Percentage'], alpha=0.7, label='Overall')
average_percentage_by_stage = df_sorted.groupby('Stage')['Percentage'].mean()
plt.bar(average_percentage_by_stage.index, average_percentage_by_stage.values, alpha=0.5, label='Average Percentage', color = 'red')
for i, value in enumerate(average_percentage_by_stage.values):
    plt.text(i, value + 0.5, f'{value:.2f}%', ha='center', color='black')

plt.xlabel('Company Stage', color = 'red', fontsize = 15)
plt.ylabel('Percentage', color = 'red', fontsize = 15) 
plt.xticks(rotation=45, ha='right')
plt.title('Percentage of Layoffs by Company Stage', color = 'red', fontsize = 20)
plt.grid(axis='y')
plt.legend(loc = 'upper left', bbox_to_anchor = (1.02, 1))
plt.tight_layout()
plt.show()

```
```
# Show the percentages of layoffs by company stage using a box plot

plt.figure (figsize=(12, 8))
plt.boxplot([df_a[df_a['Stage'] == stage]['Percentage'] for stage in stage_count_df.index], labels=stage_count_df.index)
plt.xlabel('Company Stage', color = 'red')
plt.xticks(rotation=45, ha = 'right')
plt.xticks(color='blue')
plt.ylabel('Percentage', color = 'red')
plt.yticks(color='blue')
plt.grid(axis = 'y')
plt.title('Layoffs by Company Stage', color = 'red', fontsize = 20)
plt.show()
```


## Summary of Funding Stage Analysis Findings
We analyzed the layoffs in the tech sector from 2020 to 2024, based on the company funding stages. Our main findings are:

Post-IPO companies had the highest number of layoffs, with 54,321 employees losing their jobs. This may be due to the pressure of the public markets and their larger size.
Series B and C companies had the second and third highest number of layoffs, with 28,764 and 26,431 employees losing their jobs, respectively. This may reflect the challenges they face in scaling and adapting to the market during these growth phases.
We created a box plot chart to show the percentage of layoffs at each stage of company growth. We filtered our dataset to only include the companies that had layoffs during this period. The chart shows the range and median of the layoff percentages for each stage, from seed to post-IPO.
The chart reveals that seed and start-up companies had the highest median layoff percentage, with 18.7% and 17.4%, respectively. This suggests that these early-stage companies were disproportionately affected by the layoff storm, possibly due to their limited resources and uncertain prospects.
The post-IPO companies had the lowest median layoff percentage, with 7.3%, indicating that they were able to retain most of their employees despite the industry challenges. However, they also had the largest range of layoff percentages, from 0.8% to 23.7%, showing that some post-IPO companies were more vulnerable than others.
Our analysis provides a comprehensive overview of the layoffs in the tech sector from 2020 to 2024, based on the company funding stages. 

# Conclusion
Our analysis underscores a fundamental reality: no tech company is shielded from the possibility of layoffs; they are a consequential facet of the industry's rhythm, influenced by the natural ebb and flow of business cycles, market trends, and the relentless pace of innovation. By examining the data across various sectors, company sizes, and stages of funding maturity, we gain insight into the myriad of factors that can precipitate workforce adjustments. By understanding these dimensions—industry conditions, organizational growth phases, and financial stability—we can better comprehend the layoff landscape within the tech ecosystem.


