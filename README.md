# LT-homework-cheme7770

Assumptions:
1. All the intracellular species are at steady state.
2. The metabolism follows the model in EcoSal Plus model
3.  Outside the extracellular domain, there are some boundary species which are unbalanced metabolites.
4. Other assumptions are specified in different case below.

1.	Without regulation:
	1.	Aerobic 

	- I set the glucose uptake rate to 10 mmol/(gdw-hr) by setting the lower bound to glu_c to -10. (the value can be arbitrary chosen because it is the experiment condition we can control.)
	- I enabled the ATP maintenance to set the atp flux constrain to be 8.39. (the value is given by the EcoSal Plus paper)
	- I used the cell growth reaction as my objective function.
	- I increase the upper every upper bound in the exchange array to 100. It seems that it almost make no difference. 

################################

# setup the obj -
	objective_coefficient_array = data_dictionary["objective_coefficient_array"]
	objective_coefficient_array[24] = 1.0

	# Default flux bounds array -
	default_flux_bounds_array = data_dictionary["default_flux_bounds_array"]
	default_flux_bounds_array[21,2] = 0.0


	# ATP maintenance -
	default_flux_bounds_array[20,1:2] = 8.67


	# LT Boolean regulatory for aerobic
	# default_flux_bounds_array[90,2] = 0
	# default_flux_bounds_array[71,2] = 0
	# default_flux_bounds_array[94,2] = 0
	# default_flux_bounds_array[129,2] = 0
	# default_flux_bounds_array[65,2] = 0
	# default_flux_bounds_array[66,2] = 0
	# default_flux_bounds_array[67,2] = 0
	# default_flux_bounds_array[107,2] = 0

	# LT Boolean regulatory for anaerobic
	# default_flux_bounds_array[90,2] = 0
	# default_flux_bounds_array[93,2] = 0
	# default_flux_bounds_array[94,2] = 0
	# default_flux_bounds_array[129,2] = 0
	# default_flux_bounds_array[71,2] = 0
	# default_flux_bounds_array[29,2] = 0
	# default_flux_bounds_array[30,2] = 0
	# default_flux_bounds_array[95,2] = 0
	# default_flux_bounds_array[96,2] = 0
	# default_flux_bounds_array[99,2] = 0

	# setup exchange array -

	# LT note: I changed all the upper bound to 100
	# LT noteL I also increased the glucose uptake rate to -10

	species_bounds_array = data_dictionary["species_bounds_array"]
	exchange_array = [
		0.0	100.0	;	# 73 M_ac_b
		0.0	100.0	;	# 74 M_acald_b
		0.0	100.0	;	# 75 M_akg_b
		0.0	100.0	;	# 76 M_co2_b
		0.0	100.0	;	# 77 M_etoh_b
		0.0	100.0	;	# 78 M_for_b
		0.0	100.0	;	# 79 M_fru_b
		0.0	100.0	;	# 80 M_fum_b
		-10.0	100.0	;	# 81 M_glc_D_b
		0.0	100.0	;	# 82 M_gln_L_b
		0.0	100.0	;	# 83 M_glu_L_b
		-10.0	100.0	;	# 84 M_h2o_b
		-100.0	100.0	;	# 85 M_h_b
		0.0	100.0	;	# 86 M_lac_D_b
		0.0	100.0	;	# 87 M_mal_L_b
		-100.0	100.0	;	# 88 M_nh4_b

		# anaerobic o2 set to be 0
		# aerobic o2 set to be -20
		-20.0	100.0	;	# 89 M_o2_b
		-100.0	100.0	;	# 90 M_pi_b
		0.0	100.0	;	# 91 M_pyr_b
		0.0	100.0	;	# 92 M_succ_b
	]

################################

Result:
Growth rate = 0.83 hr-1

2. Anaerobic

	1.	the setting were almost the same as that of aerobic condition. The only different thing is that at anaerobic case, the oxygen uptake rate were set to be zero.
	
################################

