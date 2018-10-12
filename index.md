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

