# Welcome to Betflix-Server 👋 
This project is the backend of Betflix.

## Get Started
From the project's root folder:
1. Install dependencies

   ```bash
   npm install
   ```

2. Create .env
  ```bash
  # Local
  SERVER_PORT = 12345 
  DB_PATH = /path/to/file.db
  MOVIES_PATH = /path/to/movies-folder
  SHOWS_PATH = /path/to/shows-folder

  # TMDb
  TMDB_API_KEY = your_key
  TMDB_READ_TOKEN = your_token
  ```

3. Start the app

   ```bash
    npm start
   ```

## Web App
A build of a ReactJS app is in the "view" folder. This can be accessed at the server's "/webapp" endpoint. 

## Mobile App
For a mobile client, an Android APK can be downloaded from the [Betflix website](https://www.lucatozzini.com/prj/betflix/). The source code for this app is from [Betflix-Expo](https://github.com/LucaTozzini/Betflix-Expo)

## REST API
| Endpoint | Method | Query | Returns | Description |
| --- | --- | --- | --- | --- |
| /media/	| GET |	offset, limit, desc, order (added, year, title, duration, random), type (movie, show, any) |	mediaObj[] | Get a media collection |
| /media/<media_id>|	GET	| |	mediaObj	|Get a media singleton|
| /media/<media_id>/seasons	| GET	| |	seasonObj[] |	Get the seasons collection |
| /media/<media_id>/seasons/<season_num>|	GET	| |	episodeObj[] |	Get a season |
| /media/<media_id>/seasons/s<season_num>-e<episode_num> | GET | |	episodeObj | Get episode |
| /external/popular-movies|	GET	| |	tmdbMovieObj[] | Get popular movies from TMDb|
| /external/movies	| GET |	query, year|	tmdbMovieObj[]|	Search movies from TMDb|
| /external/movies/<tmdb_id> | GET  | | tmdbMovieObj |	Get details of movie from TMDb|
| /external/shows	| GET |	query, year	| tmdbShowObj[] |	Search shows from TMDb|
| /external/shows/<tmdb_id> |	GET	|	 | tmdbShowObj | Get details of show from TMDb|
| /external/show/<tmdb_id>/seasons/<season_num> |	GET | | | Get details of season from TMDb|
| /stream/<media_id> | GET | | | Stream movie |
| /stream/<media_id>/s<season_num>-e<episode_num> |	GET	|	| | Stream episode |
| /torrents |	POST|	fileURL| torrentObj[]	|download .torrent file |
| /torrents	| GET |	imdbId | yifiTorrentObj[] |	Get torrents of movie from Yifi |
| /link |	POST | mediaId, tmdbId | | Link local to external|
| /link	| DELETE | mediaId |		| Delete a link |
| /link	|GET |	mediaId XOR (tmdbId and type) |	linkObj |	Get link data for local media|
| /search |	GET	| |	mediaObj[] |	Get media with matching title |
| /external/movies/<tmdb_id>/images |	GET	| language	| | |
| /external/shows/<tmdb_id>/images	| GET |	language	|	| |