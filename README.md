
Written by
http://http://blog.garthdb.com/using-the-latest-stable-version-v0-6-10-of-nodejs-on-heroku/
Using the Latest Stable Version (v0.6.10) of NodeJS on Heroku
By GARTHDB | Published: 21 FEB 2012
Update: you can also use nodejs-versions in the labs plugin.

If you’re starting some NodeJS fun on Heroku, you might find that it is not using the latest stable version (as of today is v0.6.10).  To help fix this problem Heroku has provided the means to build your own buildpacks with the Cedar Stack.  This article has one of the better tutorials, but it requires you to use aws; which just seemed silly for something as standard using the latest stable version.

I was in the process of building my own buildpack, when I found Heroku has already provided the stable versions of Node and NPM.

To use these:

Fork Heroku’s NodeJS buildpack
Clone your new repository locally
$ git clone https://github.com/[your github username]/heroku-buildpack-nodejs.git

Edit the bin/compile
$ cd heroku-buildpack-nodejs

Open some text editor >  bin/compile 
Replace this:
# config
NODE_VERSION="0.4.7"
NPM_VERSION="1.0.94"
SCONS_VERSION="1.2.0"
S3_BUCKET="heroku-buildpack-nodejs"

with this:
# config
NODE_VERSION="0.6.10"
NPM_VERSION="1.1.1"
SCONS_VERSION="1.2.0"
S3_BUCKET="heroku-buildpack-nodejs"

Commit and push changes
$ git commit -am 'updated bin/compile with latest stable versions of NPM and Node'
$ git push origin master

Create a new Heroku application
$ heroku create --stack cedar --buildpack http://github.com/[your github username]/heroku-buildpack-nodejs.git

I haven’t found any documentation on how to change the buildpack url setting in an existing application, so I’m going to assume it isn’t possible.  If anyone knows otherwise, feel free to let me know.

