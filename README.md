# Titanic Dataset Exploratory Data Analysis

## Project Overview

This project performs Exploratory Data Analysis (EDA) on the Titanic dataset using **Pandas, NumPy, Matplotlib, and Seaborn**. The main objective is to understand the factors that influenced passenger survival during the Titanic disaster.

The analysis focuses on identifying survival patterns based on gender, passenger class, age, embarked port, fare, and family size.

---

## Objective

The main goal of this project is to answer the following questions:

- What was the overall survival rate?
- Did gender affect survival?
- Did passenger class affect survival?
- How did gender and passenger class together affect survival?
- Did age or age group influence survival?
- Did embarked port have any relationship with survival?
- Were higher fares associated with better survival chances?
- Did family size affect individual survival probability?

---

## Dataset Information

The dataset contains passenger-level information from the Titanic.

### Dataset Shape

- Rows: 891
- Columns: 12 before cleaning

### Important Columns

| Column | Description |
|---|---|
| PassengerId | Unique passenger ID |
| Survived | Survival status: 0 = Not Survived, 1 = Survived |
| Pclass | Passenger class: 1 = First, 2 = Second, 3 = Third |
| Name | Passenger name |
| Sex | Gender of passenger |
| Age | Age of passenger |
| SibSp | Number of siblings/spouses aboard |
| Parch | Number of parents/children aboard |
| Ticket | Ticket number |
| Fare | Ticket fare |
| Cabin | Cabin number |
| Embarked | Port of embarkation: C = Cherbourg, Q = Queenstown, S = Southampton |

---

## Tools and Libraries Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook / Google Colab

---

## Data Cleaning

The dataset contained missing values in the following columns:

| Column | Missing Values |
|---|---:|
| Age | 177 |
| Cabin | 687 |
| Embarked | 2 |

### Cleaning Steps Performed

- Filled missing `Age` values using the median age.
- Filled missing `Embarked` values using the mode.
- Dropped the `Cabin` column because it had too many missing values.
- Checked duplicate rows.
- Created new columns:
  - `survival_status`
  - `Age_Group`
  - `Fare_Group`
  - `FamilySize`
  - `Family_Category`

---

## Exploratory Data Analysis

### 1. Overall Survival

Out of 891 passengers:

- 342 passengers survived.
- 549 passengers did not survive.

The overall survival rate was approximately **38.38%**.

**Insight:**  
The Titanic dataset shows a low overall survival rate, making it important to analyze which passenger characteristics were linked with higher survival chances.

---

### 2. Survival by Gender

Female passengers had a much higher survival rate than male passengers.

| Gender | Survival Rate |
|---|---:|
| Female | 74.20% |
| Male | 18.89% |

**Insight:**  
Gender was one of the strongest survival factors. Female passengers were much more likely to survive, likely because women were prioritized during rescue.

---

### 3. Survival by Passenger Class

| Passenger Class | Survival Rate |
|---|---:|
| 1st Class | 62.96% |
| 2nd Class | 47.28% |
| 3rd Class | 24.24% |

**Insight:**  
Passenger class strongly affected survival. First-class passengers had the highest survival rate, while third-class passengers had the lowest survival rate.

---

### 4. Survival by Gender and Passenger Class

| Gender | Class | Survival Rate |
|---|---:|---:|
| Female | 1 | 96.81% |
| Female | 2 | 92.11% |
| Female | 3 | 50.00% |
| Male | 1 | 36.89% |
| Male | 2 | 15.74% |
| Male | 3 | 13.54% |

**Insight:**  
The combination of gender and class gave a stronger explanation of survival. Female passengers in first and second class had the highest survival chances, while male passengers in third class had very low survival chances.

---

### 5. Survival by Age

Most passengers were young adults, mainly between 20 and 35 years. The median age of both survivors and non-survivors was around 28 years.

**Insight:**  
Age alone was not the strongest survival factor because survivors and non-survivors had similar median ages. However, age becomes useful when analyzed in groups.

---

### 6. Survival by Age Group

| Age Group | Survival Rate |
|---|---:|
| Child | 57.97% |
| Teenager | 42.86% |
| Young Adult | 35.33% |
| Adult | 40.00% |
| Senior | 22.73% |

**Insight:**  
Children had the highest survival rate, while seniors had the lowest survival rate. This suggests that children may have been prioritized during rescue.

---

### 7. Survival by Embarked Port

| Embarked Port | Survival Rate |
|---|---:|
| Cherbourg | 55.36% |
| Queenstown | 38.96% |
| Southampton | 33.90% |

**Insight:**  
Cherbourg had the highest survival rate, but embarked port should not be interpreted alone. The difference is connected with passenger class and gender distribution.

---

### 8. Embarked Port vs Passenger Class

| Embarked | 1st Class | 2nd Class | 3rd Class |
|---|---:|---:|---:|
| C | 50.60% | 10.12% | 39.29% |
| Q | 2.60% | 3.90% | 93.51% |
| S | 19.97% | 25.39% | 54.64% |

**Insight:**  
Cherbourg had a much higher percentage of first-class passengers, which helps explain its higher survival rate.

---

### 9. Embarked Port vs Gender

| Embarked | Female | Male |
|---|---:|---:|
| C | 43.45% | 56.55% |
| Q | 46.75% | 53.25% |
| S | 31.73% | 68.27% |

**Insight:**  
Queenstown had a higher female percentage than Southampton. This helps explain why Queenstown’s survival rate was slightly higher than Southampton despite having mostly third-class passengers.

---

### 10. Survival by Fare

Fare distribution was highly right-skewed. Most passengers paid low fares, while only a few passengers paid very high fares.

| Fare Group | Survival Rate |
|---|---:|
| Very Low | 19.94% |
| Low | 43.30% |
| Medium | 48.21% |
| High | 62.32% |
| Very High | 73.58% |

**Insight:**  
Passengers who paid higher fares generally had higher survival rates. However, fare is closely related to passenger class, so it should be interpreted together with `Pclass`.

---

### 11. Survival by Family Size

Most passengers were traveling alone.

| Family Category | Survival Rate |
|---|---:|
| Alone | 30.35% |
| Small Family | 57.88% |
| Large Family | 16.13% |

**Insight:**  
Passengers traveling with small families had better individual survival rates than passengers traveling alone or with large families. Very large families had low survival rates, but those groups had small sample sizes, so the result should be interpreted carefully.

---

### 12. Correlation Heatmap

The correlation heatmap showed that:

- `Fare` had a positive relationship with survival.
- `Pclass` had a negative relationship with survival because higher class numbers represent lower passenger classes.
- Numerical correlation alone is not enough for this dataset because many important features are categorical.

---

## Final Conclusion

Titanic survival was influenced by multiple factors. The strongest patterns were found in **gender** and **passenger class**. Female passengers and first-class passengers had much higher survival chances.

Other features such as age, fare, embarked port, and family size also showed meaningful patterns, but they should be interpreted together because many of them are connected.

Overall, passengers were more likely to survive if they were:

- Female
- First class
- Children
- Paying higher fares
- Traveling with a small family

Passengers were less likely to survive if they were:

- Male
- Third class
- Traveling alone
- Part of a very large family

---

## Project Files

```text
Titanic_EDA_Project/
│
├── EDA_On_Titanic_Dataset.ipynb
├── Titanic-Dataset.csv
└── README.md
```

---

## Key Skills Practiced

- Data loading and inspection
- Handling missing values
- Feature engineering
- GroupBy analysis
- Crosstab analysis
- Data visualization
- Histogram, barplot, boxplot, countplot, and heatmap
- Writing observations and insights from data

---

## Author

Divyansh Pratap Singh

