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

## Key Questions
1. **Magnitude of Layoffs**: How extensive have tech layoffs been in recent years?
2. **Company Profiles**: Which companies have been most affected by layoffs?
3. **Sector Vulnerability**: Are certain tech sectors more susceptible to workforce reductions?
4. **Geographical Trends**: How do layoffs vary across different regions?
5. **Impact on Innovation**: What implications do layoffs have for technological innovation?
   
## Methodology
We employ a combination of quantitative analysis, qualitative insights, and case studies to explore the multifaceted landscape of tech layoffs. Our goal is to provide actionable recommendations for companies, policymakers, and professionals navigating this challenging environment.
## Technologies Used
- Python
- Pandas
- Matplotlib
- Seaborn
## Data Sources
List the sources of your data. Include links if available.

- [Dataset 1][(https://www.kaggle.com/datasets/ulrikeherold/tech-layoffs-2020-2024)]

## Data Clean Up 
The follow is a significant portion of the code used to clean and filter the data for industry level analysis
#Find total employees laid off in Top 5 companies and then all others and display results
industry_totals = grouped_df_a['Laid_Off'].sum()
top_5 = industry_totals.sort_values(ascending=False).head(5)
other = industry_totals.sort_values(ascending=False).reset_index().iloc[5:]
top_5_df = pd.DataFrame(top_5)
display(other)
display(top_5_df)

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

In the coming sections, we'll dive deeper into the data, uncovering trends, success stories, and cautionary tales. Whether you're a tech executive, an investor, or a curious observer, join us on this journey through the tech turmoil.
Stay tuned for our next installment, where we'll explore the impact of layoffs on specific companies and sectors.
¹: [Source: Kaggle - Tech Layoffs Dataset](https://www.kaggle.com/techcrunch/2023-and-2024-tech-layoffs)

## Conclusion

