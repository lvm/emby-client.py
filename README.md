# emby-client.py

This exists to scratch an itch. It wasn't written to be an actual client but to:

* Be able to export to a .csv my movies
* Be able to update movies from the command line

## Usage

Note: To use this you'll need an [API key](https://github.com/MediaBrowser/Emby/wiki/Api-Key-Authentication). 

```
usage: emby-client [-h] -a API -s SERVER [--export EXPORT] [--update]
                   [--find FIND] [--dupes] [--missing-imdb] [--id ID]
                   [--json JSON] [--path] [--header]

optional arguments:
  -h, --help            show this help message and exit
  -a API, --api API     Emby API Key
  -s SERVER, --server SERVER
                        Emby Host
  --export EXPORT       Export CSV
  --update              Will update an [--id] object using [--json] file.
  --find FIND           Find this value
  --dupes               Print duplicates and suggest a movie to remove.
  --missing-imdb        Print movies with missing IMDB id.
  --id ID               Update this ID
  --json JSON           Path of the JSON file Or JSON string
  --path                Save file path in the CSV.
  --header              Save CSV Header.
``` 

### Export
```
$ emby-client -a ${EMBY_API} -s 1.2.3.4:8096 --export movies-$(date --iso).csv
```

Also export the full path of the movie
```
$ emby-client -a ${EMBY_API} -s 1.2.3.4:8096 --export movies-$(date --iso).csv --path
```

And the header
```
$ emby-client -a ${EMBY_API} -s 1.2.3.4:8096 --export movies-$(date --iso).csv --path --header
```

### Update

JSON as a string
```
$ emby-client -a ${EMBY_API} -s 1.2.3.4:8096 --update --id 96528 --json '{"ProviderIds": {"Imdb":"tt0113074"}}'
```

JSON as a file
```
$ emby-client -a ${EMBY_API} -s 1.2.3.4:8096 --update --id 96528 --json /tmp/movie-data.json
```

### Movies missing its IMDB id

```
$ emby-client -a ${EMBY_API} -s 1.2.3.4:8096 --missing-imdb
```

### Find movies matching a certain value (wildcard)

```
$ emby-client -a ${EMBY_API} -s 1.2.3.4:8096 --find blood
```
 
## License

License: BSD 3-Clause
