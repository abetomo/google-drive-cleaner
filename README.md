# google-drive-cleaner

[![npm version](https://badge.fury.io/js/%40abetomo%2Fgoogle-drive-cleaner.svg)](https://badge.fury.io/js/%40abetomo%2Fgoogle-drive-cleaner)
![Test](https://github.com/abetomo/google-drive-cleaner/workflows/Test/badge.svg)

A tool to remove files on Google Drive.

## install

```
% npm install @abetomo/google-drive-cleaner
```

## dryrun
### example

* Owner is `GMAIL_ADDRESS`
* File name contains `.xlsx`

```
% google-drive-cleaner \
-a AUTH_JSON_FILE_PATH \
-q "'GMAIL_ADDRESS' in owners and name contains '.xlsx'"
```

Because it is dryrun, the file to be deleted is only displayed.

### query

See [Search query terms and operators](https://developers.google.com/drive/api/guides/ref-search-terms) for queries specified with `-q`.

## delete

Add `--no-dryrun` option.

### example

* Owner is `GMAIL_ADDRESS`
* File name contains `.xlsx`

```
% google-drive-cleaner \
-a AUTH_JSON_FILE_PATH \
-q "'GMAIL_ADDRESS' in owners and name contains '.xlsx'" \
--no-dryrun
```

By adding the `--no-dryrun` option, the files on the drive are deleted.

## Usage example of Node.js API

```javascript
'use strict'

const GoogleDriveCleaner = require('@abetomo/google-drive-cleaner')
const googleDriveCleaner = new GoogleDriveCleaner('AUTH_JSON_FILE_PATH')
googleDriveCleaner.clean({
  query: 'Query string for searching delete files.',
  dryrun: true
})
```

## `AUTH_JSON_FILE_PATH`

Use GCP service account credentials. You first need to create a service account, download its json key.
