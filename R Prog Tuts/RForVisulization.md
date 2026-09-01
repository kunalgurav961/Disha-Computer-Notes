# Visualization in R Programming

Visualization is one of the most powerful parts of R programming. It helps you understand data, detect patterns, compare groups, identify outliers, and communicate results clearly. In R, visualizations can be created using:

- Base R plotting functions
- ggplot2 package
- Lattice and other specialized packages

This note focuses on practical and common visualization techniques in R, with examples and explanations.

---

## 1. Why Data Visualization Matters

A good chart can answer questions like:

- Is there a trend over time?
- Are values increasing or decreasing?
- Are there outliers?
- Do two variables have a relationship?
- Which category is largest or smallest?

Without visualization, raw numbers are hard to interpret.

Example:

```r
sales <- c(120, 150, 130, 190, 210, 250)
print(sales)
```

This list of values is difficult to understand quickly. A chart makes the pattern obvious.

---

## 2. Getting Started with Plotting in Base R

Base R already contains plotting functions. This is good for quick visual exploration.

### Example 1: Simple Scatter Plot

```r
x <- c(1, 2, 3, 4, 5, 6)
y <- c(5, 8, 11, 14, 17, 20)

plot(x, y)
```

### Explanation

- `x` and `y` are vectors of numeric values.
- `plot(x, y)` creates a scatter plot.
- Each point represents one x-y pair.
- This is useful to see relationships between two variables.

### Example 2: Scatter Plot with Labels and Title

```r
x <- c(10, 20, 30, 40, 50)
y <- c(15, 25, 30, 45, 60)

plot(x, y,
     main = "Sales vs. Advertising Spend",
     xlab = "Advertising Spend",
     ylab = "Sales",
     pch = 19,
     col = "blue")
```

### Explanation

- `main` adds the plot title.
- `xlab` and `ylab` label the axes.
- `pch = 19` changes the point symbol to a filled circle.
- `col = "blue"` changes the point color.

This chart helps you see if sales increase as advertising spend increases.

---

## 3. Line Charts

Line charts are useful when data is ordered by time or sequence.

### Example 3: Line Plot

```r
months <- c("Jan", "Feb", "Mar", "Apr", "May", "Jun")
profit <- c(2000, 2500, 2800, 3200, 3600, 4100)

plot(1:length(months), profit,
     type = "o",
     main = "Monthly Profit",
     xlab = "Month",
     ylab = "Profit (in INR)",
     col = "darkgreen",
     lwd = 2,
     xaxt = "n")

axis(1, at = 1:length(months), labels = months)
```

### Explanation

- `type = "o"` means both points and lines are plotted.
- `lwd = 2` increases line thickness.
- The result shows a trend over time.

Line plots are ideal for time series or continuous progression.

---

## 4. Bar Charts

Bar charts compare values across categories.

### Example 4: Simple Bar Plot

```r
courses <- c("R", "Python", "SQL", "Excel", "Java")
students <- c(120, 95, 80, 110, 67)

barplot(students,
        names.arg = courses,
        col = "orange",
        main = "Number of Students in Each Course",
        xlab = "Courses",
        ylab = "Students")
```

### Explanation

- `courses` contains category names.
- `students` contains the values for each category.
- `names.arg = courses` labels each bar.
- `col = "orange"` adds color.

Bar plots are excellent for comparing counts or totals across groups.

### Example 5: Horizontal Bar Plot

```r
cities <- c("Delhi", "Mumbai", "Bangalore", "Chennai", "Hyderabad")
population <- c(30, 20, 12, 11, 10)

barplot(population,
        names.arg = cities,
        horiz = TRUE,
        col = "steelblue",
        main = "City Population")
```

### Explanation

- `horiz = TRUE` makes the bars horizontal.
- This is useful when category names are long.

---

## 5. Histograms

Histograms show the distribution of a numeric variable.

### Example 6: Histogram

