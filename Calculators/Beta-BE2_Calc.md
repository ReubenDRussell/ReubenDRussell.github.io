---
layout: page
title: "B(E2) &harr; &beta; Calculator"
permalink: /Calculators/Beta-BE2_Calc
---


For the purpose of converting B(E2) to quadrupole deformation parameter &beta; (and vice versa)<br>
While every precaution has been taken, there may be bugs. So, check first with known values<br>
B(E2) is the reduced transition probability of an E2 transition, &beta; comes from the eccentricity <br> of an ellipse when describing the axial deformation of a nucleus<br>
<br><br>


Mass_Number (A): <br>
<input type="number" id="Mass_num" name="Mass_num"><br>
Proton Number (Z): <br>
<input type="number" id="Prot_num" name="Mass_num"><br>



<label for="input_menu_variable"> </label>
<select id="input_menu_variable" name="input_menu_variable">
	<option value="BE2_to_Beta_text"> B(E2) &rarr; &beta; </option>
	<option value="Beta_to_BE2_text"> &beta; &rarr; B(E2) </option>
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
<output id="Output_data_A"></output> <output id="Output_data_B"></output>




<script>


	function Director(){

		var Prot_num = Number(document.getElementById("Prot_num").value);	/* proton number*/
		var Mass_num = Number(document.getElementById("Mass_num").value);	/* mass number*/
		var e_num = Number(1.0);	/* assuming electron's charge is still just 1*/
		var Input_num = Number(document.getElementById("Input_num").value); //float(Input_data_Main.get());

		var input_selection =  document.getElementById("input_menu_variable").value; //str(want_menu_variable.get());


		if(input_selection == "BE2_to_Beta_text"){
			document.getElementById("Output_data_A").innerHTML = BE2_to_Beta(Prot_num, Mass_num, e_num, Input_num);
		}

		if(input_selection == "Beta_to_BE2_text"){
			document.getElementById("Output_data_A").innerHTML = Beta_to_BE2(Prot_num, Mass_num, e_num, Input_num);
			document.getElementById("Output_data_B").innerHTML = "e<sup>2</sup>fm<sup>4</sup>";
		}

	}


	function BE2_to_Beta(Prot_num, Mass_num, e_num, Input_num){
		return ((4*3.14159265359)/(3*Prot_num*(R0_number(Mass_num)**2))) * (( Input_num/(e_num**2) )**(0.5));
	}

	function Beta_to_BE2(Prot_num, Mass_num, e_num, Input_num){
		return (((Input_num*3*Prot_num*(R0_number(Mass_num)**2))/(4*3.14159265359))**2)*(e_num**2);
	}

	function R0_number(Mass_num){
		return 1.2 * (Mass_num**(1/3));
	}


</script>



<sub> By Reuben </sub>
