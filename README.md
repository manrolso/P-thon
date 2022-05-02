# P-thon
Basic Python student. Would like to see this brief code working and pulling data from a web page, so far I have:

import requests
from bs4 import BeautifulSoup

encabezados = {
    'Origin': 'http://fiddle.jshell.net',
    'Accept-Encoding': 'gzip, deflate',
    'Accept-Language': 'en-US,en;q=0.8',
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/100.0.4896.127 Safari/537.36',
    'Content-Type': 'application/x-www-form-urlencoded; charset=UTF-8',
    'Accept': '*/*',
    'Referer': 'http://fiddle.jshell.net/_display/',
    'X-Requested-With': 'XMLHttpRequest',
    'Connection': 'keep-alive',
}

datos = {
    'ScriptManager1': 'UpdatePanel1|btnConsultaCedula',
    '__LASTFOCUS': '',
    '__EVENTTARGET': '',
    '__EVENTARGUMENT': '',
    '__VIEWSTATE': '/wEPDwULLTE1OTIyMjMwMDVkZK8IAFVVrLVZ94xw80rFsu4opljJCVOXUsSfBJSod1T8',
    '__VIEWSTATEGENERATOR': '88BF6952',
    '__EVENTVALIDATION': '/wEdAAmsgmX2ZUY16L/wbsAezXirtTfNpOz0CH4vKngBfzxDIS2hNtLCXCKq92TKMjYS4CX24YOX6Ab2AoRRJXYcN6RPZrHMfDaOuX2c5DuODJSeiypYaPycT+v9uchEvEhJB0tWvoSmUD9cccAzkkmmOR9zkJ/OtIbU04qfUHmBu0NaRFCfQQ61frM+tUgerGfangbkVNG4e7R+/Xmh2Mum3zsAWZf7AC16Gtse4KjiO5c0yg==',
    'txtcedula': "108660676",
    'grupo': '',
    'comentario': '',
    '__ASYNCPOST': 'true',
    'btnConsultaCedula': 'Consultar',
}

url = "https://servicioselectorales.tse.go.cr/chc/consulta_cedula.aspx/"

response = requests.post(url,headers=encabezados,data=datos)

soup = BeautifulSoup(response.text, features="html.parser")
data = [item.text for item in soup.select("form1")]
print(*data, sep="\n")

#print(soup)
print(response.text)

