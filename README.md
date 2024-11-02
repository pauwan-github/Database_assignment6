import matplotlib.pyplot as plt

# Calculate total expenses by category
category_totals = data.groupby('Category')['Amount'].sum()

#Create a bar chart
plt.figure(figsize=(10, 6))
category_totals.plot(kind='bar', color='skyblue')
plt.title("Total Expenses by Category - March 2023")
plt.xlabel("Category")
plt.ylabel("Total Amount Spent")
plt.xticks(rotation=45)
plt.show()

#Prepare data for daily trends
data['Day'] = data['Date'].dt.day  # Extract day from Date
daily_totals = data.groupby('Day')['Amount'].sum()

#Create a line graph
plt.figure(figsize=(10, 6))
daily_totals.plot(kind='line', marker='o', color='purple')
plt.title("Daily Expense Trends - March 2023")
plt.xlabel("Day of the Month")
plt.ylabel("Total Daily Expenses")
plt.grid(True)
plt.show()

# Create pie chart for spending proportions
plt.figure(figsize=(8, 8))
category_totals.plot(kind='pie', autopct='%1.1f%%', startangle=140)
plt.title("Spending Proportions by Category - March 2023")
plt.ylabel('')  # Hide the y-label for cleaner presentation
plt.show()

