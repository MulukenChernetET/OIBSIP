# Data Cleaning — Customer Call List

## Objective
Take a deliberately messy customer dataset and systematically clean it into an 
analysis-ready dataset, documenting every decision made along the way.

## Dataset
Starting dataset: 21 rows, 8 columns of customer contact information 
(CustomerID, First_Name, Last_Name, Phone_Number, Address, Paying Customer, 
Do_Not_Contact, Not_Useful_Column).

## Data Quality Issues Found
- 1 duplicate row
- Missing values: Last_Name (1), Phone_Number (2), Do_Not_Contact (4)
- Inconsistent formatting in categorical columns (Paying Customer, Do_Not_Contact)
- A `Not_Useful_Column` with no analytical value

## Cleaning Steps
1. **Standardisation** :- normalised inconsistent Yes/No formatting in 
   `Paying Customer` and `Do_Not_Contact` columns.
2. **Missing value handling**:
   - `Last_Name` → filled with "Unknown" (no way to infer a missing name)
   - `Phone_Number` → left as null, flagged with a new `Phone_Missing` boolean 
     column, since a phone number cannot be reliably imputed
   - `Do_Not_Contact` → filled with "N" (assumed contactable unless explicitly 
     opted out)
3. **Duplicate removal** ;- 1 duplicate row identified and removed.
4. **Column removal** :- dropped `Not_Useful_Column`, which added no analytical value.
5. **Data type correction** :- cast `CustomerID` to string, since it's an 
   identifier, not a numeric quantity.

## Results
| Metric | Before | After |
|---|---|---|
| Row count | 21 | 20 |
| Null count | 8 | 2 |
| Duplicate count | 1 | 0 |

The 2 remaining nulls are intentional missing phone numbers that cannot be 
reliably imputed, tracked via the `Phone_Missing` flag column.

## Tech Stack
Python, pandas, numpy, Jupyter Notebook (Google Colab)

## Files
- `Cleaning_Data.ipynb`:full cleaning notebook with markdown commentary
- `cleaned_customer_data.csv` : final cleaned output
