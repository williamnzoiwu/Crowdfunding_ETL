# Crowdfunding_ETL
## Project 2
This Jupyter notebook extracts data from Excel files and then downloads them as CSV files.

### Category and Subcategory DataFrames
It first reads a Excel file called "crowdfunding.xlsx". It takes the info from the "categories" and "subcategories" columns and puts them into list, and then extracts the data to create category and subcategory DataFrames with the columns ["category_id", "category"] and ["subcategory_id.", "subcategory"] respectively.  The rows in the "category_id" column are then modified to be listed as "cat#" (cat1, cat2, cat3, etc.), and similarly with the values in the "subcategory_id" column as "subcat#". Both DataFrames are then exported as csv files: "category.csv" and "subcategory.csv".

### Campaign DataFrame
Next, the crowdfunding Excel file is then copied as a DataFrame "campaign_df". The columns "blurb", "launched_at", and "deadline" are then renamed as "description", "launched_date", and "end_date" respectively (The subcategory column was also renamed here from "sub-category" to "subcategory" so it would match the one in the subcategory DataFrame). Then the values in the "goal" and "pledged" columns are changed from integer to float types. Next, the values in the "launched_date" and "end_date" columns are changed from integers to datetime format. Next the campaign DataFrame is merged with the category and subcategory Dataframes to add the columns "category_id" and "subcategory_id" to the campaign_df. Lastly, the columns "staff_pick", "spotlight", "category & sub-category", "category", and "subcategory" are all dropped from the DataFrame, and the finished campaign Dataframe is exported as a csv file called "campaign.csv".

### Contacts DataFrame
Next, the contacts Dataframe is created using regular expression. The data is first extracted from the Excel file "contacts.xlsx" and then copied to a Dataframe with all the values starting in a single column called "text". From there, the contact id is extracted to a column called "contact_id", the names to a new column calles "name", and the emails to a column The three new columns are then created in another dataframe without the "text" column. The first and last names are then extacted from the "name" column into two new columns called "first_name" and "last_name". The name column is then dropped from the DataFrame, and the DataFrame is exported to a csv file calles "contacts.csv".

### Crowdfunding Schema
Afer all the csv files are created, their respective tables are all created in a sql schema with their same columns and respective files uploaded. The crowdfunding table is created with the primary key "cf_id" and the foreign keys "contact_id", "category_id", and "subcategory_id", with those being the primary keys in the contacts, category, and subcategory tables respectively. After all the tables are created, they are then loaded with the corresponding data from their previously created csv files.