```r
marks <- c(52, 61, 68, 77, 81, 85, 89, 90, 94, 97, 59, 63, 70, 75, 78)

hist(marks,
     breaks = 5,
     col = "purple",
     border = "white",
     main = "Distribution of Student Marks",
     xlab = "Marks",
     ylab = "Frequency")
```

### Explanation

- Histogram divides values into intervals (bins).
- `breaks = 5` creates 5 bins.
- The chart shows how frequently values fall into each range.
- This is useful for checking distribution shape, symmetry, and skewness.

---

## 6. Box Plots

Box plots show the spread, center, and outliers of a dataset.

### Example 7: Box Plot

```r
scores <- list(
  GroupA = c(55, 60, 65, 70, 72, 75, 80),
  GroupB = c(40, 43, 48, 52, 63, 68, 72, 78),
  GroupC = c(70, 73, 78, 82, 85, 88, 90)
)

boxplot(scores,
        col = c("lightblue", "lightgreen", "lightpink"),
        main = "Comparison of Scores Across Groups",
        ylab = "Scores",
        xlab = "Groups")
```

### Explanation

- Each box represents a group.
- The thick line inside the box is the median.
- The box shows the middle 50% of data.
- Whiskers show the range.
- Points outside whiskers are potential outliers.

Box plots are useful for comparing groups and checking spread.

---

## 7. Pie Charts

Pie charts show proportions of a whole.

### Example 8: Pie Chart

```r
expenses <- c(35, 25, 20, 15, 5)
labels <- c("Food", "Rent", "Education", "Transport", "Savings")

pie(expenses,
    labels = labels,
    main = "Monthly Expense Distribution",
    col = c("gold", "skyblue", "lightgreen", "tomato", "gray"))
```

### Explanation

- The size of each slice is proportional to its value.
- Useful when you want to show parts of a whole.
- Pie charts are best when the number of categories is small.

Note: Pie charts are less informative for many categories compared to bar plots.

---

## 8. Density Plots

Density plots estimate the probability distribution of continuous data.

### Example 9: Density Plot

```r
set.seed(123)
values <- rnorm(500, mean = 50, sd = 10)

plot(density(values),
     main = "Density Plot of Random Values",
     xlab = "Values",
     col = "darkred",
     lwd = 2)
```

### Explanation

- `rnorm(500, mean = 50, sd = 10)` generates 500 random values from a normal distribution.
- `density(values)` estimates the shape of the data distribution.
- The curve shows where data is concentrated.

Density plots are useful for continuous data analysis and distribution comparisons.

---

## 9. Scatter Plot Matrix

A scatter plot matrix shows relationships between multiple variables.

### Example 10: Pairs Plot

```r
df <- data.frame(
  height = c(150, 160, 170, 165, 175, 180, 155, 168),
  weight = c(50, 55, 65, 60, 70, 80, 52, 62),
  age = c(22, 24, 26, 25, 28, 29, 23, 27)
)

pairs(df)
```

### Explanation

- `pairs(df)` creates a matrix of scatter plots.
- Each variable is compared with the others.
- This helps identify possible correlations between variables.

---

## 10. Plotting with `ggplot2`

`ggplot2` is the most popular package for data visualization in R. It uses a grammar of graphics, where you build plots layer by layer.

### Install and Load

```r
install.packages("ggplot2")
library(ggplot2)
```

### Example 11: Scatter Plot in `ggplot2`

```r
df <- data.frame(
  hours = c(1, 2, 3, 4, 5, 6),
  score = c(20, 30, 45, 55, 70, 80)
)

ggplot(df, aes(x = hours, y = score)) +
  geom_point(size = 3, color = "blue") +
  geom_line(color = "darkblue") +
  labs(title = "Study Hours vs Score",
       x = "Hours Studied",
       y = "Score") +
  theme_minimal()
```

### Explanation

