---
layout: page
title: "Safe Coulex Calculator"
permalink: /Calculators/Safe_Coulex
---


For the purpose of estimating the separation between nuclei and the energy required to get that close relating to coulex. <br>
While every precaution has been taken, there may be bugs. So, check first with known values <br>
Input the bombarding energy or separation you want to find the other for (you know what I mean) <br>
Bombarding energy (MeV) = the energy of the projectile before interaction with the target (Max at &theta; = 180 degrees) <br>
Separation (fm) = the gap between the approximate edges of the nuclei (set 5fm for Cline criterion) <br>
<br><br>


Projectile Mass Number (A):
<input type="number" id="Mass1" name="Mass1"><br>
Projectile Proton Number (Z):
<input type="number" id="Prot1" name="Prot1"><br><br>

Target Mass Number (A):
<input type="number" id="Mass2" name="Mass2"><br>
Target Proton Number (Z):
<input type="number" id="Prot2" name="Prot2"><br><br>

Scattering Angle (&theta;) in degrees:
<input type="number" id="Thetadeg" name="Thetadeg"><br>




<label for="input_menu_variable";> What Are You Inputting? </label>
<select id="input_menu_variable" name="input_menu_variable">
	<option value="SEPARATION_text"> Separation (fm) </option>
	<option value="E_BOMB_text"> Bombarding Energy (MeV) </option>
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
		var Mass1 = Number(document.getElementById("Mass1").value);	//#projectile
		var Mass2 = Number(document.getElementById("Mass2").value);	//#target
		var Prot1 = Number(document.getElementById("Prot1").value);	//#projectile
		var Prot2 = Number(document.getElementById("Prot2").value);	//#target
		var Thetadeg = Number(document.getElementById("Thetadeg").value);
		let Theta = Thetadeg * (Math.PI/180);	// Converting from degrees to radians

		var Input_num = Number(document.getElementById("Input_num").value);
		var input_menu_variable = document.getElementById("input_menu_variable").value;

		// if(input_menu_variable == "select option"){
		// 	Output_data_A["text"] = "Select Something.\n OR I WILL FIND YOU!";
		// 	Output_data_B["text"] = "(Do what he says, he means it?)";
		// }

		if(input_menu_variable == "SEPARATION_text"){
			document.getElementById("Output_data_1").innerHTML = E_bomb_sep(Mass1,Mass2,Prot1,Prot2,Theta,Input_num);
			document.getElementById("Output_data_2").innerHTML = "MeV";
		}

		if(input_menu_variable == "E_BOMB_text"){
			document.getElementById("Output_data_1").innerHTML = Sep_E_bomb(Mass1,Mass2,Prot1,Prot2,Theta,Input_num);
			document.getElementById("Output_data_2").innerHTML = "fm";
		}
	}



	function E_bomb_sep(Mass1,Mass2,Prot1,Prot2,Theta,Input_num){	// manually input separation distance AND manually input Theta
		return 0.72*(1+ (1/(Math.sin(Theta/2))))*((Mass1 + Mass2)/Mass2)*( (Prot1*Prot2)/( (1.25*((Mass1**(1/3))+(Mass2**(1/3)))) +Input_num) );
	}


	// function E_bomb_Cline(Mass1,Mass2,Prot1,Prot2,Theta){	// use separation = 5fm AND manually input Theta
	// 	return 0.72*(1+ (1/(np.sin(Theta/2))))*((Mass1 + Mass2)/Mass2)*( (Prot1*Prot2)/( 1.25*((Mass1**(1/3))+(Mass2**(1/3))) +5) );
	// }


	// function E_max_sep(Mass1,Mass2,Prot1,Prot2,Separation){	// manually input separation AND using Theta = 180deg
	// 	return 1.44*((Mass1 + Mass2)/Mass2)*( (Prot1*Prot2)/( 1.25*((Mass1**(1/3))+(Mass2**(1/3))) +Separation) );
	// }


	// function E_max_Cline(Mass1,Mass2,Prot1,Prot2){	// use separation = 5fm AND using Theta = 180deg
	// 	return 1.44*((Mass1 + Mass2)/Mass2)*( (Prot1*Prot2)/( 1.25*((Mass1**(1/3))+(Mass2**(1/3))) +5) );
	// }


	function Sep_E_bomb(Mass1,Mass2,Prot1,Prot2,Theta,Input_num){	// manually put in Bombarding Energy AND Theta
		return (0.72*(1+ (1/(Math.sin(Theta/2))))*((Mass1 + Mass2)/Mass2)*( (Prot1*Prot2)/(Input_num)) - (1.25*((Mass1**(1/3))+(Mass2**(1/3)))));
	}

</script>




<sub> By Reuben </sub>
