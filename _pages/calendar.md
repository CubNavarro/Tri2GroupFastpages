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
    <th><label for="Times">Choose a Time:</label></th>
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
    </td>
    <td>
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