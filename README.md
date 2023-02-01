README file for Lab2
Lab2: Building a web app using OPENWeather APi and a free API of our choosing. We are tasked of using OpenWeather API and another API to make a weather app that could be used to access the weather data
at any given time. The goal of this lab was to determine and check our skills in using AJAX and JSON with the help of API.

The part where I struggled the most was the API on its own. Using API's of any kind is a new approach that I had never worked withy before but it was a nice touch of innovation. Finding an APi that 
did what I wanted it to do and that it synced will with my other api was pretty challenging but it all worked out. 
Something creative I added was that I added the sunrise time and sunset time of each city. I added this using the api because it was cool that I could see the different times in which different country
called sunset and sunrise due to the shape of the Earth.

I decided to work on the extra credit part of the lab which required us to use geolocate to use the location of the user to find the weather instead of hardcoding a specific location i.e Troy NY.

We will use name of city to find weather forecast by function getMeteoByCity() in app.js file

We will use coordinates of city to find weather forecast by function getMeteoByCoordinates() in app.js file

we have to use color changing algorithm which is already pre-defined , source is already given in utility.js file.

While making the web app I got stuck while writing the javascript of the getMeteoByCoordinates this took a log time to get right because it just didn't work properly. I finally got it to work aftyer I discovered
a tutorial that explained how to do this.


REFERENCE.
"https://www.w3schools.com/html/html5_geolocation.asp"
https://javascript.plainenglish.io/how-to-build-a-weather-web-app-using-vanilla-javascript-5518dbb92c52
https://www.geeksforgeeks.org/make-a-web-based-weather-report-of-your-location-using-openweathermap-api/
https://www.youtube.com/watch?v=WZNG8UomjSI




API Documentation/ Research
1. OpenWeather API
2. TwitchAPI
3. PSN API
4. IBM Cloud ApI


OpenWeather API
The openWeather API documentation on how it stores and organizes its data is pretty simple and straightforward. The data is stored using the geographic location of the city it's trying to find or cache the weather for. The Json file includes the longitude and latitude of the city to differentiate it. The Json file also includes the basic info like the id of the city, as well as the condition of the weather currently affecting the location. Be it rain, hail, sunny or anything else. This information is one of the most important and the first thing that the json files produces and stores because it's the first thing users want to see when they call the api or whenever they decide to check for the location of a particular place. The data in the Json file is divided into sub point based on the weather information. For example after defining the temp data, the Json also includes information like "temp feels like". This information is derivative of the current temperature and iot can be seen as optional or more data to circumvent the current data. One thing I like about the organization of the data is that it's very easy to read. It's convenient and it;s straight forward

