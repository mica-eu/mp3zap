# mp3zap
Search and download music from mp3zap.

## Installation

    $ npm install mp3zap

## Example
```javascript
var http = require('http'),
    fs = require('fs'),
    mp3zap =  require('mp3zap');

mp3zap("The Beatles Something", function (err, tracks) {
  if (err) throw err;

  var file = fs.createWriteStream(tracks[0].name + '.mp3');
  http.get(tracks[0].direct, function (res) {
    res.pipe(file);
  });
});
```

## API
### track
```javascript
{
    name: String, // the track name
    artist: String, // the artist name
    duration: Number?, // the duration of the track in seconds
    direct: String, // the direct MP3 url to the track
}
```

### mp3zap(terms, done)
Search MP3 tracks on mp3zap.

`terms` is expected to be a string of terms to search for.

`done` returns an array of `tracks`.

## License
MIT
