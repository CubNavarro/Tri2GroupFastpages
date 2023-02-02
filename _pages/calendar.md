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
    <th><label for="Activities">Activities:</label></th>
    <th><label for="weeks">Choose a Day:</label></th>
    <th><label for="Time">Choose a Time:</label></th>
    <th>Apply</th>
    <th>Save</th>
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
     <select name="Times" id="Time">
        <option>6:00 AM</option>
        <option>7:00 AM</option>
        <option>8:00 AM</option>
        <option>9:00 AM</option>
        <option>10:00 AM</option>
        <option>11:00 AM</option>
        <option>12:00 PM</option>
        <option>1:00 PM</option>
        <option>2:00 PM</option>
        <option>3:00 PM</option>
        <option>4:00 PM</option>
        <option>5:00 PM</option>
        <option>6:00 PM</option>
        <option>7:00 PM</option>
        <option>8:00 PM</option>
        <option>9:00 PM</option>
        <option>10:00 PM</option>
        <option>11:00 PM</option>
        <option>12:00 AM</option>

      </select>
      
    </td>
    <td><button onclick="Add()">Apply</button></td>
    <td><button>Save</button></td>
  </tr>
</table>
<br>

<div id="Days"></div>
<div id="Activities"></div>
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
    <td><div id="Monday"></div></td>
    <td><div id="Tuesday"></div></td>
    <td><div id="Wednesday"></div></td>
    <td><div id="Thursday"></div></td>
    <td><div id="Friday"></div></td>
    <td><div id="Saturday"></div></td>
    <td><div id="Sunday"></div></td>
  </tr>
</table>
<br>
<script>
  function Add(){
  var input = document.getElementById("input").value;
  var week = document.getElementById("week").value;
  switch (week) {
    case "Monday":
      var checkbox = document.createElement("check");
      checkbox.type = "checkbox";
      document.getElementById("monday").appendChild(checkbox);
      document.getElementById("monday").innerText = input + " " + document.getElementById("monday").innerText;
      break;
    case "Tuesday":
      var checkbox = document.createElement("check");
      checkbox.type = "checkbox";
      document.getElementById("tuesday").appendChild(checkbox);
      document.getElementById("tuesday").innerText = input + " " + document.getElementById("tuesday").innerText;
      break;
    case "Wednesday":
      var checkbox = document.createElement("check");
      checkbox.type = "checkbox";
      document.getElementById("wednesday").appendChild(checkbox);
      document.getElementById("wednesday").innerText = input + " " + document.getElementById("wednesday").innerText;
      break;
    case "Thursday":
      var checkbox = document.createElement("check");
      checkbox.type = "checkbox";
      document.getElementById("thursday").appendChild(checkbox);
      document.getElementById("thursday").innerText = input + " " + document.getElementById("thursday").innerText;
      break;
    case "Friday":
      var checkbox = document.createElement("check");
      checkbox.type = "checkbox";
      document.getElementById("friday").appendChild(checkbox);
      document.getElementById("friday").innerText = input + " " + document.getElementById("friday").innerText;
      break;
    case "Saturday":
      var checkbox = document.createElement("check");
      checkbox.type = "checkbox";
      document.getElementById("saturday").appendChild(checkbox);
      document.getElementById("saturday").innerText = input + " " + document.getElementById("saturday").innerText;
      break;
    case "Sunday":
      var checkbox = document.createElement("check");
      checkbox.type = "checkbox";
      document.getElementById("sunday").appendChild(checkbox);
      document.getElementById("sunday").innerText = input + " " + document.getElementById("sunday").innerText;
      break;
  }
  tasks();
}
//displays the day for the first part of daily tasks
function displayDayOfWeek() {
  var d = new Date();
  var days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
  var day = days[d.getDay()];
  document.getElementById("days").innerHTML = "Today is " + day + " these are your tasks:";
}
setInterval(displayDayOfWeek, 1000);
// takes the day and then grabs
function tasks() {
  var d = new Date();
  var days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
  var day = days[d.getDay()];
  switch (day) {
      case "Monday":
          document.getElementById("tasks").innerText = document.getElementById("monday").innerText;
          break;
      case "Tuesday":
          document.getElementById("tasks").innerText = document.getElementById("tuesday").innerText;
          break;
      case "Wednesday":
          document.getElementById("tasks").innerText = document.getElementById("wednesday").innerText;
          break;
      case "Thursday":
          document.getElementById("tasks").innerText = document.getElementById("thursday").innerText;
          break;
      case "Friday":
          document.getElementById("tasks").innerText = document.getElementById("friday").innerText;
          break;
      case "Saturday":
          document.getElementById("tasks").innerText = document.getElementById("saturday").innerText;
          break;
      case "Sunday":
          document.getElementById("tasks").innerText = document.getElementById("sunday").innerText;
          break;
  }
}
