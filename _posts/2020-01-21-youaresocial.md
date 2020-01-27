---
title: "YouAreSocial"
date: "2020-01-26"
layout: single
tags:
- Automation
- Girls
- AI
- Face Recoginition
categories:
- Projects
---

![YouAreSocial](https://scontent.faly3-2.fna.fbcdn.net/v/t1.15752-9/83316150_595279561254373_5205444180284801024_n.png?_nc_cat=101&_nc_oc=AQn6qilTHSdVNqhbvTr6OtAJaAg5BmNzaxulqZxyNyu3d8eTBCq1UirqQnEEIvBubFQ&_nc_ht=scontent.faly3-2.fna&oh=65e0b2431bf6cd1802afbdb515658546&oe=5E99E957)

# YouAreSocial

Soo You are a **Lucifer** Wannabe, then let me help you i'm the lucifer here ❤️❤️
Lucifer gets girls with his british accent and his Narcissistic personality disorder
thats why he goes to a Therapy Actually, Anyway lets get into the concept and coding

**Concept**:
  So we need to get girls but how ?, You totally need to read my book..here is the answer
  girls love people who is great, famous, rich, working hard for his goal. Basically
  they need someone to help them live in a happy and challengy life, So Can you do that?
  if yes then you need to search for your girl and thats what my robot work on, got it?
  
  
  **YouAreSocial** works on getting all girls with a list of names so firstly you need to
  add any array of the list of girl names you want the more names, the more girls you get
  ```python
  my_bitch = ["name1","name2","name3"]
  ```
  So now we need to get girl accounts to see their profile pictures, but wait some girls
  on facebook adds some baby photo or random pictures and we need the picture of the girl
  we gonna talk to and get her to love us " it determines on the way you talk " so now what.
  Okay Let's use Face Recognition to see if their is a face on her image but you need
  something, your Facebook Profile's Image API, i made my own because it is a lil complicated
  ```python
  import face_recognition
  import requests
   
  def check_faces(facebookprofilelink):
      web = requests.get("yourapi/index.php?profile_link=" + facebookprofilelink)
      file = open("randomimg.png", "w+")
      file.write(web.text)
      file.close()
      image = face_recognition.load_image_file("randomimg.png")
      face_locations = face_recognition.face_locations(image)

      print(f'There are {len(face_locations)} people in this image')
  ```
  Okay you are being a little worried on how to get their facebook profiles by the script
  please don't be a script kiddie just read the concept and make it yourself
  ```python
  def getFacebook(name):
    facebook_url = "https://www.facebook.com/search/people/?q=" + name
    cookies = {} # UR COOKIES HERE
    re = requests.get(facebook_url, cookies=cookies)
    re = re.text
    # I will BeautifulSoup for you, i won't help that much here <3
  ```
  So We got the Facebook Profile and She has a picture for her as her profile picture
  Now we need to see what she likes and how can we get her to us mmm. Facebook About
  ```python
  def getAbout(facebookurl):
    cookies = {} # UR COOKIES HERE, u need an online api python requests sessions sucks
    re = requests.get(facebookurl+"/about", cookies=cookies)
    re = re.text
    # Again, Scrape with yourself <3
  ```
  So is facebook about enough ?, no lets search another sites but how... Google Dorks
  and [Sherlock](https://github.com/sherlock-project/sherlock).. now we know everything
  lets hit her up with what she loves, yes Me of course not You, you creep !.
  
  The Script does the contact thing for ya ( bot chatting is still under development )
  we need some girls to work on the chat, hit me up if you are a girl ;)
  [OmarBadran](https://www.facebook.com/messages/t/OmarMohamedBadran)
