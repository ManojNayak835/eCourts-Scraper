# eCourts-Scraper
import requests
from bs4 import BeautifulSoup
from datetime import datetime, timedelta

url = "https://services.ecourts.gov.in/ecourtindia_v6/"

response = requests.post(url, headers=headers, data=data)


def is_listed_today_or_tomorrow(next_hearing_date):
    if next_hearing_date is None:
        return False
    today = datetime.today().date()
    tomorrow = today + timedelta(days=1)
    return next_hearing_date == today or next_hearing_date == tomorrow


case_number = input("Enter case number: ")
court_name = "GUNJAN GOYAL (Incharge) ADJ IV" 
year = input("enter the case year")

if is_listed_today_or_tomorrow:
    print("Case is listed today or tomorrow:")
    print("   Case Number:", case_number)
    print("   Court Name :", court_name)
else:
    print("Not listed today or tomorrow.")
    print("Not available")

soup = BeautifulSoup(response.text, 'html.parser')
