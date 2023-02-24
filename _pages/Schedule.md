---
layout: page
title: Schedule Maker
permalink: /markdown/
---
## Schedule Maker
  - Add your activities
  - Organize your activities
  - Schedule times for activities
<br>
## Create A Schedule!


<table width="500px">
  <tr>
    <th><label for="input">Activities:</label></th>
    <th><label for="week">Choose a Day:</label></th>
    <button onclick="Reset()">Reset</button>
    <th>Apply</th>
  </tr>
  <tr>
    <td><input id="input"></td>
    <td>
      <select name="week" id="week">
        <option>Monday</option>
        <option>Tuesday</option>
        <option>Wednesday</option>
        <option>Thursday</option>
        <option>Friday</option>
        <option>Saturday</option>
        <option>Sunday</option>
      </select>
    </td>
    <td><button onclick="Add()">Apply</button></td>
  </tr>
</table>
<br>

<table>
  <tr>
    <th>Monday</th>
    <th>Tuesday</th>
    <th>Wednesday</th>
    <th>Thursday</th>
    <th>Friday</th>
    <th>Saturday</th>
    <th>Sunday</th>
  </tr>
    <tr>
    <td><div id="monday"></div></td>
    <td><div id="tuesday"></div></td>
    <td><div id="wednesday"></div></td>
    <td><div id="thursday"></div></td>
    <td><div id="friday"></div></td>
    <td><div id="saturday"></div></td>
    <td><div id="sunday"></div></td>
  </tr>
</table>
<br>

<script>
  function Add(){
    var input = document.getElementById("input").value;
    var week = document.getElementById("week").value;
    var day = document.getElementById(week.toLowerCase());
    day.innerHTML = day.innerHTML + "<br>" + input;
    
fetch()
  .then((response) => response.json())
  .then((data) => console.log(data));
  
}


</script>

