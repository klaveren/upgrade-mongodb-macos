# How to Upgrade MongoDB 4.4 to 5.0 On Mac OS Monterey
This is a Simple Way, step by step how to upgrade MongoDB 4.4 to MongoDB 5.0 on MacOS.

The referenced docs: 
👉 https://docs.mongodb.com/manual/release-notes/5.0-upgrade-standalone/#std-label-5.0-upgrade-standalone

## Check Compatibility Version

```
db.adminCommand( { getParameter: 1, featureCompatibilityVersion: 1 } )
```

The operation should return a result that includes:\
_"featureCompatibilityVersion" : { "version" : "4.4" }._

To set or update featureCompatibilityVersion, run the following command:

```
db.adminCommand( { setFeatureCompatibilityVersion: "4.4" } )
```

## Stop MongoDB 4.4 Services

```
brew services stop mongodb/brew/mongodb-community@4.4
```

## Create Database Backup

```
mkdir ~/backupdb
cp -av /usr/local/var/mongodb ./backupdb
```

## Download MongoDB 5.0 Binaries

https://fastdl.mongodb.org/osx/mongodb-macos-x86_64-5.0.5.tgz
- Extract files...

## Replace MongoDB 4.4 Binaries with MongoDB 5.0 Binaries

```
mv /usr/local/opt/mongodb-community@4.4/bin /usr/local/opt/mongodb-community@4.4/bin-org
mkdir /usr/local/opt/mongodb-community@4.4/bin
cp -av ~/Downloads/mongodb-macos-x86_64-5.0.5/bin /usr/local/opt/mongodb-community@4.4/bin
```

## Start MongoDB Services

```
brew services start mongodb/brew/mongodb-community@4.4
```

## Enable MongoDB 5.0 Compatibility Features

```
db.adminCommand( { setFeatureCompatibilityVersion: "5.0" } ) 
```

## Install MongoDB 5.0

```
brew services stop mongodb/brew/mongodb-community@4.4
brew install mongodb-community
```

## Uninstall MongoDB 4.4

```brew uninstall mongodb/brew/mongodb-community@4.4```


be happy 🤙






