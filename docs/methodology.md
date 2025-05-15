# Methods and Computations

This section details specific assumptions and methods used by Parameters Analyzer.

## Target Selection
Once you select the target variable and its OK range or values, it's binarized into 2 classes: OK and NOK ("Not OK").

## Data Assumptions and Definitions

**Outlier filtering for numerical variables:** Values below the 1.5th percentile and above the 98.5th percentile are excluded to remove extreme outliers that distort analysis. This ensures more representative results, clearer graphs, and actionable conclusions. You can disable outlier filtering by setting `outliers_filtering` to `False`.

**Binning of values:** This divides data for each variable into "bins" or intervals. For numerical variables, [numpy.histogram](https://numpy.org/doc/stable/reference/generated/numpy.histogram.html) determines bin edges based on value distribution. For categorical variables, each unique category becomes a bin. Only the 30 most populated modalities are displayed.

By default, 10 bins are computed. Change the tab setting to increase bin resolution up to 30 bins.

**Default rates of variables:** For each variable, the average NOK rate is calculated as the proportion of values outside the target variable's good range.

**Default rates of bins:** For each bin, the defect rate is calculated and compared to the variable's average NOK rate.

**Impact of variables:** Impact is calculated as the product of the absolute difference between the bin's default rate and the variable's average default rate, multiplied by the proportion of data points in the bin. Bins with default rates much higher or lower than average and containing many data points have high impact.

**Ranking of variables:** For each variable, the absolute impact of all bins is summed. Variables are ranked by importance, with the highest total impact first. This importance measure is normalized between 0 and 100 and determines the top 30 most important variables to display.

**Display of results:** Each graph shows the variable's average default rate. Bubbles are positioned based on their default rate, with size corresponding to points in the bin. Color is red if the bin's default rate exceeds the variable's default rate, green otherwise.