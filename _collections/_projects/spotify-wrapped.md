---
layout: post
title: "Project: Spotify Wrapped"
description: Project is a mimic of Spotify's famous yearly wrapped.
technologies: [Python]
---

## What is the project ?
This project is a mimic of Spotify's famous yearly wrapped that showcases what songs, artist, generes, podcast, etc. you have intereacted with the most for that year. Now my version is definitely not that advanced yet and is set up to only return the users top songs. With that being said the project uses Spotify's API to gain access to ones data, that data is then deployed into Google Spread Sheets using it's API, and ultimately you can either leave it as it is on the spread sheet or import the data into a web app called [Glide](https://www.glideapps.com/).

<img src="assets/images/glide.PNG"
  alt="picture of spotify wrapped" 
/>

This project is a fun little experiment to gain more experiance working with API's&mdash;what they are and how they work&mdash;. It's the main reasonce why I started the project myself, to learn. There are plenty of different API's you might want to look at since most apps you use probably already use them. I went with Spotify because I like music and I use Spotify everyday, but here are other options:

* [YouTube](https://developers.google.com/youtube/v3)
* [Twitter](https://developer.twitter.com/en/docs/twitter-api)
* [Facebook](https://developers.facebook.com/docs/)


## How Did I Build the Project?
Project is build with:

{% for technology in page.technologies %}
- {{ technology }}
{% endfor %}

Here are some other things involved in the code and worth giving a look at to further understand the code:
* [Spotify's API](https://developer.spotify.com/documentation/web-api/reference/get-an-artist)
* [Google SpreadSheets](https://developers.google.com/sheets/api/quickstart/python)

Some of the libraries I used:
* [spotipy](https://spotipy.readthedocs.io/en/2.22.1/) - this is a lightweight python library for the Spotify web API
* [pandas](https://pypi.org/project/pandas/) - used for manipulating data
* [time](https://docs.python.org/3/library/time.html)
* [datetime](https://docs.python.org/3/library/datetime.html#module-datetime)
* [gspread](https://docs.gspread.org/en/v5.7.1/) - Used to open and store data


Something cool I did:

```python

## Authorization ##
SPOTIPY_CLIENT_ID='YOUR OWN'
SPOTIFY_CLIENT_SECRET='YOUR OWN'
SPOTIFY_REDIRECT_URL='http://127.0.0.1:9090'
SCOPE = "user-top-read"

# spotipy object to access info #
sp = spotipy.Spotify(auth_manager=SpotifyOAuth(client_id=SPOTIPY_CLIENT_ID,
                                               client_secret=SPOTIPY_CLIENT_SECRET,
                                               redirect_uri=SPOTIPY_REDIRECT_URI,
                                               scope=SCOPE))

## lets you know if you have any errors
print(sp.status_code)

## get top tracks ##
## try to format the dic output so its easier to read ##
top_tracks = sp.current_user_top_tracks(limit=20, offset=0, time_range="short_term")
print(top_tracks.json())

```
## Some of the challenges
While it was very fun to do this project it didnt come easy, I had a lot of problems trying to get it to work. Most of my issues where coming from the Authantication part. It is arguably the hardest part of API's and definitely gave me a lot of headaches in terms of the authorization formatting, but after looking around on the internet for some help I got it down and solved my errors. The next problem I incountered was that while I was coding I kept mixing up dictionaries with lists and this was one of the main reasons why my code wouldnt work. So when I relized what I've done it was a simple fix of changing the lists to dictionaries. Other than those issues I ran into I found that the documentation on both Spotify API and spotipy was really helpfull in making me understand how I can reach my end goal.

Overall I learned a lot about API's and became more familiar with a specific one. Now I have my very own Spotify wrapped that tells me what songs I've kepted on reapt lately. This is still a work in progress because I would like it to do more and be able to have access to other accounts, but I still think that what I did is pretty neat. 

