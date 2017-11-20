[![Build
Status](https://travis-ci.org/Rodeoclash/ffmpeg-inline.svg?branch=master)](https://travis-ci.org/Rodeoclash/ffmpeg-inline)

GeneralUI fork of the [ffmpeg-inline](https://travis-ci.org/Rodeoclash/ffmpeg-inline) project.

Wrapper around a pexe based version of ffmpeg

## Build

`npm run build`: builds javascript file in `/dist/ffmpeg-inline.js`

## Usage

```
var file = event.target.files[0] // from <input type="file" /> change event
var inputFiles = [file]
var globalOptions = '-y' // always overwrite files
var convertOptions = '-preset ultrafast -s 320x200'
var outputFiles = ['output.webm']

window.ffmpeg(globalOptions, inputFiles, convertOptions, outputFiles, {
  onProgress: function(progress) {
    console.log('progress', progress)
  }
}).then(function(results) {
  let videoFile = results.files[0]

  // 1. do something with video file (i.e. save it)
  // 2. Cleanup memory when you are done (this is important)
  saveFile(videoFile)
    .then(() => {
      results.cleanupFiles()
    })
})
```

See examples folder for working version.

## Contributing

Run `npm run-script develop` to setup local dev envionment (run examples at:
`http://localhost:8000/example_1.html`)

Run `npm test` to execute test suite.

## Credits

Thanks to http://neo.idletime.tokyo/enu/ffmpeg_pnacl/ for the pexe used in this library.
