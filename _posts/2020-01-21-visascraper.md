---
title: "VisaScraper"
date: "2020-01-21"
layout: single
tags:
- Automation
categories:
- Projects
---

# VisaScraper

VisaScraper is a tool that is used to get visa cards using mitm attack
and is used as a bot to get first to use every publicly published card
on carding websites using an account. Basically it sees every post and
checks for "|", "&", "$" known separators and sees card's data and kills
it, As you are continously refresh the website for new cards to kill it
before everybody else so i created that bot to do it for me.

**Example Code** on Altenens website and "|" separator:
```python
import requests
from bs4 import BeautifulSoup as bs
import re


ch = []
alreadycn = []
cn = 0
cv = 0
ct = 0
ce = 0
ced = 0

def getCardType(cardnumber):
	z = requests.get("https://bincheck.org/"+cardnumber[0:6])
	z = bs(z.text, "html.parser")
	daz = z.find_all("a")
	return daz[5].text
while True:
  cookies = "mycookies"
  test = requests.get('https://altenens.org/forums/accounts-and-database-dumps.45/', cookies=cookies)
	test = bs(test.text, "html.parser")
	data1 = test.find_all(class_="structItem-title")
	for i in range(6, len(data1)):
		if "threads" in data1[i].a['href'].replace("unread", ""):
			r = requests.get('https://altenens.org' + data1[i].a['href'].replace("unread", ""), cookies=cookies)
			r = bs(r.text, "html.parser")
			try:
				data = r.find_all(class_="bbWrapper")[0].text
				data = data.split(" ")
				for j in range(0, len(data)):
					if len(data[j]) == 3:
						if re.match(r'^([\s\d]+)$', data[j]):
							cv = data[j]
					if "|" in data[j]:
						for b in range(0, len(data[j].split("|"))):
							if len(data[j].split("|")[b]) == 2:
								if re.match(r'^([\s\d]+)$', data[j].split("|")[b]):
									try:
										if len(data[j].split("|")[b + 1]) == 4:
											if re.match(r'^([\s\d]+)$', data[j].split("|")[b+1]):
												ced = data[j].split("|")[b] + " " + data[j].split("|")[b+1]
										else: 
											if len(data[j].split("|")[b + 1]) == 2:
												if re.match(r'^([\s\d]+)$', data[j].split("|")[b+1]):
													ced = data[j].split("|")[b] + " 20" + data[j].split("|")[b+1]
									except IndexError as e:
										pass
						for q in data[j].split("|"):
							if len(q) == 3:
								if re.match(r'^([\s\d]+)$', q):
									#print("CVV:", q)
									cv = q
							if "@" not in q:
								ch.append(q)
							else:
								ce = q
					if len(data[j]) == 16:
						if re.match(r'^([\s\d]+)$', data[j]):
							#print("Card:", data[j])
							cn = data[j]
							#print("CardType:", getCardType(data[j]))
							ct = getCardType(data[j])
					if "|" in data[j]:
						if len(data[j]) > 16:
							if len(data[j].split("|")[0]) == 16:
								#print("Card:", data[j].split("|")[0])
								cn = data[j].split("|")[0]
								#print("CardType:", getCardType(data[j].split("/")[0]))
								ct = getCardType(data[j].split("|")[0])
					if "/" in data[j]:
						if len(data[j]) > 16:
							if len(data[j].split("/")[0]) == 16:
								#print("Card:", data[j].split("/")[0])
								cn = data[j].split("/")[0]
								#print("CardType:", getCardType(data[j].split("/")[0]))
								ct = getCardType(data[j].split("/")[0])
					if len(data[j]) == 5:
						if "/" in data[j]:
							ced = data[j].split("/")[0], "20" + data[j].split("/")[1]
				if cv != 0:
					if ced != 0:
						print "-------USING CARD-------"
						print "Card Number:", str(cn)
						print "Card CVV:", str(cv)
						print "Card Type:", str(ct)
						if ce != 0:
							print "Card Email:", str(ce)
						print "Card EXP:", str(ced[0]) + " " + str(ced[1])
						print "-------USING CARD-------"
						if cn not in alreadycn:
							alreadycn.append(cn)
						else:
							#print(alreadycn)
							continue
			except IndexError as e:
				pass
		i += 1
```

**CardKiller Function** is not posted as it is uses my own private api
**Description: Its Simple, Effective Tool to get easy money**
