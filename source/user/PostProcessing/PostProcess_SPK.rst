.. _PostProcessSPK:

*************************
PostProcess SubPackage
*************************

Using this subpackage, user can export some specific data or results from the recorders. Currently there are ObjsRecorder and Recorder modules for recording. In the following, some commands are described for exporting some results from recorded data are presented.

.. note::

   Using the results in the form of this section for post processing is not mandatory and users can use their own code on the resulted values from analysis of the software. Also, users can develope the current module for post proccessing or add their modules to the source code for futher usages. 
   
.. _First Step:

First Step: Load Data
---------------------
   
   At very fist step, user should load data and get the results dictionary. For :ref:`Objs_recorder <Objsrecorder>` and :ref:`Recorder <Recorder>` there are a specific command to load data and get the resutls. These commands are described in the following:
   
   * To load recorded data via :ref:`Objs_recorder <Objsrecorder>` use the following command. In this command **filename** is the name of recoded file using :ref:`Objs_recorder <Objsrecorder>` recorder. All the statistical analysis and data will be store in **Results** variable that shown in the following sample.
   
      .. code-block:: python
	     
         import opensrane as opr
  
         Results=opr.PostProcess.ObjsRecorderPP.Analyze(filename,100)
   
   * To load recorded data via :ref:`Recorder <Recorder>` use the following command. When user is using :ref:`Recorder <Recorder>` to record data and results, there are one separated file for each desired result and so finally there will be more than one file for recorded results. In this command **Recorer_FilenamesList** is the list of the recoded files name using :ref:`Recorder <Recorder>` recorder. All the statistical analysis and data will be store in **Results** variable that shown in the following sample. In the following sample it is assumed that user recorded the desired results in the mentioned file names. 
   
      .. code-block:: python
	     
         import opensrane as opr
  
         Results=opr.PostProcess.RecorderPP.Analyze(Recorer_FilenamesList=['RecorderA.OPRrec','RecorderB.OPRrec','RecorderC.OPRrec','RecorderD.OPRrec','RecorderE.OPRrec'])

Second Step: Results keys
-------------------------

   The **Results** variable that loaded using the commands mention in above part is a dictionary. In the following table the keys of this variable and their corresponding values are described.
   
* **DamagedLevelList** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      **DamagedLevelList**, Results['DamagedLevelList'], "By calling this key, a list of dictionaries will be shown that each dictionary is related to a scenario and shows tag of the elements and level of damage."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      [{1: None, 2: None, 3: None, 4: None, 5: None, 6: None, 7: None, 8: None},
       {1: 0, 2: 0, 3: 0, 4: 0, 5: 0, 6: 1, 7: 0, 8: 1},
       {1: None, 2: None, 3: None, 4: None, 5: None, 6: None, 7: None, 8: None},
       {1: 0, 2: 0, 3: 3, 4: 4, 5: 1, 6: 0, 7: 1, 8: 2},…]



* **FragilityTagList** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      **FragilityTagList**, Results['FragilityTagList'], "This key, returns a list of dictionaries that each dictionary is related to a scenario and each key refers to a plant unit tag and the corresponding value shows the tag of defined fragility or probit that cause damage."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      [{1: None, 2: None, 3: None, 4: None, 5: None, 6: None, 7: None, 8: None},
       {1: None, 2: None, 3: None, 4: None, 5: None, 6: None, 7: None, 8: None},
       {1: None, 2: None, 3: None, 4: None, 5: None, 6: None, 7: None, 8: None},
       {1: None, 2: None, 3: None, 4: None, 5: None, 6: None, 7: None, 8: None},
       {1: 2, 2: 2, 3: 1, 4: 1, 5: 1, 6: 3, 7: 1, 8: 3}, 
       {1: None, 2: None, 3: 1, 4: None, 5: None, 6: None, 7: 1, 8: 1}, 
       {1: None, 2: 3, 3: 1, 4: 3, 5: 2, 6: 1, 7: 1, 8: 1},…]


