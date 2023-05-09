.. _UniAnalyze:

UniAnalyze Command
******************

.. function:: opr.Analyze.ScenarioAnalyze.UniAnalyze(SavetoFile=True)
   
   By running this command, **only one scenario analysis will be run** and the defined algorithm will be implemented for defined model. The main structure of the command has been shown in the following.

.. note::

   When analyze finished, all objects and results are in the memory and user can use them for post processing. SavetoFile option cause that the resulted scenario will be remain in the memory and when the number of scenarios in the memory become equal recorder object SaveStep number, they will be save into the reorder file specified in the recorder object.
   
   if user set SavetoFile to False, then the results won't save into the defined recorder object and results remain in the memory. If user, for some reasons had to use UniAnalyze to do multiple analysis, then the SavetoFile option can set to False to make the analysis faster and then after some steps (for example 1000 steps) can set it True till the recorded results will be save into the defined recorder file or object.
   


Code Developed by: |bsz|