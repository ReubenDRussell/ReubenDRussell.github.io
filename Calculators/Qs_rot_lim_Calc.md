---
layout: page
title: Q<sub>s</sub> lim &harr; B(E2) Calculator
permalink: /Calculators/Qs_rot_lim_Calc
---


For the purpose of estimating the limits of Q<sub>s</sub> for an axial rotor using B(E2)<br>
While every precaution has been taken, there may be bugs. So, check first with known values <br>
I know this works for B(E2;0<sup>+</sup><sub>1</sub> &rarr; 2<sup>+</sup><sub>1</sub>), probably works for other B(E2)?<br>
This calculator is mainly for finding the axial rotor limit of Q<sub>s</sub>. Numbers given should be taken as |Q<sub>s</sub>(2<sup>+</sup><sub>1</sub>)|<br>
If changing the equation to look at a non 2<sup>+</sup><sub>1</sub> state Q<sub>s</sub> then look into Clebsch-Gordan coefficients (just to be sure)<br>
<br><br>


<label for="input_menu_variable"> </label>
<select id="input_menu_variable" name="input_menu_variable">
	<option value="BE2_to_Q_text"> B(E2)&uarr; &rarr; Qₛ </option>
	<option value="Q_to_BE2_text"> Qₛ &rarr; B(E2)&uarr; </option>
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

		var Input_num	= Number(document.getElementById("Input_num").value);

		var input_menu_variable	= document.getElementById("input_menu_variable").value;


		if(input_menu_variable == "BE2_to_Q_text"){
			document.getElementById("Output_data_1").innerHTML = BE2_to_Q(Input_num);
			document.getElementById("Output_data_2").innerHTML = "eb";
		}

		if(input_menu_variable == "Q_to_BE2_text"){
			document.getElementById("Output_data_1").innerHTML = Q_to_BE2(Input_num);
			document.getElementById("Output_data_2").innerHTML = "e<sup>2</sup>b<sup>2</sup>";
		}

	}


	function BE2_to_Q(Input_num){
		return (-2/7)*( ( (16*3.14159265359*Input_num)/5 )**(0.5) );
	}

	function Q_to_BE2(Input_num){
		return (5/(16*3.14159265359))*( ((-7/2)*Input_num)**2 );
	}


</script>




<sub> By Reuben </sub>