* **LOCList** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      **LOCList**, Results['LOCList'], "This key, returns a list of dictionaries that each dictionary shows the released liquid mass value (Loss Of Containment) of the plant unit in each scenario."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      [{1: 0, 2: 0, 3: 0, 4: 0, 5: 0, 6: 0, 7: 0, 8: 0},
       {1: 0, 2: 0, 3: 0, 4: 0, 5: 0, 6: 0, 7: 0, 8: 0},
       {1: 0, 2: 0, 3: 0, 4: 0, 5: 0, 6: 0, 7: 0, 8: 0},
       {1: 2827433.3882308137, 2: 4208351.855042743, 3: 4208351.855042743, 4: 4208351.855042743, 5: 3674532.4313447657, 6: 3674532.4313447657, 7: 3674532.4313447657, 8: 3674532.4313447657},…]
	   
	   
* **NodesGroupDamageList** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      **NodesGroupDamageList**, Results['NodesGroupDamageList'], "This key, return a list of dictionaries each dictionary is results of each scenario and its keys are the NodesGroups tag and corresponding value shows the elements damage condition according defined probit functions (0 shows No damage and 1 shows damaged). It returns empty list for Not damaged case."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      [{1: []}, {1: []}, {1: []}, {1: []}, {1: []},
       {1:[0,0,0,0,0,1,1,1,0,1,0,0,0,1,1,1,1,0,0,0,1,0]}, ... ]
	   

* **NodesGroupTypeDict** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      **NodesGroupTypeDict**, Results['NodesGroupTypeDict'], "This key returns a dictionary that each key refers to a NodesGroup tag and the corresponding value is the type of the NodesGroup."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      [{1: []}, {1: []}, {1: []}, {1: []}, {1: []},
       {1:'Social'}, ... ]
	   

* **TotalLOCList** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      **TotalLOCList**, Results['TotalLOCList'], "This key returns list of total liquid mass (kg) that has released in each scenario."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 3674532.4313447657, 0, 0, 03674532.4313447657, 20593020.94647379, 0, 0, 0, 11557416.717732275, 5674351.416812722, 0, 0, 0, 14028296.729529412, 4208351.855042743, 0, 0, 0, 0, 0,…]
	  

* **LOC_bins_hist_probloc** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**LOC_bins_hist_probloc**", "[bins,hist,probloc]= Results['LOC_bins_hist_probloc']", "This key returns 3 lists that are histogram data of the released liquids however they can be calculated from the previous described list. The first list is the bins data that its length should be one value greater than the two other lists. The second list is histogram data that shows the frequency of the bins and the last list is the probability of each bin value."


* **Total_Number_Of_Scenarios** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**Total_Number_Of_Scenarios**", "Results['Total_Number_Of_Scenarios']", "This key simply returns total number of sampled scenarios. "
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      1000000


* **UnitsZeroDamageProb** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
    
      **UnitsZeroDamageProb**, Results['UnitsZeroDamageProb'], "This key returns the damage probability of each unit in zero level as a dictionary. The keys are the units tag and their corresponding values show the probability of damaging in the zero level."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      {1: 0.0018952380952380952, 2: 0.001990476190476190, 3: 0.0021714285714285715, 4: 0.0019047619047619048, 5: 0.0019904761904761905, 6: 0.0021714285714285715, 7: 0.0021523809523809525, 8: 0.001961904761904762}
	  


* **ProbOfFragilities** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      **ProbOfFragilities**, Results['ProbOfFragilities'], "This key returns the probability of happening of each defined fragility or probit function as a dictionary. The keys show the defined fragility or probit tag and the corresponding values shows their governing probability among analysis. Probits that have defined for the Vulnerable areas (NodesGroup) will not consider in this part and their probability will be shown as zero (probits with tag 5 and 6)."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      {1: 0.003952380952380952, 2: 0.012285714285714285, 3: 0.005238095238095238, 4: 0.0009904761904761905, 5: 0.0, 6: 0.0}
	  
	  
* **Damagelevel_eLOC** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**Damagelevel_eLOC**", "Results['Damagelevel_eLOC']", "This key returns the expected released liquid (mass in kg) in each damage level as a dictionary. Each key refers to the damage level and the corresponding value shows expected liquid released mass in that damage level."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      {0: 56082.8170381438, 1: 8802.563549482884, 3: 925.6543716581589, 4: 395.0027138190845, 2: 3376.962598791185, 6: 26.927937030769655, 5: 116.56262508340092}
	  

