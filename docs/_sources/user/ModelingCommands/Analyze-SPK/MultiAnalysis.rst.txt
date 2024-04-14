.. _MultiAnalysis:

MultiAnalysis Command
*********************

.. function:: opr.Analyze.ScenarioAnalyze.MultiAnalysis(AnalysisNumber=100, fileindex=0, MergeSavedFiles=False)
   
   This command as obvious from its name, **implement multiple analysis** equal to specified AnalysisNumber.

   .. csv-table:: 
      :header: "Argument", "Type", "Description"
      :widths: 10, 10, 40
   
      fileindex, int, An integer value that will be add to the end of the filename to save recorded scenarios in seperate file.
      MergeSavedFiles, boolean, "If set this option into True, When analysis finished all files will be merge into one file and for huge files it takes so much memory and time!. The created final file has an uppercase M in its suffix."
	  
.. note::

   When the number of analyses reaches to the defined SaveStep number, the resulted scenarios will be saved in the defined file specified in the recorder object with defined fileindex as suffix. 
   


Code Developed by: |bsz|