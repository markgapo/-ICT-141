<!DOCTYPE html>
<html>
<head>
	<title>ICT 141</title>
	<script type="text/javascript" src="script.js"></script>
	<link rel="stylesheet" type="text/css" href="style.css">
</head>
<body class="body">
	<div class="header">
		<p>ICT 141 MIDTERM PROJECT</p>
	</div>

	<div class="search">
		<input type="text" id="myInput" onkeyup="search()" placeholder="Search">
	</div>

	<div>
		<table id="data_table">
		<tr>
		<th>ID NUMBER</th>
		<th>NAME</th>
		<th>YEAR</th>
		<th>Option</th>
		</tr>

		<tr id="row4">
		<td rowspan="3" colspan="5"><input type="button" class="add" onclick="create_row();" value="Create" id="create_button"></td>
		
		</tr>


		</table>

	</div>

</body>
</html>

function create_row()
{
 var table=document.getElementById("data_table");
 var table_len=(table.rows.length);
 var row = table.insertRow(table_len).outerHTML="<tr><td><input type='text' id='new_idnumber'></td><td><input type='text' id='new_name'></td><td><input type='number' id='new_year'></td><td align='center'><input type='button' id='create_button' class='add2' onclick='add_row()' value='Create'></td></tr>"
 document.getElementById("row4").style.display="none";
}
 
function add_row()
{
 var new_idnumber=document.getElementById("new_idnumber").value;
 var new_name=document.getElementById("new_name").value;
 var new_year=document.getElementById("new_year").value;

 if(!check_inputEmpty()){
 var table=document.getElementById("data_table");
 var table_len=(table.rows.length)-1;
 var row = table.insertRow(table_len).outerHTML="<tr id='row"+table_len+"'><td id='idnumber_row"+table_len+"'>"+new_idnumber+"</td><td id='name_row"+table_len+"'>"+new_name+"</td><td id='year_row"+table_len+"'>"+new_year+"</td><td><input type='button' id='edit_button"+table_len+"' value='Edit' class='edit' onclick='edit_row("+table_len+")'> <input type='button' id='save_button"+table_len+"' value='Save' class='save' onclick='save_row("+table_len+")'> <input type='button' value='Delete' class='delete' onclick='delete_row("+table_len+")'></td></tr>";
 }
 document.getElementById("new_idnumber").value="";
 document.getElementById("new_name").value="";
 document.getElementById("new_year").value="";
}

function edit_row(no)
{
 document.getElementById("edit_button"+no).style.display="none";
 document.getElementById("save_button"+no).style.display="inline";
      
 var idnumber=document.getElementById("idnumber_row"+no);
 var name=document.getElementById("name_row"+no);
 var year=document.getElementById("year_row"+no);

 var idnumber_data=idnumber.innerHTML;
 var name_data=name.innerHTML;
 var year_data=year.innerHTML;

 idnumber.innerHTML="<input type='text' id='idnumber_text"+no+"' value='"+idnumber_data+"'>";
 name.innerHTML="<input type='text' id='name_text"+no+"' value='"+name_data+"'>";
 year.innerHTML="<input type='text' id='year_text"+no+"' value='"+year_data+"'>";
}

function save_row(no)
{
 var idnumber_val=document.getElementById("idnumber_text"+no).value;
 var name_val=document.getElementById("name_text"+no).value;
 var year_val=document.getElementById("year_text"+no).value;

 if(!check_inputEmptyEdit(no)){
 document.getElementById("idnumber_row"+no).innerHTML=idnumber_val;
 document.getElementById("name_row"+no).innerHTML=name_val;
 document.getElementById("year_row"+no).innerHTML=year_val;

 document.getElementById("edit_button"+no).style.display="inline";
 document.getElementById("save_button"+no).style.display="inline";
 }
 else{
 document.getElementById("edit_button"+no).style.display="none";
 document.getElementById("save_button"+no).style.display="inline";
 }
}