* **ScenariosAnalyzeNumbers** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**ScenariosAnalyzeNumbers**", "Results['ScenariosAnalyzeNumbers']", "This key returns scenarios name with the following format as key and list of the analyze number as corresponding value as a dictionary."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      {'(0):[3]': [202, 5646, 16833, 17173, 20846, 23658, 29179, 30415, 41698, 42064, 42114], '(0):[3,5]-(1):[2]-(2):[1,6,7]': [316778], 
       '(0):[1,3,6]-(1):[4,7]': [316830], '(0):[1,3,6]-(1):[4,7]-(2):[8]': [316830], '(0):[4,5]-(1):[3]-(2):[2]-(3):[1,6]': [316858]}
	  
   
   .. note::
   
      The rule of mentioning scenarios is : (Damage level):[list of units tag that damaged in this level] for example:
         '(0):[3]' shows a scenario with damaging plant unit 3 in damage level 0
         '(0):[3,5]-(1):[2]' shows a scenario with damaged plant units with tag 3 and 5 in damage level 0 and damaged plant unit with tag 2 at damage level 1


* **ScenariosProbability** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**ScenariosProbability**", "Results['ScenariosProbability']", "This key returns scenarios name as key and the corresponding probability as value. "
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      {'(0):[3]': [202, 5646, 16833, 17173, 20846, 23658, 29179, 30415, 41698, 42064, 42114], '(0):[3,5]-(1):[2]-(2):[1,6,7]': [316778], 
       '(0):[1,3,6]-(1):[4,7]': [316830], '(0):[1,3,6]-(1):[4,7]-(2):[8]': [316830], '(0):[4,5]-(1):[3]-(2):[2]-(3):[1,6]': [316858]}
	   
   .. note::
   
      The rule of mentioning scenarios is : (Damage level):[list of units tag that damaged in this level] for example:
         '(0):[3]' shows a scenario with damaging plant unit 3 in damage level 0
         '(0):[3,5]-(1):[2]' shows a scenario with damaged plant units with tag 3 and 5 in damage level 0 and damaged plant unit with tag 2 at damage level 1
		 
		 
* **ScanariosSubScenario** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**ScanariosSubScenario**", "Results['ScanariosSubScenario'][Scenario name]", "This key returns a dictionary that its key is the Scenario name and the corresponding value is next damage level scenarios."
	  
   Sample for resulted **value**:
   
   .. code-block::
   
      Results['ScanariosSubScenario']['(0):[3]']

      ['(0):[3]-(1):[2]', '(0):[3]-(1):[4]', '(0):[3]-(1):[2,4]', '(0):[3]-(1):[7,8]', '(0):[3]-(1):[7]', '(0):[3]-(1):[2,6]', '(0):[3]-(1):[4,7]', '(0):[3]-(1):[4,7,8]', '(0):[3]-(1):[2,7]', '(0):[3]-(1):[1,2]', '(0):[3]-(1):[2,4,7]', '(0):[3]-(1):[5,6,7]', '(0):[3]-(1):[6,7]']
   
   To see next level scenario:
   
   .. code-block::
      
      Results['ScanariosSubScenario']['(0):[3]-(1):[2]']

      ['(0):[3]-(1):[2]-(2):[1]', '(0):[3]-(1):[2]-(2):[5,6]', '(0):[3]-(1):[2]-(2):[6]', '(0):[3]-(1):[2]-(2):[7]', '(0):[3]-(1):[2]-(2):[1,6]', '(0):[3]-(1):[2]-(2):[4]', '(0):[3]-(1):[2]-(2):[4,7]', '(0):[3]-(1):[2]-(2):[6,7]']
	  
   
	   
   .. note::
   
      The rule of mentioning scenarios is : (Damage level):[list of units tag that damaged in this level] for example:
         '(0):[3]' shows a scenario with damaging plant unit 3 in damage level 0
         '(0):[3,5]-(1):[2]' shows a scenario with damaged plant units with tag 3 and 5 in damage level 0 and damaged plant unit with tag 2 at damage level 1
		 
		 
