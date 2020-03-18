# Wget

GNU Wget is a free software package for retrieving files using HTTP, HTTPS and FTP. It is a non-interactive commandline tool that can be called from scripts, cron jobs, terminals, etc. The tool is useful for downloading all images or PDFs from a web page.

The terminal command below demonstrates downloading all jpg and png images from the Ray Wenderlich home page and saving into a folder named "ray".

```bash
# Download all jpg and png images from Ray Wenderlich website
# -nd saves all files to current folder without creating subfolders
# -r turn on recursive retrieving
# -P declare directory to save the files
# -A accept files of a certain type
wget -nd -r -P ./ray -A jpg,png http://www.raywenderlich.com
```

The next command will download all PDFs on a web page and place them into a folder named "docs".

```bash
wget -nd -r -P ./docs -A pdf http://www.website.com
```

Further reading about the wget tool is availabe at [GNU Wget](https://www.gnu.org/software/wget/) and [Install and configure](http://coolestguidesontheplanet.com/install-and-configure-wget-on-os-x/).
