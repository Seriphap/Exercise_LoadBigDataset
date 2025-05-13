# Exercise_LoadBigDataset
<br>

## Step1: Download CSV file into Dataframe
<p><font size="4">&nbsp;&nbsp;&nbsp;Dataset: https://drive.google.com/file/d/1njGRC9gjmnbi9qGLmzRQj4MyMyPDHp1h/view?usp=drive_link </p>

- Install gdown library for download file from google drive
```python
!pip install gdown
```

- Download file from google drive 
```python
import dask.dataframe as dd
import gdown

file_id = '1njGRC9gjmnbi9qGLmzRQj4MyMyPDHp1h'
url = f'https://drive.google.com/uc?id={file_id}'

# Download the file
gdown.download(url, '/content/downloaded_file.csv', quiet=False)

# Read CSV with Dask
df = dd.read_csv('/content/downloaded_file.csv')
```

## Step2: Show the data information
```python
display(df.dtypes) # Display column data types (metadata)
```
<img src="https://github.com/user-attachments/assets/e552fe81-f43d-48da-be2b-7e30307337d5" width="30%">

## Step3: Show example data (10 rows)
```python
display(df.head(10))
num_rows = len(df.compute())
print(f"Number of rows: {num_rows}")
```
<img src="https://github.com/user-attachments/assets/72edd14c-5e86-40e2-92f1-e420cc9d4eef" width="150%">

## Step4: Show summary statistics data
```python
print("\nSummary statistics:")
display(df.describe().compute())  # Trigger computation with compute()
```
<img src="https://github.com/user-attachments/assets/6217c681-419e-4352-846c-30f6403c56f8" width="100%">


