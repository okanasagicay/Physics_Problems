# Task 07 – Standard Deviation

## Problem Statement

Eleven students received the following test scores:

$$
88, \ 92, \ 79, \ 85, \ 95, \ 81, \ 86, \ 90, \ 83, \ 77, \ 89
$$

Calculate the mean $\bar{x}$ and standard deviation $\sigma$ using:

$$
\bar{x} = \frac{1}{N} \sum_{i=1}^{N} x_i
$$

$$
\sigma = \sqrt{\frac{1}{N-1} \sum_{i=1}^{N} (x_i - \bar{x})^2}
$$

Then remove the highest and lowest scores and recalculate.

## Step-by-Step Solution

### Part 1: All 11 scores

**Step 1: Calculate the sum**

$$
\sum x_i = 88 + 92 + 79 + 85 + 95 + 81 + 86 + 90 + 83 + 77 + 89
$$

$$
= 88 + 92 = 180
$$
$$
180 + 79 = 259
$$
$$
259 + 85 = 344
$$
$$
344 + 95 = 439
$$
$$
439 + 81 = 520
$$
$$
520 + 86 = 606
$$
$$
606 + 90 = 696
$$
$$
696 + 83 = 779
$$
$$
779 + 77 = 856
$$
$$
856 + 89 = 945
$$

$$
\sum x_i = 945
$$

**Step 2: Calculate the mean**

$$
\bar{x} = \frac{945}{11} = 85.909\ldots \approx 85.91
$$

**Step 3: Calculate deviations and squared deviations**

| $x_i$ | $x_i - \bar{x}$ | $(x_i - \bar{x})^2$ |
|-------|----------------|---------------------|
| 88    | 2.09           | 4.3681              |
| 92    | 6.09           | 37.0881             |
| 79    | -6.91          | 47.7481             |
| 85    | -0.91          | 0.8281              |
| 95    | 9.09           | 82.6281             |
| 81    | -4.91          | 24.1081             |
| 86    | 0.09           | 0.0081              |
| 90    | 4.09           | 16.7281             |
| 83    | -2.91          | 8.4681              |
| 77    | -8.91          | 79.3881             |
| 89    | 3.09           | 9.5481              |

**Step 4: Sum of squared deviations**

$$
\sum (x_i - \bar{x})^2 = 4.3681 + 37.0881 + 47.7481 + 0.8281 + 82.6281
$$
$$
+ 24.1081 + 0.0081 + 16.7281 + 8.4681 + 79.3881 + 9.5481
$$

$$
= 311.0 \ \text{(approximately)}
$$

**Step 5: Calculate standard deviation**

$$
\sigma = \sqrt{\frac{311.0}{11 - 1}} = \sqrt{\frac{311.0}{10}} = \sqrt{31.10} = 5.577
$$

Round to two decimals:

$$
\sigma \approx 5.58
$$

**Results for all 11 scores:**

$$
\bar{x} = 85.91, \quad \sigma = 5.58
$$

---

### Part 2: Remove highest (95) and lowest (77)

Remaining scores: $88, 92, 79, 85, 81, 86, 90, 83, 89$

$N = 9$

**Step 1: New sum**

$$
\sum x_i = 945 - 95 - 77 = 945 - 172 = 773
$$

**Step 2: New mean**

$$
\bar{x}_{\text{new}} = \frac{773}{9} = 85.888\ldots \approx 85.89
$$

**Step 3: Squared deviations from new mean**

| $x_i$ | $x_i - 85.89$ | $(x_i - 85.89)^2$ |
|-------|---------------|-------------------|
| 88    | 2.11          | 4.4521            |
| 92    | 6.11          | 37.3321           |
| 79    | -6.89         | 47.4721           |
| 85    | -0.89         | 0.7921            |
| 81    | -4.89         | 23.9121           |
| 86    | 0.11          | 0.0121            |
| 90    | 4.11          | 16.8921           |
| 83    | -2.89         | 8.3521            |
| 89    | 3.11          | 9.6721            |

**Step 4: Sum of squared deviations**

$$
\sum = 4.4521 + 37.3321 + 47.4721 + 0.7921 + 23.9121 + 0.0121 + 16.8921 + 8.3521 + 9.6721
$$

$$
= 148.8889 \approx 148.89
$$

**Step 5: New standard deviation**

$$
\sigma_{\text{new}} = \sqrt{\frac{148.89}{9 - 1}} = \sqrt{\frac{148.89}{8}} = \sqrt{18.61125} = 4.314
$$

Round to two decimals:

$$
\sigma_{\text{new}} \approx 4.31
$$

## Final Results

| Dataset | Mean $\bar{x}$ | Standard Deviation $\sigma$ |
|---------|----------------|-----------------------------|
| All 11 scores | 85.91 | 5.58 |
| Without highest and lowest | 85.89 | 4.31 |

## Interpretation

Removing the extreme values (95 and 77) slightly decreases the mean (85.91 → 85.89) but significantly reduces the standard deviation from 5.58 to 4.31. This shows that outliers increase the spread of data. The new standard deviation better represents the consistency of the central cluster of scores.
