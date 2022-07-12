# Hi there, I'm Eren - [Hosting Türkiye][website] <img width="30px" src="https://media.tenor.com/images/3b388fe03da271d2674faf85eb7c3fcd/tenor.gif" />

<img align="right" alt="GIF" height="160px" src="https://media.giphy.com/media/du3J3cXyzhj75IOgvA/giphy.gif" />

## I'm an computer and cyber security student

- 👨‍💻 I’m currently working on web development technologies like JavaScrpit, PHP etc.
- 📚 I’m currently learning everything about engineering software tools like MATLAB, AutoCAD. 
- 💪🏼 Future Goals: Learn more technologies - Never stop creating new ideas.


---



### Contact with me 📝

[<img align="left" alt="hostingturkiye.com.tr" height="30px" src="https://cdn-icons-png.flaticon.com/512/1150/1150626.png" />][website]3
[<img align="left" alt="SpaceEA | Discord" height="30px" src="https://image.flaticon.com/icons/png/512/356/356060.png"/>][discord]
[<img align="left" alt="SpaceEA | Spotify" height="30px" src="https://cdn-icons-png.flaticon.com/512/408/408697.png" />][Spotify]

<br />

---

### Languages and Tools 🛠 

![C](http://img.shields.io/badge/-C-A8B9CC?style=flat-square&logo=c&logoColor=ffffff)
![Python](http://img.shields.io/badge/-Python-3776AB?style=flat-square&logo=python&logoColor=ffffff)
![JavaScript](https://img.shields.io/badge/-JavaScript-%23F7DF1C?style=flat-square&logo=javascript&logoColor=000000&labelColor=%23F7DF1C&color=%23FFCE5A)
![HTML5](https://img.shields.io/badge/-HTML5-%23E44D27?style=flat-square&logo=html5&logoColor=ffffff)
![CSS3](https://img.shields.io/badge/-CSS3-%231572B6?style=flat-square&logo=css3)
![Nodejs](https://img.shields.io/badge/-Nodejs-339933?style=flat-square&logo=Node.js&logoColor=ffffff)
![Firebase](https://img.shields.io/badge/-Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=ffffff)
![Git](https://img.shields.io/badge/-Git-%23F05032?style=flat-square&logo=git&logoColor=%23ffffff)
![GitHub](https://img.shields.io/badge/-GitHub-181717?style=flat-square&logo=github)
![VS Code](http://img.shields.io/badge/-VS%20Code-007ACC?style=flat-square&logo=visual-studio-code&logoColor=ffffff)
![Powershell](http://img.shields.io/badge/-Powershell-5391FE?style=flat-square&logo=powershell&logoColor=ffffff)
![Windows](http://img.shields.io/badge/-Windows-0078D6?style=flat-square&logo=windows&logoColor=ffffff)

[website]: https://hostingturkiye.com.tr/
[discord]: https://discord.gg/aNRTCTHSrz
[Spotify]: https://open.spotify.com/user/h08wi83hv74a9coty964dlqw4



require "hallon"

# Get an application key from Spotify (the binary kind), from [here](https://developer.spotify.com/en/libspotify/application-key/)
# The binary kind.
session = Hallon::Session.initialize(IO.read("a0cc8734ed884a1b9f7576a917b3b8d0"))

# User you login credentials
session.login!("junkiesxl", "not really my password so please don't even try")

# Enter the URI of the playlist you want to add songs to
playlist = Hallon::Playlist.new("spotify:user:junkiesxl:playlist:2YF0zXj84fJvyBOCwEZtDf").load

# Takes a artist name (string), and a `Hallon::Playlist` will try to
# add the top songs of the artists to the playlist.
def add_top_hits_of_artist(artist_name, playlist)
  results = Hallon::Search.new(artist_name).load
  artist = results.artists.first
  if (!artist)
    puts "Nothing found with #{artist_name}, did you mean #{results.did_you_mean}"
    return
  end

  puts "Found #{artist.name}"

  tracks = artist.browse.load.top_hits[0..15]
  puts "  - has #{tracks.size} top hits"

  playlist.insert(playlist.size, tracks).upload
  puts "  - added to the playlist"
end

thursday.each do |artist_name|
  add_top_hits_of_artist(artist_name, playlist)
end




----
