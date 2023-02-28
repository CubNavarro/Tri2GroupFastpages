---
title: Activities
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

      const titleData = document.createElement("td")
      titleData.innerHTML = `<a href=${ev.link}> ${ev.title} </a>`
      row.appendChild(titleData)

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
//const url = "http://127.0.0.1:8086/api/breakingFun"
const url = "https://fnvs.duckdns.org/api/breakingFun"
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
        <input type="text" name="addAddress" id="addAddress" value="CNN" required>
    </label></p>
    <p><label>
        Activity:
        <input type="text" name="addActivity" id="addActivity" value="San Diego" required>
    </label></p>

    <p>
        <button>Input Breaking Fun</button>
    </p>
</form>

<script>
 function create_user(){
    const body = {
        title: document.getElementById("addFun").value,
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

//fetch("http://127.0.0.1:8086/api/breakingFun/create", requestOptions)
  fetch("https://fnvs.duckdns.org/api/breakingFun/create", requestOptions)
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


<br/>
<h2>Delete Breaking Fun!!</h2>

<form action="javascript:delete_Fun()">
    <p><label>
        Fun Item:
        <input type="text" name="deleteFun" id="deleteFun" required>
    </label></p>

    <p>
        <button>Delete Breaking Fun</button>
    </p>
</form>

<script>
 function delete_Fun(){
    const body = {
        id: document.getElementById("deleteFun").value,
    };

    const requestOptions = {
        method: 'DELETE',
        mode: 'cors', // no-cors, *cors, same-origin
        cache: 'default', // *default, no-cache, reload, force-cache, only-if-cached
        credentials: 'omit', // include, *same-origin, omit	
        body: JSON.stringify(body),
        headers: {
            "content-type": "application/json",
            'Authorization': 'Bearer my-token',
        },
    };

//fetch("http://127.0.0.1:8086/api/breakingFun/delete", requestOptions)
 fetch("https://fnvs.duckdns.org/api/breakingFun/delete", requestOptions)
    .then(response  => {
       if (response.status == 200) {
          const errorMsg = 'DELETE SUCCESS: ' + response.status;
          console.log(errorMsg);
          reset(); 
          return;
        }
    })
    .catch(error => console.log('error', error))
 }