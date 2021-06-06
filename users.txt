let rp = require('request-promise')

module.exports.usersData = async(req, res, next) => {
 if(!req.body || !req.body.rollNumbers) { return res.send('Please send rollnumbers') }
   // "req.body.rollNumbers" has the array of rollNumbers that comes from the front-end
   const rollNumbers = req.body.rollNumbers	// Eg: rollNumbers = [5,6,7,8,9,10,11,12]
   const rollNumbers = []
   for await(let i of rollNumbers) {
     let responseFromProEdge = await getProEdge(i)
     result.push(responseFromProEdge)  
   }
   res.send(result)
}

async function getProEdge(rollNumber) {
  return new Promise((resolve, reject) => {
    let options = {}, response = [];
    options = {
      uri: `${baseApiUrl}` // External Api Base Url
      qs: { rollnumber: rollNumber },
      json: true
    }
    rp(options) // Calling the External Api through "reques-promise" package
      .then((repos) => { // Response from External Api
response = { key: rollNumber, value: repos }
return resolve(response)
})
.catch(err => {
console.log('error is', err)
return reject(err)
})  // If any error from External Api, it will get printed in the logs

})
}