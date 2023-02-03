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
    <th><label for="Activities">Activities:</label></th>
    <th><label for="weeks">Choose a Day:</label></th>
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
    <td><button onclick="add()">Apply</button></td>
  </tr>
</table>
<br>

<div id="schedule"></div>

<script>
  function add(){
    var input = document.getElementById("input").value;
    var week = document.getElementById("week").value;

    var newDiv = document.createElement("div");
    newDiv.innerText = input + " on " + week;
    document.getElementById("schedule").appendChild(newDiv);
  }
</script>