# setup the obj -
	objective_coefficient_array = data_dictionary["objective_coefficient_array"]
	objective_coefficient_array[24] = 1.0

	# Default flux bounds array -
	default_flux_bounds_array = data_dictionary["default_flux_bounds_array"]
	default_flux_bounds_array[21,2] = 0.0


	# ATP maintenance -
	default_flux_bounds_array[20,1:2] = 8.67


	# LT Boolean regulatory for aerobic
	# default_flux_bounds_array[90,2] = 0
	# default_flux_bounds_array[71,2] = 0
	# default_flux_bounds_array[94,2] = 0
	# default_flux_bounds_array[129,2] = 0
	# default_flux_bounds_array[65,2] = 0
	# default_flux_bounds_array[66,2] = 0
	# default_flux_bounds_array[67,2] = 0
	# default_flux_bounds_array[107,2] = 0

	# LT Boolean regulatory for anaerobic
	# default_flux_bounds_array[90,2] = 0
	# default_flux_bounds_array[93,2] = 0
	# default_flux_bounds_array[94,2] = 0
	# default_flux_bounds_array[129,2] = 0
	# default_flux_bounds_array[71,2] = 0
	# default_flux_bounds_array[29,2] = 0
	# default_flux_bounds_array[30,2] = 0
	# default_flux_bounds_array[95,2] = 0
	# default_flux_bounds_array[96,2] = 0
	# default_flux_bounds_array[99,2] = 0

	# setup exchange array -

	# LT note: I changed all the upper bound to 100
	# LT noteL I also increased the glucose uptake rate to -10

	species_bounds_array = data_dictionary["species_bounds_array"]
	exchange_array = [
		0.0	100.0	;	# 73 M_ac_b
		0.0	100.0	;	# 74 M_acald_b
		0.0	100.0	;	# 75 M_akg_b
		0.0	100.0	;	# 76 M_co2_b
		0.0	100.0	;	# 77 M_etoh_b
		0.0	100.0	;	# 78 M_for_b
		0.0	100.0	;	# 79 M_fru_b
		0.0	100.0	;	# 80 M_fum_b
		-10.0	100.0	;	# 81 M_glc_D_b
		0.0	100.0	;	# 82 M_gln_L_b
		0.0	100.0	;	# 83 M_glu_L_b
		-10.0	100.0	;	# 84 M_h2o_b
		-100.0	100.0	;	# 85 M_h_b
		0.0	100.0	;	# 86 M_lac_D_b
		0.0	100.0	;	# 87 M_mal_L_b
		-100.0	100.0	;	# 88 M_nh4_b

		# anaerobic o2 set to be 0
		# aerobic o2 set to be -20
		0.0	100.0	;	# 89 M_o2_b
		-100.0	100.0	;	# 90 M_pi_b
		0.0	100.0	;	# 91 M_pyr_b
		0.0	100.0	;	# 92 M_succ_b
	]

################################


Result:
Growth rate = 0.21 hr-1

Compare the differences between aerobic and anaerobic:
The main difference is that in aerobic case, the metabolism circle goes through the whole TCA cycle. However, for the anaerobic case, it only go through the lower part of the TCA cycle.

also, in anaerobic case, it produce some side product such as ac_e, acald_e, etoh_e and for_e, which are not produced in aerobic case.


	1.	With regulation: 


		-  with regulation, we need to build up a Boolean regulation rule.
	-	First, check all the regulator in the system. To check the presence of a specific regulatory species or reaction in the cell, check the uptake_array and flux array and see if that species or reaction is zero in the array. If it is zero, then we assume that species or reaction is not in the cell, otherwise it exist in the cell.
   -	Then, we check the true/false value the the regulator in table 17 in the EcoSal Plus paper by the regulatory rule it provide.
	•	Finally, we can use the above table to check the on/off condition of the gene listed in the table 16 in the EcoSal Plus paper (results are shown in the excel file I upload). And we would know what reactions are turned off in the cell.
	•	In Julia, set the upper flux bound to zero in order to shut down that reaction.


	1.	Aerobic environment
the reactions that had been turned off are: ICL, FUMt2_2, MALt2_2 and SUCCr2_2, FORt2, FORti, FRD7, PFL.
	
################################