function delete_row(no)
{
 document.getElementById("row"+no+"").outerHTML="";
}

function check_inputEmpty()
{
 var empty = false,
  idnumber=document.getElementById("new_idnumber").value,
  name=document.getElementById("new_name").value,
  year=document.getElementById("new_year").value,
  table=document.getElementById("data_table"),
  tr = table.getElementsByTagName("tr");
  if(idnumber === ""){
    alert("Please enter your ID number");
    empty=true;
  }
  else if(name === ""){
    alert("Please enter your name");
    empty=true;
  }
  else if(year === ""){
    alert("Please enter your year");
    empty=true;
  }
  else if(year < 1){
    alert("Invalid year!");
    empty=true;
  }
  return empty;
}
function check_inputEmptyEdit(no)
{
 var empty = false,
  idnumber=document.getElementById("idnumber_text"+no).value,
  name=document.getElementById("name_text"+no).value,
  year=document.getElementById("year_text"+no).value;
  if(idnumber === ""){
    alert("Please enter your ID number");
    empty=true;
  }
  else if(name === ""){
    alert("Please enter your name");
    empty=true;
  }
  else if(year === ""){
    alert("Please enter your year");
    empty=true;
  }
  else if(year < 1){
    alert("Invalid year!");
    empty=true;
  }
  return empty;
}

function search()  
{
 var input, filter, table, tr, td, i, idnumber, name, year;
 input = document.getElementById("myInput");
 filter = input.value.toUpperCase();
 table = document.getElementById("data_table");
 tr = table.getElementsByTagName("tr");
 
 for (i = 0; i < tr.length; i++) {
   
   idnumber = tr[i].getElementsByTagName("td")[0];
   name = tr[i].getElementsByTagName("td")[1];
   year = tr[i].getElementsByTagName("td")[2];
   
   if (idnumber) {
    if (idnumber.innerHTML.toUpperCase().indexOf(filter) > -1) {
        tr[i].style.display = "";
    } 
    else if(name.innerHTML.toUpperCase().indexOf(filter) > -1) {
      tr[i].style.display = "";
    }
    else if(year.innerHTML === filter) {
      tr[i].style.display = "";
    }
    else {
        tr[i].style.display = "none";
    }
   }
 }
  document.getElementById("row4").style.display="none";
}

 .body {
    background-color: #EEE;
}

.header {
    text-align: center;
    width: 60%;
    background-color: #0e3c00;
    height: 50px;
    margin-left: 20%;
}

.header p {
    padding-top: 15px;
    color: #b7b01d;
}

.search {
    width: 60%;
    background-color:#0e3c00;
    margin-left: 20%;
    height: 45px;
    margin-top: 5%;      
}

.search input {
    width: 35%;
    margin-left:7px;
    margin-top: 7px;
    padding: 5px;
    border-radius: 2px;
}
            
table {
    margin-left: 20%;
    font-family: "Trebuchet MS", Arial, Helvetica, sans-serif;
    border-collapse: collapse;
    width: 60%;
}

td {
    border: 1px solid #0e3c00;
    padding: 8px;
    text-align: center;
}

th {
    padding-top: 12px;
    padding-bottom: 12px;
    text-align: center;
    background-color: #0e3c00;
    color: #b7b01d;
    border: 1px;
}

.add {

    width: 10%;
    background-color: #0e3c00;
    color: #b7b01d;
    height: 30px;

}

.add2 {

    width: 60%;
    background-color: #0e3c00;
    color: #b7b01d;
    height: 30px;

}
.edit {
    width: 20%;
    background-color: #0e3c00;
    color: #b7b01d;
    height: 30px;
}
      
.save {
    width: 25%;
    background-color: #0e3c00;
    color: #b7b01d;
    height: 30px;
}

.delete {
    width: 30%;
    background-color: #0e3c00;
    color: #b7b01d;
    height: 30px;
}

