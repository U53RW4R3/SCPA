# exifLooter

## 01 - Setup

```
$ go install github.com/aydinnyunus/exifLooter@latest && \
sudo mv ~/go/bin/exifLooter /usr/local/bin/
```

## 02 - Help Menu

```
$ exifLooter -h
ExifLooter finds GeoLocation Metadata and display. You can use with pipe and flags

Usage:
  exifLooter [flags]

Flags:
  -d, --directory string   Specify a directory for Analyzing
  -h, --help               help for exifLooter
  -i, --image string       Specify a image for Analyzing
  -m, --open-street-map    Get Open Street Map Link
  -p, --pipe               Pipe with other scripts
  -r, --remove             Remove metadata from Image
```

## 03 - Usage

Analyze metadata from an image.

```
$ exifLooter -i /path/to/image.jpeg
```

Specify a directory with images to analyze.

```
$ exifLooter -d /path/to/directory/
```

Remove meta data from an image.

```
$ exifLooter -r /path/to/image.jpeg
```

---
## References

- [exifLooter](https://github.com/aydinnyunus/exifLooter)