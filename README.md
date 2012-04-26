
See

http://blog.garthdb.com/using-the-latest-stable-version-v0-6-10-of-nodejs-on-heroku/

Using the Latest Stable Version (v0.6.10) of NodeJS on Heroku

By GARTHDB | Published: 21 FEB 2012


This git modified to

--------

package_download "nodejs" "0.6.15" $bootstrap_node
 
engine_defaults["node"]="0.6.15"

engine_defaults["npm"]="1.1.1"

--------


$ heroku config:add BUILDPACK_URL="git://github.com/kenokabe/heroku-buildpack-nodejs.git"

to the existing app