- `ggplot(df, aes(x = hours, y = score))` initializes the plot.
- `aes()` defines which variables map to x and y axes.
- `geom_point()` adds scatter points.
- `geom_line()` adds a connecting line.
- `labs()` adds labels.
- `theme_minimal()` gives a clean style.

This is more readable and flexible than base R plotting.

### Example 12: Bar Plot in `ggplot2`

```r
sales <- data.frame(
  product = c("A", "B", "C", "D"),
  revenue = c(500, 700, 600, 900)
)

ggplot(sales, aes(x = product, y = revenue, fill = product)) +
  geom_bar(stat = "identity") +
  labs(title = "Product Revenue",
       x = "Product",
       y = "Revenue") +
  theme_classic()
```

### Explanation

- `geom_bar(stat = "identity")` uses exact values from the data.
- `fill = product` gives each bar a different color.
- The plot compares revenue across products.

### Example 13: Histogram in `ggplot2`

```r
set.seed(42)
values <- rnorm(300, mean = 100, sd = 15)

plot_df <- data.frame(values)

ggplot(plot_df, aes(x = values)) +
  geom_histogram(binwidth = 5, fill = "tomato", color = "black") +
  labs(title = "Histogram of Values",
       x = "Value",
       y = "Count") +
  theme_bw()
```

### Explanation

- `geom_histogram()` creates a histogram.
- `binwidth = 5` controls the width of each bin.
- Color and theme improve readability.

---

## 11. Customizing Plots

R plots can be adjusted in many ways for publication or presentation.

### Example 14: Custom Graphic Style

```r
x <- c(1, 2, 3, 4, 5)
y <- c(5, 8, 11, 14, 18)

plot(x, y,
     type = "b",
     main = "Customized Plot",
     xlab = "X Axis",
     ylab = "Y Axis",
     col = "red",
     pch = 17,
     cex = 1.5,
     lwd = 2,
     bg = "yellow")
```

### Explanation

- `type = "b"` draws both points and lines.
- `pch = 17` changes the symbol.
- `cex = 1.5` enlarges point size.
- `lwd = 2` increases line width.
- `bg = "yellow"` sets a background color.

This makes plots more visually attractive and easier to read.

---

## 12. Faceting in `ggplot2`

Faceting splits a plot by groups.

### Example 15: Faceted Plot

```r
iris_df <- iris

ggplot(iris_df, aes(x = Sepal.Length, y = Sepal.Width)) +
  geom_point(color = "darkgreen") +
  facet_wrap(~ Species) +
  labs(title = "Sepal Length vs Width by Species",
       x = "Sepal Length",
       y = "Sepal Width") +
  theme_light()
```

### Explanation

- `facet_wrap(~ Species)` creates separate plots for each species.
- This helps compare subgroups within the same dataset.
- It is extremely useful in exploratory data analysis.

---

## 13. Saving Plots

After creating a chart, you may want to save it to a file.

### Example 16: Save a Plot as PNG

```r
png("my_plot.png", width = 800, height = 600)
plot(1:10, 1:10, main = "Example Plot")
dev.off()
```

### Explanation

- `png()` opens a PNG device.
- `dev.off()` closes the graphics device and saves the file.

Other formats include:

```r
pdf("my_plot.pdf")
plot(1:10, 1:10)
dev.off()
```

This allows you to include visual output in reports or presentations.

---

## 14. Important Plotting Concepts

### a) Axis labels

Axis labels explain what the graph is showing.

```r
plot(c(1,2,3,4), c(4,6,8,10), xlab = "Time", ylab = "Value")
```

### b) Main title

```r
plot(c(1,2,3,4), c(4,6,8,10), main = "Trend Over Time")
```

### c) Color

```r
plot(1:5, 1:5, col = "red", pch = 16)
```

### d) Point type and size

```r
plot(1:5, 1:5, pch = 19, cex = 2)
```

These small details make the plot clearer and more professional.

---

## 15. Choosing the Right Chart

