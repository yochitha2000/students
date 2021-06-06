const port = 9000
const express = require('express')
const { usersData } = require('./users')
const app = express()
const bodyParser = require('body-parser')
app.use(bodyParser.json())

app.get('/), (req, res) => { res.send('Default Path') })

// Api Url: http://localhost:9000/rollnumbers
app.post('/rollnumbers), (req, res, next) => {	// Node.js Api Call
usersData(req, res, next)
})


app.listen(port, () => { console.log(`Server running at: ${port}`) })