---
Fun: Activities
layout: base
permalink: /data/activities
tags: [javascript, fetch, get, post, put]
---

<h1>Breaking Fun!!</h1>
<br/>

<table  style="width:100%" id = "table">
  <thead>
  <tr>
    <th>Item</th>
    <th>Activity</th>
    <th>Address</th>
    <th>Fun</th>
  </tr>
  </thead>
  <tbody id="result">
    <!-- javascript generated data -->
  </tbody>
</table>

<script>

var requestOptions = {
  method: 'GET',
  redirect: 'follow'
};

//fetch("https://finalcptperiod4.duckdns.org/api/activities", requestOptions)
fetch("https://finalcptperiod4.duckdns.org/api/activities", requestOptions)
  .then(response => response.json())
  .then(r => {
    r.forEach(ev => {
      const row = document.createElement("tr")
      const itemData = document.createElement("td")
      itemData.innerHTML = `${ev.id}`
      row.appendChild(itemData)

      const ActivityData = document.createElement("td")
      ActivityData.innerHTML = `${ev.Activity}`
      row.appendChild(ActivityData)

      const AddressData = document.createElement("td")
      AddressData.innerHTML = `${ev.Address}`
      row.appendChild(AddressData)

      const FunData = document.createElement("td")
      FunData.innerHTML = `<a href=${ev.link}> ${ev.Fun} </a>`
      row.appendChild(FunData)

      document.getElementById("table").appendChild(row)
    })
  })
  .catch(error => console.log('error', error))

function reset() {
  window.location.reload();
}
</script>

<script>
const resultContainer = document.getElementById("result");
  // prepare URL's to allow easy switch from deployment and localhost
//const url = "https://finalcptperiod4.duckdns.org/api/activities"
const url = "https://finalcptperiod4.duckdns.org/api/activities"
const create_fetch = url + '/create';
const read_fetch = url + '/';
read_users();

function read_users() {
    // prepare fetch options
    const read_options = {
      method: 'GET', // *GET, POST, PUT, DELETE, etc.
      mode: 'cors', // no-cors, *cors, same-origin
      cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
      credentials: 'omit', // include, *same-origin, omit
      headers: {
        'Content-Type': 'application/json'
      },
    };     // fetch the data from API
    fetch(read_fetch, read_options)
      // response is a RESTful "promise" on any successful fetch
      .then(response => {
        // check for response errors
        if (response.status !== 200) {
            const errorMsg = 'Database read error: ' + response.status;
            //console.log(errorMsg);
            const tr = document.createElement("tr");
            const td = document.createElement("td");
            td.innerHTML = errorMsg;
            tr.appendChild(td);
            return;
        }
        // valid response will have json data
        response.json().then(data => {
            console.log(data);
            for (let row in data) {
              console.log(data[row]);
              //add_row(data[row]);
            }
        })
    }) 
      // catch fetch errors (ie ACCESS to server blocked)
    .catch(err => {
      //console.error(err);
      const tr = document.createElement("tr");
      const td = document.createElement("td");
      td.innerHTML = err;
      tr.appendChild(td);
      resultContainer.appendChild(tr);
    });
  }
</script>

		
<br/>
<h2>Add Breaking Fun!!</h2>

<form action="javascript:create_user()">
    <p><label>
        Fun:
        <input type="text" name="addFun" id="addFun" required>
    </label></p>
    <p><label>
        Address:
        <input type="text" name="addAddress" id="addAddress" value="addAddress" required>
    </label></p>
    <p><label>
        Activity:
        <input type="text" name="addActivity" id="addActivity" value="addActivity" required>
    </label></p>

    <p>
        <button>Input Activity</button>
    </p>
</form>

<script>
 function create_user(){
    const body = {
        Fun: document.getElementById("addFun").value,
        Address: document.getElementById("addAddress").value,
        Activity: document.getElementById("addActivity").value        
    };

    const requestOptions = {
        method: 'POST',
        body: JSON.stringify(body),
        headers: {
            "content-type": "application/json",
            'Authorization': 'Bearer my-token',
        },
    };

//fetch("https://finalcptperiod4.duckdns.org/api/activities/create", requestOptions)
  fetch("https://finalcptperiod4.duckdns.org/api/activities/create", requestOptions)
    .then(response  => {
       if (response.status == 200) {
          const errorMsg = 'POST SUCCESS: ' + response.status;
          console.log(errorMsg);
          reset(); 
          return;
        }
    })
    .catch(error => console.log('error', error))
 }

</script>