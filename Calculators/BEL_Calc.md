---
# B(EL) Calculator (non-mixed)
layout: page
title: "B(EL) Calculator"
permalink: /Calculators/BEL_Calc
---



While every precaution has been taken, there may be bugs. So, check first with known values<br>
L is sometimes also denoted as λ<br>
J<sub>i</sub> and J<sub>f</sub> are treated as being higher and lower energy states respectively.<br>
(trust it to ~6 decimal places, beyond that it seems to very with other calculators I've tested it on)<br>



Mass Number (A) :
<input type="number" id="Mass_num" name="Mass_num"><br><br>	<!-- <br> means line break (new line?) -->
Multipolarity (L) :
<input type="number" id="lamda" name="lamda"><br><br>



J<sub>i </sub> (higher) :
<input type="number" id="J_initial" name="J_initial"><br><br>
J<sub>f </sub> (lower) :
<input type="number" id="J_final" name="J_final"><br><br><br><br>




<label for="input_menu_variable"> Input:</label>
<select id="input_menu_variable" name="input_menu_variable">
	<option value="ME_text">Matrix Element (eb^(L/2))</option>
	<option value="BEL_Wu_text">B(EL)↓ (W.u.)</option>
	<option value="BEL_e2fm2L_text">B(EL)↓ (e^2 fm^(2L))</option>
	<option value="ME_efmL_text">Matrix Element (e fm^L)</option>
	<option value="BEL_e2bL_text">B(EL)↓ (e^2 b^L)</option>
	<option value="BEL_e2fm2L_UP_text">B(EL)↑ (e^2 fm^(2L))</option>
	<option value="BEL_e2bL_UP_text">B(EL)↑ (e^2 b^L)</option>
</select><br>
<input type="number" id="Input_num" name="Input_num"><br><br><br>



<label for="want_menu_variable">Output Selection:<br></label>
<select id="want_menu_variable" name="want_menu_variable">
	<option value="ME_text">Matrix Element (eb^(L/2))</option>
	<option value="BEL_Wu_text">B(EL)↓ (W.u.)</option>
	<option value="BEL_e2fm2L_text">B(EL)↓ (e^2 fm^(2L))</option>
	<option value="ME_efmL_text">Matrix Element (e fm^L)</option>
	<option value="BEL_e2bL_text">B(EL)↓ (e^2 b^L)</option>
	<option value="BEL_e2fm2L_UP_text">B(EL)↑ (e^2 fm^(2L))</option>
	<option value="BEL_e2bL_UP_text">B(EL)↑ (e^2 b^L)</option>
</select><br><br>
<button style="background-color: #31d700;
		border-color:black;
		width: 75px;
		height: 75px;
		border-radius: 10px;
		font-size: 20px"
		type="button" onclick="Director()">GO</button>
<br><br>
Output:
<output id="Output_data_1"></output> <output id="Output_data_2"></output>
<p id="Hints_option">  </p>



<script>	// script in java?
	function Director(){

		document.getElementById("Hints_option").innerHTML = "";	// resetting the hint option if it has been triggered


		var Mass_num	= Number(document.getElementById("Mass_num").value);
		var lamda 	= Number(document.getElementById("lamda").value);
		var J_initial 	= Number(document.getElementById("J_initial").value);
		var J_final 	= Number(document.getElementById("J_final").value);
		var Input_num	= Number(document.getElementById("Input_num").value);
		
		var input_menu_variable	= document.getElementById("input_menu_variable").value;
		var want_menu_variable	= document.getElementById("want_menu_variable").value;


		if(input_menu_variable == "ME_text"){
			if(want_menu_variable == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "Go Away.";
			}
			if(want_menu_variable == "BEL_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = ME_BEL_Wu(Mass_num, lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "W.u.";
			}
			if(want_menu_variable == "BEL_e2fm2L_text"){
				document.getElementById("Output_data_1").innerHTML = ME_BEL_e2fm2L(lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "ME_efmL_text"){
				document.getElementById("Output_data_1").innerHTML = ME_eb_efmL(lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e fm^"+lamda;
			}
			if(want_menu_variable == "BEL_e2bL_text"){
				document.getElementById("Output_data_1").innerHTML = ME_BEL_e2bL(J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
			if(want_menu_variable == "BEL_e2fm2L_UP_text"){
				document.getElementById("Output_data_1").innerHTML = ME_BEL_e2fm2L_UP(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "BEL_e2bL_UP_text"){
				document.getElementById("Output_data_1").innerHTML = ME_BEL_e2bL_UP(J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
		}

		if(input_menu_variable == "ME_efmL_text"){
			if(want_menu_variable == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = ME_efmL_eb(lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "eb^"+(lamda/2);
			}
			if(want_menu_variable == "BEL_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = ME_efmL_BEL_Wu(Mass_num, lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "W.u.";
			}
			if(want_menu_variable == "BEL_e2fm2L_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_Wu_e2fm2L(Mass_num, lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "ME_efmL_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "Have a guess what went wrong.";
			}
			if(want_menu_variable == "BEL_e2bL_text"){
				document.getElementById("Output_data_1").innerHTML = ME_efmL_BEL_e2bL(lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
			if(want_menu_variable == "BEL_e2fm2L_UP_text"){
				document.getElementById("Output_data_1").innerHTML = ME_efmL_BEL_e2fm2L_UP(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "BEL_e2bL_UP_text"){
				document.getElementById("Output_data_1").innerHTML = ME_efmL_BEL_e2bL_UP(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
		}

		if(input_menu_variable == "BEL_Wu_text"){
			if(want_menu_variable == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_Wu_ME(Mass_num, lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "eb^"+(lamda/2);
			}
			if(want_menu_variable == "BEL_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "Idiot.";
			}
			if(want_menu_variable == "BEL_e2fm2L_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_Wu_e2fm2L(Mass_num, lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "ME_efmL_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_Wu_ME_efmL(Mass_num, lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e fm^"+lamda;
			}
			if(want_menu_variable == "BEL_e2bL_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_Wu_e2bL(Mass_num, lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
			if(want_menu_variable == "BEL_e2fm2L_UP_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_Wu_e2fm2L_UP(Mass_num, lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "BEL_e2bL_UP_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_Wu_e2bL_UP(Mass_num, lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
		}

		if(input_menu_variable == "BEL_e2fm2L_text"){
			if(want_menu_variable == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2fm2L_ME(lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "eb^"+(lamda/2);
			}
			if(want_menu_variable == "BEL_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2fm2L_Wu(Mass_num, lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "W.u.";
			}
			if(want_menu_variable == "BEL_e2fm2L_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "Why do you even try?";
			}
			if(want_menu_variable == "ME_efmL_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2fm2L_ME_efmL(lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e fm^"+lamda;
			}
			if(want_menu_variable == "BEL_e2bL_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2fm2L_e2bL(lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
			if(want_menu_variable == "BEL_e2fm2L_UP_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_DWN_UP(J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "BEL_e2bL_UP_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2fm2L_e2bL_UP(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
		}

		if(input_menu_variable == "BEL_e2bL_text"){
			if(want_menu_variable == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2bL_ME(J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "eb^"+(lamda/2);
			}
			if(want_menu_variable == "BEL_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2bL_Wu(Mass_num, lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "W.u.";
			}
			if(want_menu_variable == "BEL_e2fm2L_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2bL_e2fm2L(lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "ME_efmL_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2bL_ME_efmL(lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e fm^"+lamda;
			}
			if(want_menu_variable == "BEL_e2bL_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "Is your brain working?";
			}
			if(want_menu_variable == "BEL_e2fm2L_UP_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2bL_e2fm2L_UP(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "BEL_e2bL_UP_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_DWN_UP(J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
		}

		if(input_menu_variable == "BEL_e2fm2L_UP_text"){
			if(want_menu_variable == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2fm2L_UP_ME(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "eb^"+(lamda/2);
			}
			if(want_menu_variable == "BEL_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2fm2L_UP_Wu(Mass_num, lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "W.u.";
			}
			if(want_menu_variable == "BEL_e2fm2L_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_UP_DWN(J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "ME_efmL_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2fm2L_UP_ME_efmL(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e fm^"+lamda;
			}
			if(want_menu_variable == "BEL_e2bL_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2fm2L_UP_e2bL(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
			if(want_menu_variable == "BEL_e2fm2L_UP_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "I give up...";
			}
			if(want_menu_variable == "BEL_e2bL_UP_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2fm2L_UP_e2bL_UP(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
		}

		if(input_menu_variable == "BEL_e2bL_UP_text"){
			if(want_menu_variable == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2bL_UP_ME(J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "eb^"+(lamda/2);
			}
			if(want_menu_variable == "BEL_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2bL_UP_Wu(Mass_num, lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "W.u.";
			}
			if(want_menu_variable == "BEL_e2fm2L_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2bL_UP_e2fm2L(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "ME_efmL_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2bL_UP_ME_efmL(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e fm^"+lamda;
			}
			if(want_menu_variable == "BEL_e2bL_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_UP_DWN(J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 b^"+lamda;
			}
			if(want_menu_variable == "BEL_e2fm2L_UP_text"){
				document.getElementById("Output_data_1").innerHTML = BEL_e2bL_UP_e2fm2L_UP(lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "e^2 fm^"+(2*lamda);
			}
			if(want_menu_variable == "BEL_e2bL_UP_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "Dont.";
			}
			
		}

		if(Mass_num == 0 && lamda == 0 && J_initial == 0 && J_final == 0 && Input_num == 0){
			document.getElementById("Output_data_1").innerHTML = "For Fucks Sake!!!";
			document.getElementById("Output_data_2").innerHTML = "Put in all the required inputs";
			document.getElementById("Hints_option").innerHTML = "All need the input quantity, <br> M.E. needs lamda, B(EL) needs J_i and lamda (if W.u. add A), upB(EL) ones need J_f <br> Add a number in all boxes whether needed or not";
		}


		
	}

		/* Useful equations that do stuff: */

	function BEL_Wu_e2fm2L(Mass_num, lamda, Input_num){
		// return Input_num * ( ( ( Math.pow((1.2),(2 * lamda)) ) / (4*3.14159265359) ) * (Math.pow(( 3  / (lamda + 3)),2) ) * ( Math.pow(Mass_num,( (2*lamda) / 3)) ));
		return Input_num * (( ((1.2)**(2 * lamda)) / (4*3.14159265359) ) * (( 3  / (lamda + 3)) **2 ) * ( Mass_num **( (2*lamda) / 3) ));
	}

	function BEL_e2fm2L_Wu(Mass_num, lamda, Input_num){
		return Input_num / (( ((1.2)**(2 * lamda)) / (4*3.14159265359) ) * (( 3  / (lamda + 3)) **2 ) * ( Mass_num **( (2*lamda) / 3) ));
	}

	function ME_BEL_e2bL(J_initial, Input_num){
		return (Input_num **(2))/((2*J_initial)+1);
	}

	function BEL_e2bL_ME(J_initial, Input_num){
		return ((Input_num) * ( (2*J_initial) +1 ))**(0.5);
	}


		/* Equations made up of the useful ones: */

	function BEL_Wu_e2bL(Mass_num, lamda, Input_num){
		return UNIT_BEL_e2fm2L_e2bL(lamda, BEL_Wu_e2fm2L(Mass_num, lamda, Input_num));
	}

	function BEL_e2bL_Wu(Mass_num, lamda, Input_num){
		return BEL_e2fm2L_Wu(Mass_num, lamda, UNIT_BEL_e2bL_e2fm2L(lamda, Input_num));
	}

	function ME_eb_efmL(lamda, Input_num){
		return UNIT_ME_eb_efmL(lamda, Input_num);
	}

	function ME_efmL_eb(lamda, Input_num){
		return UNIT_ME_efmL_eb(lamda, Input_num);
	}

	function ME_BEL_e2fm2L(lamda, J_initial, Input_num){
		return UNIT_BEL_e2bL_e2fm2L(lamda, ME_BEL_e2bL(J_initial, Input_num));
	}

	function BEL_e2fm2L_ME(lamda, J_initial, Input_num){
		return BEL_e2bL_ME(J_initial, UNIT_BEL_e2fm2L_e2bL(lamda, Input_num));
	}

	function ME_BEL_Wu(Mass_num, lamda, J_initial, Input_num){
		return BEL_e2fm2L_Wu(Mass_num, lamda, UNIT_BEL_e2bL_e2fm2L(lamda, ME_BEL_e2bL(J_initial, Input_num)));
	}

	function BEL_Wu_ME(Mass_num, lamda, J_initial, Input_num){
		return BEL_e2bL_ME(J_initial, UNIT_BEL_e2fm2L_e2bL(lamda, BEL_Wu_e2fm2L(Mass_num, lamda, Input_num)));
	}

	function ME_efmL_BEL_Wu(Mass_num, lamda, J_initial, Input_num){
		return BEL_e2fm2L_Wu(Mass_num, lamda, UNIT_BEL_e2bL_e2fm2L(lamda, ME_BEL_e2bL(J_initial, UNIT_ME_eb_efmL(lamda, Input_num))));
	}

	function BEL_Wu_ME_efmL(Mass_num, lamda, J_initial, Input_num){
		return UNIT_ME_eb_efmL(lamda, BEL_e2bL_ME(J_initial, UNIT_BEL_e2fm2L_e2bL(lamda, BEL_Wu_e2fm2L(Mass_num, lamda, Input_num))));
	}

	function ME_efmL_BEL_e2bL(lamda, J_initial, Input_num){
		return ME_BEL_e2bL(J_initial, UNIT_ME_efmL_eb(lamda, Input_num));
	}

	function BEL_e2bL_ME_efmL(lamda, J_initial, Input_num){
		return UNIT_ME_eb_efmL(lamda, BEL_e2bL_ME(J_initial, Input_num));
	}

	function ME_efmL_BEL_e2fm2L(lamda, J_initial, Input_num){
		return ME_BEL_e2fm2L(lamda, J_initial, UNIT_ME_efmL_eb(lamda, Input_num));
	}

	function BEL_e2fm2L_ME_efmL(lamda, J_initial, Input_num){
		return UNIT_ME_eb_efmL(lamda, BEL_e2fm2L_ME(lamda, J_initial, Input_num));
	}

	function BEL_e2fm2L_e2bL(lamda, Input_num){
		return UNIT_BEL_e2fm2L_e2bL(lamda, Input_num);
	}

	function BEL_e2bL_e2fm2L(lamda, Input_num){
		return UNIT_BEL_e2bL_e2fm2L(lamda, Input_num);
	}

	function ME_BEL_e2fm2L_UP(lamda, J_initial, J_final, Input_num){
		return BEL_DWN_UP(J_initial, J_final, ME_BEL_e2fm2L(lamda, J_initial, Input_num));
	}

	function ME_BEL_e2bL_UP(J_initial, J_final, Input_num){
		return BEL_DWN_UP(J_initial, J_final, ME_BEL_e2bL(J_initial, Input_num));
	}

	function ME_efmL_BEL_e2fm2L_UP(lamda, J_initial, J_final, Input_num){
		return BEL_DWN_UP(J_initial, J_final, ME_efmL_BEL_e2fm2L(lamda, J_initial, Input_num));
	}

	function ME_efmL_BEL_e2bL_UP(lamda, J_initial, J_final, Input_num){
		return BEL_DWN_UP(J_initial, J_final, ME_efmL_BEL_e2bL(lamda, J_initial, Input_num));
	}

	function BEL_Wu_e2fm2L_UP(Mass_num, lamda, J_initial, J_final, Input_num){
		return BEL_DWN_UP(J_initial, J_final, BEL_Wu_e2fm2L(Mass_num, lamda, Input_num));
	}

	function BEL_Wu_e2bL_UP(Mass_num, lamda, J_initial, J_final, Input_num){
		return BEL_DWN_UP(J_initial, J_final, BEL_Wu_e2bL(Mass_num, lamda, Input_num));
	}

	function BEL_e2fm2L_e2bL_UP(lamda, J_initial, J_final, Input_num){
		return BEL_DWN_UP(J_initial, J_final, UNIT_BEL_e2fm2L_e2bL(lamda, Input_num));
	}

	function BEL_e2bL_e2fm2L_UP(lamda, J_initial, J_final, Input_num){
		return BEL_DWN_UP(J_initial, J_final, UNIT_BEL_e2bL_e2fm2L(lamda, Input_num));
	}

	function BEL_e2fm2L_UP_ME(lamda, J_initial, J_final, Input_num){
		return BEL_e2fm2L_ME(lamda, J_initial, BEL_UP_DWN(J_initial, J_final, Input_num));
	}

	function BEL_e2fm2L_UP_Wu(Mass_num, lamda, J_initial, J_final, Input_num){
		return BEL_e2fm2L_Wu(Mass_num, lamda, BEL_UP_DWN(J_initial, J_final, Input_num));
	}

	function BEL_e2fm2L_UP_ME_efmL(lamda, J_initial, J_final, Input_num){
		return BEL_e2fm2L_ME_efmL(lamda, J_initial, BEL_UP_DWN(J_initial, J_final, Input_num));
	}

	function BEL_e2fm2L_UP_e2bL(lamda, J_initial, J_final, Input_num){
		return UNIT_BEL_e2fm2L_e2bL(lamda, BEL_UP_DWN(J_initial, J_final, Input_num));
	}

	function BEL_e2fm2L_UP_e2bL_UP(lamda, J_initial, J_final, Input_num){	//The middle steps here can probably be skipped but I am too sleepy to double check my thinking.
		return BEL_DWN_UP(J_initial, J_final, UNIT_BEL_e2fm2L_e2bL(lamda, BEL_UP_DWN(J_initial, J_final, Input_num)));
	}

	function BEL_e2bL_UP_ME(J_initial, J_final, Input_num){
		return BEL_e2bL_ME(J_initial, BEL_UP_DWN(J_initial, J_final, Input_num));
	}

	function BEL_e2bL_UP_Wu(Mass_num, lamda, J_initial, J_final, Input_num){
		return BEL_e2bL_Wu(Mass_num, lamda, BEL_UP_DWN(J_initial, J_final, Input_num));
	}

	function BEL_e2bL_UP_e2fm2L(lamda, J_initial, J_final, Input_num){
		return UNIT_BEL_e2bL_e2fm2L(lamda, BEL_UP_DWN(J_initial, J_final, Input_num));
	}

	function BEL_e2bL_UP_ME_efmL(lamda, J_initial, J_final, Input_num){
		return BEL_e2bL_ME_efmL(lamda, J_initial, BEL_UP_DWN(J_initial, J_final, Input_num));
	}

	function BEL_e2bL_UP_e2fm2L_UP(lamda, J_initial, J_final, Input_num){	//The middle steps here can probably be skipped but I am too sleepy to double check my thinking.
		return BEL_DWN_UP(J_initial, J_final, UNIT_BEL_e2bL_e2fm2L(lamda, BEL_UP_DWN(J_initial, J_final, Input_num)));
	}


		/* Up and Down B(EL) converters: */

	function BEL_DWN_UP(J_initial, J_final, Input_num){
		return Input_num * (   ( (2*J_initial)  +1 ) / ( (2*J_final)  +1)  );
	}

	function BEL_UP_DWN(J_initial, J_final, Input_num){
		return Input_num / (   ( (2*J_initial)  +1 ) / ( (2*J_final)  +1)  );
	}


		/* Unit converters: */

	function UNIT_ME_eb_efmL(lamda, Input_num){
		return Input_num *( 100 ** (lamda/2) );
	}

	function UNIT_ME_efmL_eb(lamda, Input_num){
		return Input_num / ( 100 ** (lamda/2) );
	}

	function UNIT_BEL_e2bL_e2fm2L(lamda, Input_num){
		return Input_num * ( 100 **lamda );
	}

	function UNIT_BEL_e2fm2L_e2bL(lamda, Input_num){
		return Input_num / ( 100 **lamda );
	}




</script>

<br><br><br>
<sub>By Reuben</sub>