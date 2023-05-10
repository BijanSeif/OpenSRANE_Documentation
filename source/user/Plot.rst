.. _Plot:

***************
Plot SubPackage
***************

Plot subpackage present some commands that using them user can **plot some of defined or resulted data**. Obviously, the current plots are according current needs and users can add other plots with other visualization packages and …. Plotly python visualization package has been selected for plots however users can develop other plotting packages. In the following, available plotting commands are described:

Plotly
======

   The following commands are provided using Plotly library.
   
Fragilities
-----------
   
   To plot defined fragilities. 
   
   .. function:: Plot.Plotly.PlotFragilities(StdNumber=3, NPoints=100, FragilityTagList=[],PlotMode=1)

   
   .. csv-table:: 
      :header: "Argument", "Type", "Description"
      :widths: 10, 10, 40
	  
      StdNumber, int, The number of the standard deviation that will be consider for each fragility to plot in this range
	  NPoints, int, The number of the points that will be consider for each fragility 
	  FragilityTagList, list of int, the list of fragility tags and those that mentioned in this list will be plotted and if nothing entered all fragilities will be plot.
	  PlotMode, int, "Options with values equal to 1,2 or 3 to change the plot mode. For variou Editors with one on these option plot will be activate!"
	  
   .. admonition:: Example:
   
      In the following example three Fragilities are defined and also plotted with various NPoints and StdNumber.
   
      **Python Code**
   
      .. code-block:: python
      
        opr.wipe()
        
        #Define the Fragilities
        opr.Fragilities.Fragility(1,'EFB','normal',5,1)
        opr.Fragilities.Fragility(2,'Gear Damage','normal',6,1.2)
        opr.Fragilities.Fragility(3,'Body Buckling','normal',7,1.4)
		
        #Plot command
        opr.Plot.Plotly.PlotFragilities(StdNumber=3, NPoints=100, FragilityTagList=[], PlotMode=1)
	
      The above command causes to plot Fragilities all together as shown in the following.
	  
      .. raw:: html
          :file: figures/FragAll.html
	  
      But the following command will cause to plot only fragilities with tags 1 and 2 and only with 10 numbers along their curves.
	  
      **Python Code**
   
      .. code-block:: python
		
        #Plot command
        opr.Plot.Plotly.PlotFragilities(StdNumber=3, NPoints=10, FragilityTagList=[1,2], PlotMode=1)

      .. raw:: html
          :file: figures/Frag12.html		
         
Probits
-------	 
   
   To plot defined probits.
   
   .. function:: Plot.Plotly.PlotProbits(StdNumber=3, NPoints=100, ProbitTag=None, PlotMode=1)
   
   .. csv-table:: 
      :header: "Argument", "Type", "Description"
      :widths: 10, 10, 40
	  
      StdNumber, int, The number of the standard deviation that will be consider for each fragility to plot in this range
	  NPoints, int, The number of the points that will be consider for each fragility 
	  ProbitTag, int, the tag of a special defined probit to plot and in nothing enter all probits will be plotted.
	  PlotMode, int, "Options with values equal to 1,2 or 3 to change the plot mode. For variou Editors with one on these option plot will be activate!"
	  
   .. admonition:: Example:
   
      In the following example three Fragilities are defined and also plotted with various NPoints and StdNumber.
   
      **Python Code**
   
      .. code-block:: python
      
        opr.wipe()

        opr.Fragilities.Probit(tag=1,Distribution_Type='normal',K1=5,K2=2)
        opr.Fragilities.Probit(2,'normal',3,2)
        opr.Fragilities.Probit(3,'lognormal',4,3)
		
        #Plot command
        opr.Plot.Plotly.PlotProbits(StdNumber=3, NPoints=100, ProbitTag=None, PlotMode=1)
	
      The above command causes to plot probits all together as shown in the following.
	  
      .. raw:: html
          :file: figures/ProbAll.html
	  
      But the following command will cause to plot only Probit with tags 1 and only with 10 numbers along its curves.
	  
      **Python Code**
   
      .. code-block:: python
		
        #Plot command
        opr.Plot.Plotly.PlotProbits(StdNumber=3, NPoints=10, ProbitTag=1, PlotMode=1)

      .. raw:: html
          :file: figures/Prob1.html		
		
		
		
Code Developed by: |bsz|