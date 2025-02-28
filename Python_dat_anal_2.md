## Python_dat_anal_2.den

## PANDAS

-- treba si to prebehnut , vela pouzitelnych funkcii na datovu analyzu


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/basics.md


-- subory csv: https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/tree/main/data


```python
import pandas as pd

data = [['Alex', 10], ['Ronald', 18], ['Jane', 33]]
df = pd.DataFrame(data, columns=['Name', 'Age'])
df.index+=1
print(df)

print(df.columns)
print(df.values)
print(df.index)

print('----------------')

print(df.shape)
print(df.size)
```

-- info o suboroch

```python
import pandas as pd

df = pd.read_csv('products.csv') 
print(df.info())


import pandas as pd

df = pd.read_csv('mock_data.csv') 
print(df.info())
```

-- describe function


```python
import pandas as pd

s1 = pd.Series([1, 2, 3, 4, 5, 6, 7, 8])
s2 = pd.Series([12, 23, 31, 14, 11, 61, 17, 18])

data = {'Vals 1': s1, 'Vals 2': s2}
df = pd.DataFrame(data)

print(df.describe())
```
for a scecific collumn

```python
import pandas as pd

filename = 'mock_data2.csv'
df = pd.read_csv(filename)

print('basic stats for Entries')
summary_entries = df['entries'].describe()

print(summary_entries)
```


-- export do roznych formatov


