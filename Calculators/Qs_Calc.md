---
layout: page
title: "Q<sub>s</sub> &harr; M.E. Calculator"
permalink: /Calculators/Qs_Calc
---


For the purpose of converting Matrix Elements to Spectroscopic Quadrupole Moments (and vice versa)<br>
While every precaution has been taken, there may be bugs. So, check first with known values<br>
I believe a states transition to itself is going to be E2. So, on that assumption, units are constant as eb<br>
(trust it to ~6 decimal places, beyond that it seems to very with other calculators I've tested it on)<br>
<br><br>


Spin of state: <br>
<input type="number" id="Spin" name="Spin"><br>



<label for="input_menu_variable"> </label>
<select id="input_menu_variable" name="input_menu_variable">
	<option value="ME_to_Q_text"> M.E. &rarr; Qₛ </option>
	<option value="Q_to_ME_text"> Qₛ &rarr; M.E. </option>
</select>



Input: <br>
<input type="number" id="Input_num" name="Input_num"><br><br>



<button style="background-color: #31d700;
		border-color:black;
		width: 75px;
		height: 75px;
		border-radius: 10px;
		font-size: 20px"
		type="button" onclick="Director()">GO</button>
<br><br>



Output: <br>
<output id="Output_data_1"></output> <output id="Output_data_2"></output>



<script>


	function Director(){
		var Spin	= Number(document.getElementById("Spin").value);
		var Input_num	= Number(document.getElementById("Input_num").value);

		var input_menu_variable	= document.getElementById("input_menu_variable").value;


		if(input_menu_variable == "ME_to_Q_text"){
			document.getElementById("Output_data_1").innerHTML = ME_to_Q(Spin, Input_num);
		}

		if(input_menu_variable == "Q_to_ME_text"){
			document.getElementById("Output_data_1").innerHTML = Q_to_ME(Spin, Input_num);
		}

		document.getElementById("Output_data_2").innerHTML = "eb";

	}


	function ME_to_Q(Spin, Input_num){
		return Input_num * ((( Spin*((2 * Spin) -1)/( ((2* Spin) +1)*((2* Spin) +3)*(Spin +1) ) )*((16*3.14159265359)/5) )**(0.5) );
	}

	function Q_to_ME(Spin, Input_num){
		return Input_num / ((( Spin*((2 * Spin) -1)/( ((2* Spin) +1)*((2* Spin) +3)*(Spin +1) ) )*((16*3.14159265359)/5) )**(0.5) );
	}


</script>


<br><br><br>

<sub> By Reuben </sub>
