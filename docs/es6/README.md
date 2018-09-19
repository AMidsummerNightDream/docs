# ES2015

## Promise

``` js
const p = new Promise((resolve, reject) {
  if (ture) {
  	resolve()
  } else {
  	reject()
  }
})

p.then(result => {

}).catch(err => {

})
```

## Fetch

``` js
fetch('https://www.example.com/search/', {
  method: 'POST',
  headers: {
  	Accept: 'application/json',
  	Content-Type: 'application/x-www-form-urlencoded',
  },
  credentials: 'include',
  body: 'data'
})
.then(res => {
  if (res.status >= 200 && res.status <= 300 || res.status == 304) {
  	return res.json()
  } 
})
.then(res => {
  console.log(res)
}).catch(err => {

})
```