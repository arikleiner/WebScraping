import requests
import bs4
import csv
import sys



res = requests.get("https://www.failory.com/startups/israel")

soup = bs4.BeautifulSoup(res.text,'html')

h3=soup.select('h3')

li=soup.select('li')

web=[]
for link in soup.find_all('a'):
    web.append(link.get('href'))

city=0
employees=1
funding=2
contweb=14

with open("101empresas.csv",'w',newline='') as output:
    writer = csv.writer(output,delimiter=" ")
    writer.writerow("CompanyName,CityName,EmployeesFrom,EmployeesTo,Funding")


    for n in h3:        
        desde = n.text.find(" ")
        
        companyname=n.text[desde+1::]
        cityname=li[city].text[6::]
        cantemployees=li[employees].text[21::].replace("-",",")
        fundingamouny=li[funding].text[17::].replace(",",".")
        
        print(companyname)
        print(cityname)
        print(cantemployees)
        print(fundingamouny)
        print(web[contweb])
        
        writer.writerow(companyname+','+cityname+','+cantemployees+','+fundingamouny)


        city+=3
        employees+=3
        funding+=3
        contweb+=1
        
output.close()