![image](https://github.com/user-attachments/assets/77dd58ea-b140-4d8d-a86a-0f6af0e7b1fa)


--napr. do csv

```python
import pandas as pd

data = [['Alex', 10], ['Ronald', 18], ['Jane', 33]]
df = pd.DataFrame(data, columns=['Name', 'Age'])

df.to_csv('users.csv', index=False)
```

-- change index


```python
import pandas as pd

df = pd.read_csv("military_spending.csv") 
df.index = df.index + 1

print(df)
```

-- custom index

```python
import pandas as pd

data = {'country': ['Brazil', 'Russia', 'India', 'China', 'South Africa'],
        'capital': ['Brasilia', 'Moscow', 'New Dehli', 'Beijing', 'Pretoria'],
        'area': [8.516, 17.10, 3.286, 9.597, 1.221],
        'population': [200.4, 143.5, 1252, 1357, 52.98]}

df = pd.DataFrame(data)
print(df)

print('------------------------------')

df.index = ['BR', 'RU', 'IN', 'CH', 'SA']
print(df)
```

--no index

```python
import pandas as pd 
  
df = pd.read_csv("military_spending.csv") 

# print(df)
print(df.to_string(header=False, index=False))
```

## The inplace attribute


https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/basics.md#the-inplace-attribute

```python
import pandas as pd

file_name = 'countries.csv'

df = pd.read_csv(file_name)

# tu sa nebude nic menit, iba sa vypise
df2 = df.query("continent == 'Europe'")
print(df2)


# tu sa zmeni povodny dataframe
# df.query("continent == 'Europe'", inplace=True)
# print(df)
```

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/basics.md#data-type-inference


-- vyuzitie ake typy v DB mam nastavit pre dane stlpce


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/basics.md#converters


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/basics.md#missing-values

## IMPORT DATA

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/import.md

-- pip instal lxml

```python
import pandas as pd

# URL of the XML file
url = "https://webcode.me/users.xml"

# Read the XML data into a DataFrame
df = pd.read_xml(url)

# Display the DataFrame
print(df)
```

--https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/import.md#html-table-to-dataframe

```python
import pandas as pd

# URL of the HTML page containing the table
url = "https://webcode.me/users.html"

# Read the HTML table into a DataFrame
df_list = pd.read_html(url)

# The function returns a list of DataFrames, so we select the first one
df = df_list[0]

# Display the DataFrame
print(df)
```

--shmu udaje

```python
import pandas as pd

# URL of the HTML page containing the table
url = "https://www.shmu.sk/sk/?page=1&id=hydro_vod_all&station_id=5127"

# Read the HTML table into a DataFrame
df_list = pd.read_html(url)

# The function returns a list of DataFrames, so we select the first one
df = df_list[1]

# Display the DataFrame
print(df)
```



## PANDAS vs POSTGRES

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/import.md#postgresql-to-dataframe

```python
import pandas as pd

# Create the connection string
cs = 'postgresql://postgres:postgres@localhost/testdb'

# Execute a query to fetch data from the 'users' table
query = "SELECT * FROM users"
df = pd.read_sql_query(query, cs)

print(df)

```

-- hesla uchovavat v .env suboroch

DATABASE_URL=postgresql://postgres:s$cret@localhost/testdb

-- pip install python-decouple

```python
import pandas as pd
from decouple import config

# pip install decouple

# Load the connection string from the .env file
cs = config('DATABASE_URL')

# Execute a query to fetch data from the 'users' table
query = "SELECT * FROM users"
df = pd.read_sql_query(query, cs)

# Display the first 15 rows of the DataFrame
print(df.head(15).to_string(index=False))
```


## Stocks from Yahoo

https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/import.md#stocks-from-yahoo

-- pip install yfinance

```python
import yfinance as yf
import pandas as pd

# Define the ticker symbol
ticker_symbol = 'AAPL'

# Get data on this ticker
ticker_data = yf.Ticker(ticker_symbol)

# Get the historical prices for this ticker
df = ticker_data.history(period='1y')

# Ensure the date contains only the date part
df.index = df.index.date

# Display the DataFrame
print(df.tail(30))
```


## Streamlit
-- treba si prebehnut, velmi zaujmave funkcie

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md

-- pip instal streamlit

-- spustit: streamlit run streamlit_text.py

```python
import streamlit as st

st.title('Text input')

name = st.text_input('Enter your name:')

if name:
    st.write(f'Hello {name}!')
```

-- data table

```python
import streamlit as st
import pandas as pd

df = pd.read_csv('products.csv')

# Display title and description
st.title('Data Dashboard')
st.write('This is a simple data dashboard using Streamlit.')

# use table to display data
st.table(df.head(15))
```


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#text-input---slider


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#control-number-of-rows-with-slider

```python
import streamlit as st
import pandas as pd

df = pd.read_csv('products.csv')

st.title('Data Dashboard')

# Set the default number of rows to display
default_rows = 10

# Create a slider to control the number of rows
n = st.slider("Number of rows to display", 3, len(df), value=default_rows)

# Display the DataFrame with the selected number of rows
st.table(df.head(n))
```

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#line-chart

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#map-chart


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#scatter-plot-with-matplotlib

-- dalsia kniznica na grafy

-- streamlit run plotly_streallit_chart.py

```python
import streamlit as st
import plotly.express as px
import pandas as pd
import numpy as np

# Generate example data
data = {
    'Category': ['A', 'B', 'C', 'D'],
    'Quantity': [10, 20, 30, 40]
}

df = pd.DataFrame(data)

# Title of the app
st.title('Pie Chart Example')

# Create a pie chart
fig = px.pie(df, values='Quantity', names='Category', title='Quantity by Category')

# Display the pie chart using Streamlit
st.plotly_chart(fig)
```

## kniznica na grafy - plotly
https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#pie-chart-with-plotly
-- pip install plotly

https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#upload-a-file

```python
import streamlit as st
import pandas as pd

st.title('Upload CSV file')

# File uploader
uploaded_file = st.file_uploader('Choose a CSV file', type='csv')

if uploaded_file is not None:
    # Read the uploaded file
    df = pd.read_csv(uploaded_file)
    
    # Display the DataFrame
    st.write('Uploaded DataFrame:')
    st.write(df)
```


-- natiahnut csv subora a potom zapisat do DB


```python
import streamlit as st
import pandas as pd
from sqlalchemy import create_engine

st.title("CSV File Loader and Exporter to Local PostgreSQL")

# Function to upload CSV file
uploaded_file = st.file_uploader("Choose a CSV file", type=["csv"])

if uploaded_file is not None:
    # Read the CSV file
    df = pd.read_csv(uploaded_file)

    # Display the DataFrame
    st.write("File uploaded successfully!")
    st.write(df)

    # Request database connection parameters
    st.sidebar.subheader("Database Connection Parameters")
    host = st.sidebar.text_input("Host", "localhost")
    database = st.sidebar.text_input("Database", "testdb")
    user = st.sidebar.text_input("User", "postgres")
    password = st.sidebar.text_input("Password", type="password")
    table_name = st.sidebar.text_input("Table Name", "Test")

    # Function to export DataFrame to PostgreSQL
    def export_to_postgresql(df, host, database, user, password, table_name):
        # Create the connection string
        engine = create_engine(f'postgresql://{user}:{password}@{host}/{database}')
        # Export DataFrame to PostgreSQL
        df.to_sql(table_name, engine, if_exists='replace', index=False)

    # Export the DataFrame to PostgreSQL
    if st.button("Export to PostgreSQL"):
        export_to_postgresql(df, host, database, user, password, table_name)
        st.write("Data exported to PostgreSQL successfully!")

else:
    st.write("No file uploaded.")
```

## Markdown

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#markdown

```python
import streamlit as st
import pandas as pd

# Title of the app
st.title('Streamlit markdown')

# Display a simple DataFrame
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'Occupation': ['Engineer', 'Doctor', 'Artist']
})

st.write('Simple DataFrame:')
st.write(df)

# Display some markdown text
st.markdown('This is **Streamlit**. You can write *markdown* too!')

st.markdown('Python *source code*')

st.markdown('''
~~~python
import streamlit as st
import pandas as pd

# Title of the app
st.title('Streamlit markdown')

# Display a simple DataFrame
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'Occupation': ['Engineer', 'Doctor', 'Artist']
})

st.write('Here is a simple DataFrame:')
st.write(df)

# Display some markdown text
st.markdown('This is **Streamlit**. You can write *markdown* too!')
~~~ ''')
```

![image](https://github.com/user-attachments/assets/e88b6364-e6e1-4042-88b2-17cccd610eec)



## Database example


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#database-example

- novy adresar test + otvorit folder vo vs code
- do neho adresar .streamlit
- do neho secrets.loml :
```python
  [connections.postgresql]
type="sql"
dialect = "postgresql"
host = "localhost"
port = "5432"
database = "testdb"
username = "postgres"
password = "postgres"
```
- main.py do adresara test a spustit streamlit run main.py

![image](https://github.com/user-attachments/assets/10cb326b-9bbd-4d5b-ae18-a8093d054ef7)


![image](https://github.com/user-attachments/assets/b7925f6d-8674-4cd3-b241-5c4da5922869)


## PAGES

https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#pages

```python
import streamlit as st
import pandas as pd
import numpy as np


def page1():
    st.title("Page 1: Random Data")
    df = pd.DataFrame(np.random.randn(10, 5), columns=[
                      'A', 'B', 'C', 'D', 'E'])
    st.dataframe(df)


def page2():
    st.title("Page 2: Emojis")
    st.write("Here are some emojis:")
    st.write(":smile:", ":heart:", ":joy:", ":heart_eyes:", ":cry:", 
             ":thumbsup:", ":thumbsdown:", ":raised_hands:", ":tada:",
             ":birthday:", ":dog:", ":sunglasses:", ":pleading_face:", ":shrug:", 
             ":sparkles:", ":pizza:", ":star2:", ":books:", ":art:")


def page3():
    st.title("Page 3: Lorem Ipsum")
    st.write("""
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu
fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in
culpa qui officia deserunt mollit anim id est laborum.
""")


page_names = ["Random Data", "Emojis", "Lorem Ipsum"]
selected_page = st.sidebar.selectbox("Select a Page", page_names)

if selected_page == "Random Data":
    page1()
elif selected_page == "Emojis":
    page2()
else:
    page3()
```

![image](https://github.com/user-attachments/assets/b85990f3-45be-42bc-92be-321d7ae12bee)


## Multi pages

https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/streamlit.md#multi-page-app-with-configuration


![image](https://github.com/user-attachments/assets/7afb9e6f-10ad-4a5f-9736-9ac5d41c329b)

![image](https://github.com/user-attachments/assets/f2f18f81-79ab-4497-a432-917379d40d72)


## SELECTOLAX  - parsovanie html,xml dokumentov

https://zetcode.com/python/beautifulsoup/

## live server -- online sa aplikuju zmeny, ktore urobim v html po save .py suboru

## web scrabing bazos

```python
import itertools
from bs4 import BeautifulSoup
import httpx
import time
import asyncio

base_url = 'https://reality.bazos.sk'
url = 'https://reality.bazos.sk/predam/byt/'
urls = []
pages = []


def get_main_content_div(soup):
    main_content_div = soup.find('div', class_='maincontent')
    return main_content_div


def get_number_of_ads(main_content_div):
    inzer_text = main_content_div.find('div', class_='inzeratynadpis').text
    return int(inzer_text[inzer_text.find('inzerátov z') + len('inzerátov z'):].replace(' ', ''))


def get_links(main_content_div):
    h2_tags = main_content_div.find_all(
        'h2', class_='nadpis') if main_content_div else []

    # Find all links within these h2 tags
    links = [h2_tag.find('a')['href']
             for h2_tag in h2_tags if h2_tag.find('a')]

    if not links:
        print('No links found')
        exit(1)

    return links


def write_to_file(urls):
    with open('links.txt', 'w') as f:
        for url in urls:
            f.write(f'{url}\n')


async def get_async(url):
    async with httpx.AsyncClient() as client:
        return await client.get(url)

# def batched(iterable, n):
#     it = iter(iterable)
#     batch = list(itertools.islice(it, n))
#     while batch:
#         yield batch
#         batch = list(itertools.islice(it, n))


async def launch():

    resp = httpx.get(url)
    soup = BeautifulSoup(resp.text, 'lxml')

    main_content_div = get_main_content_div(soup)
    n_ads = get_number_of_ads(main_content_div)
    print(n_ads)

    for n in range(1, n_ads + 1, 20):
        page = f'{base_url}/predam/byt/{n}/'
        pages.append(page)

    # print(pages)
    # for batch in itertools.batched(pages, 20):
    #     print(batch)

    for batch in itertools.batched(pages, 20):
        print('start batch', time.time())
        resps = await asyncio.gather(*[get_async(page) for page in batch])
        for resp in resps:
            soup = BeautifulSoup(resp.text, 'lxml')
            main_content_div = get_main_content_div(soup)
            new_links = get_links(main_content_div)
            new_urls = [f'{base_url}{link}' for link in new_links]
            urls.extend(new_urls)
        
        print('finished batch')
        await asyncio.sleep(2)

    write_to_file(urls)

asyncio.run(launch())
```
