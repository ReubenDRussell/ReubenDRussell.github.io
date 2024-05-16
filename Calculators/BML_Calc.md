---
layout: page
title: "B(ML) Calculator"
permalink: /Calculators/BML_Calc
---



While every precaution has been taken, there may be bugs. So, check first with known values<br>
L is sometimes also denoted as &lambda;<br>
J<sub>i</sub> and J<sub>f</sub> are treated as being higher and lower energy states respectively.<br>
(trust it to ~6 decimal places, beyond that it seems to very with other calculators I've tested it on)<br>
NEED TO DOUBLE CHECK UNITS ETC. IN CASE OF WRONG POWERS IN THE UNIT. before showing.<br>




Mass Number (A) :
<input type="number" id="Mass_num" name="Mass_num"><br><br>

Multipolarity (L) :
<input type="number" id="lamda" name="lamda"><br><br>



J<sub>i </sub> (higher) :
<input type="number" id="J_initial" name="J_initial"><br><br>

J<sub>f </sub> (lower) :
<input type="number" id="J_final" name="J_final"><br><br><br><br>




<label for="input_menu_variable"> Input:<br></label>
<select id="input_menu_variable" name="input_menu_variable">
	<option value="ME_text">Matrix Element (&mu;_N fm^((2L-2)/2) )</option>
	<option value="BML_Wu_text">B(ML)↓ (W.u.)</option>
	<option value="BML_DWN_text">B(ML)↓ (&mu;_N^2 fm^(2L-2) )</option>
	<option value="BML_UP_text">B(ML)↑ (&mu;_N^2 fm^(2L-2) )</option>
</select><br>
<label for="Input_num";>  </label>
<input type="number" id="Input_num" name="Input_num"><br><br><br>





Output Selection:<br>
<select id="want_menu_variable" name="want_menu_variable">
	<option value="ME_text">Matrix Element (&mu;_N fm^((2L-2)/2) )</option>
	<option value="BML_Wu_text">B(ML)↓ (W.u.)</option>
	<option value="BML_DWN_text">B(ML)↓ (&mu;_N^2 fm^(2L-2) )</option>
	<option value="BML_UP_text">B(ML)↑ (&mu;_N^2 fm^(2L-2) )</option>
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




<script>
	
	function Director(){

		var Mass_num	= Number(document.getElementById("Mass_num").value);
		var lamda 	= Number(document.getElementById("lamda").value);
		var J_initial 	= Number(document.getElementById("J_initial").value);
		var J_final 	= Number(document.getElementById("J_final").value);
		var Input_num	= Number(document.getElementById("Input_num").value);
		
		var input_selection	= document.getElementById("input_menu_variable").value;
		var want_selection	= document.getElementById("want_menu_variable").value;

		document.getElementById("Output_data_1").innerHTML = "work check";

		if(input_selection == "ME_text"){
			if(want_selection == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "Go Away.";
			}
			if(want_selection == "BML_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = ME_BML_Wu(Mass_num, lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "W.u.";
			}
			if(want_selection == "BML_DWN_text"){
				document.getElementById("Output_data_1").innerHTML = ME_BML_DWN(J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "&mu;<sub>N</sub><sup>2</sup> fm<sup>"+((2*lamda) -2)+"</sup>";
			}
			if(want_selection == "BML_UP_text"){
				document.getElementById("Output_data_1").innerHTML = ME_BML_UP(J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "&mu;<sub>N</sub><sup>2</sup> fm<sup>"+((2*lamda) -2)+"</sup>";
			}
		}

		if(input_selection == "BML_Wu_text"){
			if(want_selection == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = BML_Wu_ME(Mass_num, lamda, J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "&mu;<sub>N</sub> fm<sup>"+(((2*lamda) -2)/2)+"</sup>";
			}
			if(want_selection == "BML_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "Try again ... &#128577;";
			}
			if(want_selection == "BML_DWN_text"){
				document.getElementById("Output_data_1").innerHTML = BML_Wu_DWN(Mass_num, lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "&mu;<sub>N</sub><sup>2</sup> fm<sup>"+((2*lamda) -2)+"</sup>";
			}
			if(want_selection == "BML_UP_text"){
				document.getElementById("Output_data_1").innerHTML = BML_Wu_UP(Mass_num, lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "&mu;<sub>N</sub><sup>2</sup> fm<sup>"+((2*lamda) -2)+"</sup>";
			}
		}

		if(input_selection == "BML_DWN_text"){
			if(want_selection == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = BML_DWN_ME(J_initial, Input_num);
				document.getElementById("Output_data_2").innerHTML = "&mu;<sub>N</sub> fm<sup>"+(((2*lamda) -2)/2)+"</sup>";
			}
			if(want_selection == "BML_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = BML_DWN_Wu(Mass_num, lamda, Input_num);
				document.getElementById("Output_data_2").innerHTML = "W.u.";
			}
			if(want_selection == "BML_DWN_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "Just; no.";
			}
			if(want_selection == "BML_UP_text"){
				document.getElementById("Output_data_1").innerHTML = BML_DWN_UP(J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "&mu;<sub>N</sub><sup>2</sup> fm<sup>"+((2*lamda) -2)+"</sup>";
			}
		}

		if(input_selection == "BML_UP_text"){
			if(want_selection == "ME_text"){
				document.getElementById("Output_data_1").innerHTML = BML_UP_ME(J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "&mu;<sub>N</sub> fm<sup>"+(((2*lamda) -2)/2)+"</sup>";
			}
			if(want_selection == "BML_Wu_text"){
				document.getElementById("Output_data_1").innerHTML = BML_UP_Wu(Mass_num, lamda, J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "W.u.";
			}
			if(want_selection == "BML_DWN_text"){
				document.getElementById("Output_data_1").innerHTML = BML_UP_DWN(J_initial, J_final, Input_num);
				document.getElementById("Output_data_2").innerHTML = "&mu;<sub>N</sub><sup>2</sup> fm<sup>"+((2*lamda) -2)+"</sup>";
			}
			if(want_selection == "BML_UP_text"){
				document.getElementById("Output_data_1").innerHTML = "COME ON!?!?!?";
				document.getElementById("Output_data_2").innerHTML = "Go and have a break<br>then try again";
			}
		}
	}




			/*## Useful equations that do stuff: ##*/

	function ME_BML_DWN(J_initial, Input_num){
		return (Input_num **(2))/((2*J_initial)+1);
	}

	function BML_Wu_DWN(Mass_num, lamda, Input_num){
		return Input_num * ( ((10*(1.2**((2*lamda) -2)))/3) * ((3/(lamda +3))**2) * (Mass_num ** ( ((2*lamda) -2) /3)) );
	}

	function BML_DWN_ME(J_initial, Input_num){
		return (Input_num * ( (2*J_initial) +1 ))**(0.5);
	}

	function BML_DWN_Wu(Mass_num, lamda, Input_num){
		return Input_num / ( ((10*(1.2**((2*lamda) -2)))/3) * ((3/(lamda +3))**2) * (Mass_num ** ( ((2*lamda) -2) /3)) );
	}


			/*## Equations made up of the useful ones: ##*/


	function ME_BML_Wu(Mass_num, lamda, J_initial, Input_num){
		return BML_DWN_Wu(Mass_num, lamda, ME_BML_DWN(J_initial, Input_num) );
	}

	function ME_BML_UP(J_initial, J_final, Input_num){
		return BML_DWN_UP(J_initial, J_final, ME_BML_DWN(J_initial, Input_num));
	}

	function BML_Wu_ME(Mass_num, lamda, J_initial, Input_num){
		return BML_DWN_ME(J_initial, BML_Wu_DWN(Mass_num, lamda, Input_num));
	}

	function BML_Wu_UP(Mass_num, lamda, J_initial, J_final, Input_num){
		return BML_DWN_UP(J_initial, J_final, BML_Wu_DWN(Mass_num, lamda, Input_num));
	}

	function BML_UP_ME(J_initial, J_final, Input_num){
		return BML_DWN_ME(J_initial, BML_UP_DWN(J_initial, J_final, Input_num));
	}

	function BML_UP_Wu(Mass_num, lamda, J_initial, J_final, Input_num){
		return BML_UP_DWN(J_initial, J_final, BML_DWN_Wu(Mass_num, lamda, Input_num));
	}



				/*## Up and Down B(ML) converters: ##*/

	function BML_DWN_UP(J_initial, J_final, Input_num){			//# converter rather than caring about unit, so can be used for e^2b^L and e^2fm^2L if the same before and after units
		return Input_num * (   ( (2*J_initial)  +1 ) / ( (2*J_final)  +1)  );
	}

	function BML_UP_DWN(J_initial, J_final, Input_num){			//# converter rather than caring about unit, so can be used for e^2b^L and e^2fm^2L if the same before and after units
		return Input_num / (   ( (2*J_initial)  +1 ) / ( (2*J_final)  +1)  );
	}






</script>



<sub> By Reuben </sub>
