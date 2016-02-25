# Delete remote tags

```javascript
'use strict'

const _exec = require('child_process').exec

function exec(cmd) {
  return new Promise(function (resolve, reject) {
    console.log('exec:', cmd)
    _exec(cmd, function (err, stdout) {
      if (err) {
        reject(err)
      } else {
        resolve(stdout)
      }
    })
  })
}

exec('git tag -l').then(function (stdout) {
  let tags = stdout.trim().split('\n')
  let ret = Promise.resolve()
  tags.forEach(function (tag) {
    ret = ret.then(function () {
      return exec('git tag -d ' + tag)
    }).then(function () {
      return exec('git push origin :refs/tags/' + tag)
    })
  })
  return ret
})


```
