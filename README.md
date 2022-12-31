# Youtube-Clone-with-fetching-real-time-data-from-orginal-YouTube
a youtube clone using HTML, CSS and JS only. No other library. We'll also use youtube API to fetch real data from youtube.

- Our clone has a lot of features. like, It's look like youtube. All the video data is coming from youtube directly. We have working search bar also which redirects user to official youtube search page. And whenever user click on video card, he/she will be redirect to youtube's official video page.
-  we have 3 files index.html, style.css and app.js. check them out by clicking above links.
-  After completing styling follow the below steps for YouTube API key.
# steps for YouTube API:-
- Search Google cloud in chrome.
- Create a new project by a name: youtube-clone and tap bars on the  top left.
- Select API and Services then click Library.
-  Scroll down and select YouTube Data API v3 and tap enable.
-  Go in Credentials and create new credentials of API key.
-  Copy that key and once you got your API key. Store that in a variable in your app.js file.
-  For fetching Videos. We need youtube api route. You can find that in youtube documentation.
-  FOllow the code from app.js file.

Explanation:-
 fetch method fetch() to fetch data from youtube.
fetch(video_http + new URLSearchParams({
}))
- You can see we are fetching data from the "video_http" that we got from youtube documentation. And to add parameters to the URL we are using new URLSearchParama(object). Pass the parameters that are mentioned in the code. They all are self explanatory. part param define what art of data we want in this case we want all video related data. So, pass snippet.

After fetching the data we are converting it to JSON by res.json(). You can see youtube data structure.

- All the data we want is in item's array. So after getting JSON data from res.json() loop through the data.items using forEach() method and pass that item into a function called getChannelIcon(item).
- What this function is for. Well, if you see youtube video's data. It contain everything but not channel icon. And we want channel icon too. So we have to fetch icons separately. Using "channel_http"
- And store this HTTP in our app.js file. Below our video_http variable.

-And again add "?" at last of the link.
And, Now make that getChannelIcon function.


Inside this function, we are getting individual video's data because we called this is a loop, remember? And after getting individual video's data we are making request to youtube api for channel information. Again use URLSearchParam to add parameters. Pass video_data.snippet.channelId inside id param. After getting response convert it into JSON by calling res.json() and after converting data into JSON. Set video_data.channelThumbnail to data.items[0].snippet.thumbnails.default.url.

By this we have successfully added channel icon URL to our actual video's data.

After this we are calling another function makeVideoCard(data). This function is to create card.

Now, create Video card. But before creating this function select our Video Container element from HTML.



Inside this functions, as we have to attach card inside video container element use innerHTML method to add HTML code inside videoContainer element. Remember to use += instead of = because we want to add HTML not rewrite the HTML.

And what we add, well we already have our HTML card structure. Copy that code and paste it here. But use template string here. So, it will be easy to add variables with text.

And after pasting HTML structure, remove the actual image sources and titles, channel name instead use ${variable} this to add variable.

And the last thing inside video element use onclick="location.href = 'https://youtube.com/watch?v=${data.id}'" to add click event.

Our video card are done.