Different charts are useful for different questions:

- Scatter plot: relationship between two numeric variables
- Line chart: change over time
- Bar plot: comparison of categories
- Histogram: distribution of single variable
- Box plot: spread and outliers
- Pie chart: proportion of total
- Density plot: probability distribution
- Heatmap: pattern in a matrix or table

### Example 17: Heatmap

```r
mat <- matrix(c(1, 2, 3, 4,
                5, 6, 7, 8,
                9, 10, 11, 12), nrow = 3, byrow = TRUE)

heatmap(mat, col = heat.colors(12), scale = "none")
```

### Explanation

- Heatmaps represent data values with colors.
- They are useful for large matrices and pattern detection.
- Darker or brighter colors represent different magnitude values.

---

## 16. Working with Real Data Example

Let's use a sample dataset for visualization in R.

```r
students <- data.frame(
  Name = c("Amit", "Neha", "Rohit", "Pooja", "Sanjay"),
  Math = c(78, 85, 90, 72, 88),
  Science = c(80, 76, 92, 68, 84),
  English = c(74, 82, 79, 88, 90)
)

print(students)
```

### Example 18: Compare Marks in a Bar Chart

```r
barplot(as.matrix(students[, 2:4]),
        beside = TRUE,
        legend.text = students$Name,
        col = c("red", "green", "blue", "orange", "purple"),
        main = "Student Subject-wise Marks",
        xlab = "Subjects",
        ylab = "Marks")
```

### Explanation

- `as.matrix(students[, 2:4])` converts the marks into a matrix.
- `beside = TRUE` places bars side by side.
- `legend.text = students$Name` adds a legend.
- This helps compare multiple students across subjects.

---

## 17. Best Practices for Visualization

- Use meaningful titles and labels.
- Avoid cluttered plots.
- Choose the correct chart type.
- Use colors carefully.
- Keep legends understandable.
- Consider the audience.
- Make plots simple and readable.

---

## 18. Summary

Visualization in R is a key step in data analysis. Common charts include:

- Scatter plot
- Line plot
- Bar chart
- Histogram
- Box plot
- Pie chart
- Density plot
- Heatmap

Base R is useful for quick plotting, while `ggplot2` is better for advanced, elegant, and publication-quality graphs.

With practice, you can build plots that make data interpretation faster and more effective.

---

## 19. Small Practice Questions

1. Create a scatter plot for two numeric vectors.
2. Plot monthly sales using a line chart.
3. Create a bar plot for category-wise data.
4. Use a histogram to show data distribution.
5. Use `ggplot2` to create a box plot.
6. Save a graph in PNG format.

---

## 20. Quick Example: A Complete `ggplot2` Workflow

```r
library(ggplot2)

# Sample data
sales_data <- data.frame(
  month = factor(c("Jan", "Feb", "Mar", "Apr", "May", "Jun"),
                 levels = c("Jan", "Feb", "Mar", "Apr", "May", "Jun")),
  sales = c(200, 250, 300, 400, 380, 450)
)

# Plot
p <- ggplot(sales_data, aes(x = month, y = sales, group = 1)) +
  geom_line(color = "blue", size = 1.2) +
  geom_point(size = 3, color = "red") +
  labs(title = "Monthly Sales Trend",
       x = "Month",
       y = "Sales") +
  theme_minimal()

print(p)
```

### Explanation

- We create a data frame with month and sales values.
- `geom_line()` draws the trend line.
- `geom_point()` adds markers at each point.
- `labs()` sets the chart labels.
- `theme_minimal()` gives a clean style.

This is a typical workflow used in real analysis projects.

---

## Final Thought

R is one of the best languages for data visualization because it offers both simple built-in plotting and advanced plotting libraries. Start with base R for understanding, then move to `ggplot2` for professional and attractive visualizations.

The key is not only to create charts, but to choose the correct visualization that tells the truth in the data clearly and effectively.