* **Damagelevel_Scenario_Dict** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**Damagelevel_Scenario_Dict**", "Results['Damagelevel_Scenario_Dict']", "This key returns a dictionary that its keys are the damage level and its values are list of the Scenarios in the corresponding level."
	
	
* **HazardMagnitude** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**HazardMagnitude**", "Results['HazardMagnitude']", "This key returns a list that each cell is a dictionary that its key is the hazard tag and each value is the sampled value."
	  
	  
* **NodesGroupRadiationDict** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**NodesGroupRadiationDict**", "Results['NodesGroupRadiationDict']", "This key returns a dictionary that its keys are the NodesGroup tag and the corresponding value is a list of each node radiation average values."
	  
	  
* **NodesGroupOverPressureDict** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**NodesGroupOverPressureDict**", "Results['NodesGroupOverPressureDict']", "This key returns a dictionary that its keys are the NodesGroup tag and the corresponding value is a list of each node Overpressure average values."
	  

* **NodesGroup_Rad_Probit_Dict** key


   .. csv-table:: 
      :header: "Key Name","How to call","Description"
      :widths: 10, 10, 40
   
      "**NodesGroup_Rad_Probit_Dict**", "Results['NodesGroup_Rad_Probit_Dict']", "This key returns a dictionary that its keys are the NodesGroup tag and the corresponding value is a list of each node Radiation probit average values [Probit(Radiation)]."


PostProcess Plots (PlotPP)
--------------------------
   
   By the following commands it is possible to plot some data using PostProcess resutls. The **Results** variable in the followign commands is the variable that calculated in the :ref:`First Step`. 
   
   
   
* **DamageLevel_ExpectedLoss**
   
   Using this command the expected loss of containment in each damage level will be plotted.

   .. function:: PostProcess.PlotPP.DamageLevel_ExpectedLoss(PPResults=None,yaxistype='log',PlotMode=1)
   
   .. csv-table:: 
      :header: "Argument", "Type", "Description"
      :widths: 10, 10, 40
   
      PPResults, str, Name of the variable that results of :ref:`First Step` are stored in.
      yaxistype, str, "Type of the yaxis ['linear', 'log', 'date', 'category','multicategory']"
      PlotMode, int, "Options between 1,2 and 3 to plot on various editors."
	  
   .. admonition:: Example:
   
      The following demonstrates the use of the mentioned command. The results are stores in a file with name 'Recorder' using :ref:`Objs_recorder <Objsrecorder>`.
   
      **Python Code**
   
      .. code-block:: python
      
         import opensrane as opr
		
         results=opr.PostProcess.ObjsRecorderPP.Analyze('Recorder',100)
		 
         opr.PostProcess.PlotPP.DamageLevel_ExpectedLoss(results,'linear')
    
      The result of above command is:
	  
      .. raw:: html
          :file: figures/DamageLevel_ExpectedLoss.html
		  


* **Unit_ZeroLevel_DamageProb**
   
   Using this command each plant unit damage probability in zero level will be plotted.

   .. function:: PostProcess.PlotPP.Unit_ZeroLevel_DamageProb(PPResults=None,yaxistype='log',PlotMode=1)
   
   .. csv-table:: 
      :header: "Argument", "Type", "Description"
      :widths: 10, 10, 40
   
      PPResults, str, Name of the variable that results of :ref:`First Step` are stored in.
      yaxistype, str, "Type of the yaxis ['linear', 'log', 'date', 'category','multicategory']"
      PlotMode, int, "Options between 1,2 and 3 to plot on various editors."
	  
   .. admonition:: Example:
   
      The following demonstrates the use of the mentioned command. The results are stores in a file with name 'Recorder' using :ref:`Objs_recorder <Objsrecorder>`.
   
      **Python Code**
   
      .. code-block:: python
      
         import opensrane as opr
		
         results=opr.PostProcess.ObjsRecorderPP.Analyze('Recorder',100)
		 
         opr.PostProcess.PlotPP.Unit_ZeroLevel_DamageProb(results,'linear')
    
      The result of above command is:
	  
      .. raw:: html
          :file: figures/Unit_ZeroLevel_DamageProb.html
		  

