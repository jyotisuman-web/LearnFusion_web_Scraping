import requests
from bs4 import BeautifulSoup
import pandas as pd
url='https://www.python.org'
request=requests.get(url)
print(request)
s=BeautifulSoup(request.text,"html.parser")
print(s.prettify())
print(s.title)
button=s.find('button').text
print("Button ->",button)
for tag in s.find_all(True):
    print(tag.name)
target_div = s.find('div', {'class': 'row'})
p_elements = target_div.find_all('p')
table = []

for item in s.find_all('div', class_='small-widget'):
    title = item.find('h2', class_='widget-title').text #if item.find('h2', class_='widget-title') else None
    first_paragraph = item.find('p').text # if item.find('p') else None
    link = item.find('a').text.strip() if item.find('a') else None
    entry = {
        'title': title,
        'description': first_paragraph,
        'links': link
    }
    table.append(entry)

df = pd.DataFrame(table)
df.to_csv('events.csv', index=False)
# Print the DataFrame
print("Data saved to events.csv")
eventlist=[]
ul=s.select_one('ul.menu')
for li in ul.find_all('li'):
      title=li.find('href')
      event=li.find('a').text.strip()
      entry={
        'Event':event,

      }
      eventlist.append(entry)
df=pd.DataFrame(eventlist)
print(df)
