# Install packages

```
curl -s --compressed "https://eternalconcert.github.io/ppa/KEY.gpg" | sudo apt-key add -
sudo curl -s --compressed -o /etc/apt/sources.list.d/github_ppa.list "https://eternalconcert.github.io/ppa/files.list"

sudo apt update
```

# Add packages

```
# Packages & Packages.gz
dpkg-scanpackages --multiversion . > Packages
gzip -k -f Packages

# Release, Release.gpg & InRelease
apt-ftparchive release . > Release
gpg --default-key "Christian Kokoska <info@softcreate.de>" -abs -o - Release > Release.gpg
gpg --default-key "Christian Kokoska <info@softcreate.de>" --clearsign -o - Release > InRelease

# Commit & push
git add -A
git commit -m update
git push
```

Source: https://assafmo.github.io/2019/05/02/ppa-repo-hosted-on-github.html
