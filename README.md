# How to upgrade MongoDB 4.4 to 5.0 On Mac OS Monterey
Step by step to upgrade simple way MongoDB 4.4 to 5.0 on MacOS.

The referenced docs: 
👉 https://docs.mongodb.com/manual/release-notes/5.0-upgrade-standalone/#std-label-5.0-upgrade-standalone

## Check Compatibility Version

```db.adminCommand( { getParameter: 1, featureCompatibilityVersion: 1 } )```

- The operation should return a result that includes "featureCompatibilityVersion" : { "version" : "4.4" }.

To set or update featureCompatibilityVersion, run the following command:

```db.adminCommand( { setFeatureCompatibilityVersion: "4.4" } )```

## stop mongodb services

```brew services stop mongodb/brew/mongodb-community@4.4```

## Create database backup

```mkdir ~/backupdb```
```cp -av /usr/local/var/mongodb ./backupdb```

## Download mongodb binaries

https://fastdl.mongodb.org/osx/mongodb-macos-x86_64-5.0.5.tgz
- Extract files...

## Replace mongodb binaries

```mv /usr/local/opt/mongodb-community@4.4/bin /usr/local/opt/mongodb-community@4.4/bin-org```
```mkdir /usr/local/opt/mongodb-community@4.4/bin```
```cp -av ~/Downloads/mongodb-macos-x86_64-5.0.5/bin /usr/local/opt/mongodb-community@4.4/bin```

## Restart mongodb services

```brew services start mongodb/brew/mongodb-community@4.4```

## Enable mongodb 5.0 features

```db.adminCommand( { setFeatureCompatibilityVersion: "5.0" } ) ```

## Install mongodb5

```brew services stop mongodb/brew/mongodb-community@4.4 ```
```brew install mongodb-community```

## Uninstall Mongodb 4.4

```brew uninstall mongodb/brew/mongodb-community@4.4```


be happy 🤙