* **Fragilities_Probits_Probability**
   
   Using this command each fragility and probit happening probability will be plotted.

   .. function:: PostProcess.PlotPP.Fragilities_Probits_Probability(PPResults=None,yaxistype='log',PlotMode=1)
   
   .. csv-table:: 
      :header: "Argument", "Type", "Description"
      :widths: 10, 10, 40
   
      PPResults, str, Name of the variable that results of :ref:`First Step` are stored in.
      yaxistype, str, "Type of the yaxis ['linear', 'log', 'date', 'category','multicategory']"
      PlotMode, int, "Options between 1,2 and 3 to plot on various editors."
	  
   .. admonition:: Example:
   
      The following demonstrates the use of the mentioned command. The results are stores in a file with name 'Recorder' using :ref:`Objs_recorder <Objsrecorder>`.
   
      **Python Code**
   
      .. code-block:: python
      
         import opensrane as opr
		
         results=opr.PostProcess.ObjsRecorderPP.Analyze('Recorder',100)
		 
         opr.PostProcess.PlotPP.Fragilities_Probits_Probability(results,'log')
    
      The result of above command is:
	  
      .. raw:: html
          :file: figures/Fragilities_Probits_Probability.html
		  

* **Expected_Total_LOC**
   
   Using this command expected total loss of containment will be plotted.

   .. function:: PostProcess.PlotPP.Expected_Total_LOC(PPResults=None,yaxistype='log',PlotMode=1)
   
   .. csv-table:: 
      :header: "Argument", "Type", "Description"
      :widths: 10, 10, 40
   
      PPResults, str, Name of the variable that results of :ref:`First Step` are stored in.
      yaxistype, str, "Type of the yaxis ['linear', 'log', 'date', 'category','multicategory']"
      PlotMode, int, "Options between 1,2 and 3 to plot on various editors."
	  
   .. admonition:: Example:
   
      The following demonstrates the use of the mentioned command. The results are stores in a file with name 'Recorder' using :ref:`Objs_recorder <Objsrecorder>`.
   
      **Python Code**
   
      .. code-block:: python
      
         import opensrane as opr
		
         results=opr.PostProcess.ObjsRecorderPP.Analyze('Recorder',100)
		 
         opr.PostProcess.PlotPP.Expected_Total_LOC(results,'log')
    
      The result of above command is:
	  
      .. raw:: html
          :file: figures/Expected_Total_LOC.html
		  

* **ScenarioProbability**
   
   Using this command probability of scenarios will be plotted.

   .. function:: PostProcess.PlotPP.ScenarioProbability(PPResults=None,yaxistype='log',DamageLevel=[],ScenarioList=[],PlotMode=1,)
   
   .. csv-table:: 
      :header: "Argument", "Type", "Description"
      :widths: 10, 10, 40
   
      PPResults, str, Name of the variable that results of :ref:`First Step` are stored in.
      yaxistype, str, "Type of the yaxis ['linear', 'log', 'date', 'category','multicategory']"
      PlotMode, int, "Options between 1,2 and 3 to plot on various editors."
	  DamageLevel, list of int, List of damage level that user want to watch the results
	  ScenarioList, list of str, List of scenarios that want to be shown in plot. (for Empty it means that plot all scenarios)
	  
	  
   .. admonition:: Example:
   
      The following demonstrates the use of the mentioned command. The results are stores in a file with name 'Recorder' using :ref:`Objs_recorder <Objsrecorder>`.
   
      **Python Code**
   
      .. code-block:: python
      
         import opensrane as opr
		
         results=opr.PostProcess.ObjsRecorderPP.Analyze('Recorder',100)
		 
         opr.PostProcess.PlotPP.ScenarioProbability(results,'log',)
    
      The result of above command is:
	  
      .. raw:: html
          :file: figures/ScenarioProbability.html
      
      |

      And to plot just for damage level 0 and 1
	  
      .. code-block:: python
      
         import opensrane as opr
		
         results=opr.PostProcess.ObjsRecorderPP.Analyze('Recorder',100)
		 
         opr.opr.PostProcess.PlotPP.ScenarioProbability(results,'log',DamageLevel=[0,1],)
		 
      .. raw:: html
          :file: figures/ScenarioProbability01.html
		  

      |

      And if user wants to plot for some specific scenarios:
	  
      .. code-block:: python
		 
         opr.PostProcess.PlotPP.ScenarioProbability(results,'linear', ScenarioList=[f'(0):[{i}]' for i in range(1,9)],)
		 
      .. raw:: html
          :file: figures/ScenarioProbabilityScens.html