{
  "coord": {
    "lon": 10.99,
    "lat": 44.34
  },
  "weather": [
    {
      "id": 501,
      "main": "Rain",
      "description": "moderate rain",
      "icon": "10d"
    }
  ],
  "base": "stations",
  "main": {
    "temp": 298.48,
    "feels_like": 298.74,
    "temp_min": 297.56,
    "temp_max": 300.05,
    "pressure": 1015,
    "humidity": 64,
    "sea_level": 1015,
    "grnd_level": 933
  },

While looking at the other data the weather api provided I discovered that the api could be used to calculate the sea level of an area. It could calculate the min and max sea level. The geo locator call is another great function of the api, it's able to be used to search a location based on the current location of where its been called or any location in the world. It asks for permission to use  and access the users location and it gives the info out.Geocoder API can automatically convert city names and zip-codes to geo coordinates and the other way around.


2. Twitch Api
The twitch api is divided into multiple parts or components:
Starting a Poll
Starting a Prediction
Starting a Raid
Creating Stream Clips
Creating Stream Markers
Getting Videos
Scheduling Broadcasts
Moderating a Broadcaster’s Chat
Getting a Creator’s Goals
Getting an Extension Analytics Report
Getting a Game Analytics Report
however, I decided to focus on the  starting a poll api because i felt it's something we could implement into our own api when we created it. The twitch api is pretty basic and easy to use especially the one for starting a poll. In order for a poll to be created, the streamer of a member of the community can start a poll and this done by creating a Post request to create a poll endpoint on the server side. Only users with access to the token are allowed to create polls thereby nullifying excess polls and unnecessary ones.

curl -X POST 'https://api.twitch.tv/helix/polls' \
-H 'Authorization: Bearer vpx9etxs8bbii29krls1ljai1kdr' \
-H 'Client-Id: dt4z41sa8uexdkjvt7uu9jjqm575' \
-H 'Content-Type: application/json' \
-d '{"broadcaster_id":"123456","title":"Streaming next Tuesday. Which time works best for you?","choices":[{"title":"9AM"},{"title":"10AM"},{"title":"7PM"},{"title":"8PM"},{"title":"9PM"}],"duration":300}'

Here is an example of a call, here the streamer creates a poll asking her current viewers what time the next stream will take place. The poll should runs for 5 minutes. The data in this json is organized entirely differently from that of the openweathermap api, here the call is directed at and for a specific users need, unlike the api for open weathermap its pretty general.

{
  "data": [
    {
      "id": "84c8d008-5f57-4583-b7fa-b824e15b0655",
      "broadcaster_id": "123456",
      "broadcaster_name": "smartysmartmaster",
      "broadcaster_login": "smartysmartmaster",
      "title": "Streaming next Tuesday. Which time works best for you?",
      "choices": [
        {
          "id": "0214c236-f36d-49ca-a019-0f78329aaa60",
          "title": "9AM",
          "votes": 0,
          "channel_points_votes": 0,
          "bits_votes": 0
        },
        {
          "id": "975c4906-278d-468c-9706-4e33a7a35adc",
          "title": "10AM",
          "votes": 0,
          "channel_points_votes": 0,
          "bits_votes": 0
        },

        One thing I noticed between twitch's api and openweather's api is the way they are built and structured. Twitch is meant to be an interactive and flexible platform used daily by different users making it's adaptability range huge. The API gives the streamer or developer a lot of features that are useful and allow for flexibility, for example the poll api can be merged into another poll, merged from a poll from multiple streams it also allows users to keep track of their selection.
        This is done by twitch's currency called channel points. Whenever a user views a streamer for a period of time, they get points which can be used for a multitude of things, use channel emotes or gifs, cool banner to their names and a bunch of other things. This points are specific to every stream so OI can have 200 points for streamer B and 1000 for streamer F which shows them how much time is spent in a particular channel. This points allow users to participate in multiple polls, so if I want to be able to influence a p;articular decision the more time I have spent in that channel over time the more points I have potentially gained and the more influenceI have.

curl -X POST 'https://api.twitch.tv/helix/polls' \
-H 'Authorization: Bearer vpx9etxs8bbii29krls1ljai1kdr' \
-H 'Client-Id: dt4z41sa8uexdkjvt7uu9jjqm575' \
-H 'Content-Type: application/json' \
-d '{"broadcaster_id":"123456","title":"Streaming next Tuesday. Which time works best for you?","choices":[{"title":"9AM"},{"title":"10AM"},{"title":"7PM"},{"title":"8PM"},{"title":"9PM"}],"duration":300,"channel_points_voting_enabled":true,"channel_points_per_vote":200}'

This post request here shows the user spending 200 channel points per votevote 




3. PSN API
What is ethe PSN ApI? The Psn api is an api that is used to acess all the virtual and digital troipies users get when playing games on the playstation platform. The Playstation platform keeps a tally and record of thiis but it isn't as detailed an organized as that of https://psnprofiles.com/RuptureDreams

This is a website tat is used by most playstation gamers to keep track of all their trophies 

Unblike otehr api that is called, the PSN api installed as a package using npm. 
npm install psn-api
The Psn api is restricted and locked through authorization cookies and a Json response file. The function call to acess the api is
 function calls from this package.
// This is the value you copied from the previous step.
const myNpsso = "<64 character token>";

// We'll exchange your NPSSO for a special access code.
const accessCode = await exchangeNpssoForCode(npsso);

// 🚀 We can use the access code to get your access token and refresh token.
const authorization = await exchangeCodeForAccessToken(accessCode);
The user is given access to log into the psn api 


A call to access every game trophy earned 

// This returns a list of all the games you've earned trophies for.
const trophyTitlesResponse = await getUserTitles(
  { accessToken: authorization.accessToken },
  "me"
);

The calls can also be specified for a particular console generation like the PS3, Vita or Ps5. The title platfrom can be specified using  npServiceName and the parameter as a;ways is trophy



here's an example of a call for a Ps3 to get all the trophies a user has gained

import { getTitleTrophies } from "psn-api";

// "NPWR00867_00" is the title ID for Red Dead Redemption.
const response = await getTitleTrophies(authorization, "NPWR00867_00", "all", {
  npServiceName: "trophy"
});


Here is the call for the Ps5

import { getTitleTrophies } from "psn-api";

// "NPWR20188_00" is the title ID for Astro's Playroom.
const response = await getTitleTrophies(authorization, "NPWR20188_00", "all");

Here the call doesn't specify the need for a paraameter like trophy

Returns

The call returns the trophy veresion, its groups, the individual object for each trophy, total item countauthorization	AuthorizationPayload	

The unique ID of the game title you wish to retrieve the trophy list for.
trophyGroupId	string	"all" to return all trophies for the title, otherwise restrict results to a specific trophy group (such as a DLC).
options	GetTitleTrophiesOptions	Most often used to specify an npServiceName if you're retrieving entites belonging to a non-PS5 title. Can also be used for pagination or localization options (see Options section below).
Options​
These are the possible values that can be in the options object (the fourth parameter of the function that uses the GetTitleTrophiesOptions type).

Name	Type	Description
npServiceName	"trophy" | "trophy2"	"trophy" is required for titles belonging to the PS3, PS4, or PS Vita platforms. "trophy2" is used for the PS5 platform, but is optional.
limit	number	Limit the number of trophies returned.
offset	number	Return trophy data from this result onwards.
headerOverrides	CallValidHeaders	Override the headers in the request to the PSN API, such as to change the language.
Source​



#4 IBM Cloud Api
IBM Watsoon cloud api 

Focusing on the cloudf Pak for data urls the api can be called using an end[point similar to this 

curl -X {request_method} -H "Authorization: Bearer {token}" "https://{cpd_cluster_host}{:port}/discovery/{deployment_id}/instances/{instance_id}/api"\


For Cloud Pak for Data, we pass a bearer token in an Authorization header to authenticate to the API. The token is associated with a username.
For testing and development, you can use the bearer token that's displayed in the Cloud Pak for Data web client


curl -k -X POST -H "cache-control: no-cache" -H "Content-Type: application/json" -d "{\"username\":\"{username}\",\"password\":\"{password}\"}" "https://{cpd_cluster_host}{:port}/icp4d-api/v1/authorize"