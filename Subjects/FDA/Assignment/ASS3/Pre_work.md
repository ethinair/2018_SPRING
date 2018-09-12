### Web scrapping [9/12]
```

# reference 
https://www.youtube.com/watch?v=XQgXKtPSzUI

# i find three diff src website could find the results
# 1 http://geospatial.dcgis.dc.gov/propertywebservice/SSLSearch.asmx?op=findBySquareSuffixLot
# 2 https://www.taxpayerservicecenter.com/RP_Search.jsp?search_type=Assessment
# 3 http://dcatlas.dcgis.dc.gov/mar/ 
# among them, the 2nd one has the simplest structure
```

from urllib.request import urlopen as uReq
from bs4 import BeautifulSoup as soup

```
# my_url = 'http://dcatlas.dcgis.dc.gov/mar/location_detail.aspx'
# this url is wrong -> since get nothing from it

# tips -> we can change the input from the url ssl=xxx or go back to the src page
my_url = "https://www.taxpayerservicecenter.com/RP_Detail.jsp?ssl=0866%20%20%20%200021"

#opening a connection -> grabbing the page
uClient = uReq(my_url)
page_rst = uClient.read()
uClient.close()

#html parser
#soup is a datatype
page_soup = soup(page_rst,"html.parser")

# findAll function of soup 
# this one is locate based on class(i change it to span since the infor i need is w/i span -> result:didn't work)
# how to locate based on specific key word since sometimes there are many value
# -> in the same class but diff location.
# {object}

# blackblue4 = page_soup.findAll('span',{"class":"blackblue4"})
# container = page_soup.findAll(div",{"class":"mar_table_details_container"})

contentPadding = page_soup.findAll("div",{"class":"contentPadding"})

# now we need loc the useful info -> from outside to inside
# contentPadding.form.table.tbody -> didn't work
# need to learn the structure of html

```