# setup the obj -
	objective_coefficient_array = data_dictionary["objective_coefficient_array"]
	objective_coefficient_array[24] = 1.0

	# Default flux bounds array -
	default_flux_bounds_array = data_dictionary["default_flux_bounds_array"]
	default_flux_bounds_array[21,2] = 0.0


	# ATP maintenance -
	default_flux_bounds_array[20,1:2] = 8.67


	# LT Boolean regulatory for aerobic
	default_flux_bounds_array[90,2] = 0
	default_flux_bounds_array[71,2] = 0
	default_flux_bounds_array[94,2] = 0
	default_flux_bounds_array[129,2] = 0
	default_flux_bounds_array[65,2] = 0
	default_flux_bounds_array[66,2] = 0
	default_flux_bounds_array[67,2] = 0
	default_flux_bounds_array[107,2] = 0

	# LT Boolean regulatory for anaerobic
	# default_flux_bounds_array[90,2] = 0
	# default_flux_bounds_array[93,2] = 0
	# default_flux_bounds_array[94,2] = 0
	# default_flux_bounds_array[129,2] = 0
	# default_flux_bounds_array[71,2] = 0
	# default_flux_bounds_array[29,2] = 0
	# default_flux_bounds_array[30,2] = 0
	# default_flux_bounds_array[95,2] = 0
	# default_flux_bounds_array[96,2] = 0
	# default_flux_bounds_array[99,2] = 0

	# setup exchange array -

	# LT note: I changed all the upper bound to 100
	# LT noteL I also increased the glucose uptake rate to -10

	species_bounds_array = data_dictionary["species_bounds_array"]
	exchange_array = [
		0.0	100.0	;	# 73 M_ac_b
		0.0	100.0	;	# 74 M_acald_b
		0.0	100.0	;	# 75 M_akg_b
		0.0	100.0	;	# 76 M_co2_b
		0.0	100.0	;	# 77 M_etoh_b
		0.0	100.0	;	# 78 M_for_b
		0.0	100.0	;	# 79 M_fru_b
		0.0	100.0	;	# 80 M_fum_b
		-10.0	100.0	;	# 81 M_glc_D_b
		0.0	100.0	;	# 82 M_gln_L_b
		0.0	100.0	;	# 83 M_glu_L_b
		-10.0	100.0	;	# 84 M_h2o_b
		-100.0	100.0	;	# 85 M_h_b
		0.0	100.0	;	# 86 M_lac_D_b
		0.0	100.0	;	# 87 M_mal_L_b
		-100.0	100.0	;	# 88 M_nh4_b

		# anaerobic o2 set to be 0
		# aerobic o2 set to be -20
		-20.0	100.0	;	# 89 M_o2_b
		-100.0	100.0	;	# 90 M_pi_b
		0.0	100.0	;	# 91 M_pyr_b
		0.0	100.0	;	# 92 M_succ_b
	]

################################

Growth rate = 0.83 hr-1

	2.	Anaerobic environment
the reactions that had been turned off are: ICL, MALS, FUMt2_2, MALt2_2 and SUCCr2_2,D-LACt2, MDH, NADH16

################################

# setup the obj -
	objective_coefficient_array = data_dictionary["objective_coefficient_array"]
	objective_coefficient_array[24] = 1.0

	# Default flux bounds array -
	default_flux_bounds_array = data_dictionary["default_flux_bounds_array"]
	default_flux_bounds_array[21,2] = 0.0


	# ATP maintenance -
	default_flux_bounds_array[20,1:2] = 8.67


	# LT Boolean regulatory for aerobic
	# default_flux_bounds_array[90,2] = 0
	# default_flux_bounds_array[71,2] = 0
	# default_flux_bounds_array[94,2] = 0
	# default_flux_bounds_array[129,2] = 0
	# default_flux_bounds_array[65,2] = 0
	# default_flux_bounds_array[66,2] = 0
	# default_flux_bounds_array[67,2] = 0
	# default_flux_bounds_array[107,2] = 0

	# LT Boolean regulatory for anaerobic
	default_flux_bounds_array[90,2] = 0
	default_flux_bounds_array[93,2] = 0
	default_flux_bounds_array[94,2] = 0
	default_flux_bounds_array[129,2] = 0
	default_flux_bounds_array[71,2] = 0
	default_flux_bounds_array[29,2] = 0
	default_flux_bounds_array[30,2] = 0
	default_flux_bounds_array[95,2] = 0
	default_flux_bounds_array[96,2] = 0
	default_flux_bounds_array[99,2] = 0

	# setup exchange array -

	# LT note: I changed all the upper bound to 100
	# LT noteL I also increased the glucose uptake rate to -10

	species_bounds_array = data_dictionary["species_bounds_array"]
	exchange_array = [
		0.0	100.0	;	# 73 M_ac_b
		0.0	100.0	;	# 74 M_acald_b
		0.0	100.0	;	# 75 M_akg_b
		0.0	100.0	;	# 76 M_co2_b
		0.0	100.0	;	# 77 M_etoh_b
		0.0	100.0	;	# 78 M_for_b
		0.0	100.0	;	# 79 M_fru_b
		0.0	100.0	;	# 80 M_fum_b
		-10.0	100.0	;	# 81 M_glc_D_b
		0.0	100.0	;	# 82 M_gln_L_b
		0.0	100.0	;	# 83 M_glu_L_b
		-10.0	100.0	;	# 84 M_h2o_b
		-100.0	100.0	;	# 85 M_h_b
		0.0	100.0	;	# 86 M_lac_D_b
		0.0	100.0	;	# 87 M_mal_L_b
		-100.0	100.0	;	# 88 M_nh4_b

		# anaerobic o2 set to be 0
		# aerobic o2 set to be -20
		0.0	100.0	;	# 89 M_o2_b
		-100.0	100.0	;	# 90 M_pi_b
		0.0	100.0	;	# 91 M_pyr_b
		0.0	100.0	;	# 92 M_succ_b
	]

################################

	Growth rate = 0.21 hr-1

