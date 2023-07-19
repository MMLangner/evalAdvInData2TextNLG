# evalAdvInData2TextNLG
"Supplementary material for the INLG 2023 paper "Validating Predictive Models Of Evaluative Language For Controllable Data2Text Generation"

This directory contains supplementary material for the paper "Validating Predictive Models Of Evaluative Language For Controllable Data2Text Generation",
accepted for the 16th International Natural Language Generation Conference (INLG 2023)."

Code, web application and data are published under GNU General Public License V3.
Please refer to the respective license in this github repository.


 /additional_graphs_and_plots_technical_database
 
    --> data analysis of technical database, visualizing
	data for people without permission from ADAC to use the database

 /Data_analysis_and_regression/experimental_data
 
    --> contains source code for data analysis, regression model training
	and plotting of the various graphs and figures in the paper
	It also contains different databases with data collected during different
	phases of the empirical study

	> scripts for data analysis
	1. ablation_data_evaluation.py + studyEvalAdv_GER_50_ablation.sqlite3
	2. main_study_data_evaluation.py + studyEvalAdv_GER_50.sqlite3

	> scripts needed for regression:
	linear_regression.py
	polynomial_regression.py
	dnn_regression.py
	RegressionTest.py (interface to data analysis scripts |^|)
      
      
 /empirical_study/studyEvalAdv
 
    --> web application built for conducting the empirical study.
	The application can be run locally & offline after installing
	necessary requirements (django, command "pip3 install django")
	You should have installed a python interpreter and a package 
	manager such as pip beforehand.

	USAGE:

	1. open terminal / cmd.exe and  navigate to the directory /studyEvalAdv,
	which contains "manage.py"
	2. execute command "python3 manage.py makemigrations"
	3. execute command "python3 mangage.py migrate"
	4. execute command "python3 mangage.py runserver"
	5. open browser and visit url "http://127.0.0.1:8000/evalAdv/"

	For simple usage, please use one of the databases in /databases,
	copy to /studyEvalAdv and rename to "db.sqlite3".

	ADVANCED:

	You can modify items etc. by manipulating the csv files "items,csv",
	"items_ablation.csv" and "distractors.csv". In order to transfer changes
	to the database, you should follow these steps:

	1. make modifications to items
	2. run python3 manage.py shell
	3. execute script:

	> from evalAdv.models import ExpectationItem, DistractorItem
	> from imports import load_csv_items
	> a = load_csv_items("<item_file_name>", ExpectationItem) # replace file name
	> for x in a:
	>     x.save()
	> b = load_csv_items("<distractors_file>", DistractorItem) # replace file name
	> for y in b:
	>     y.save()
	> quit()
