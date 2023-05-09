.. _MultiParallel:

MultiParallel Command
*********************

.. function:: opr.Analyze.ScenarioAnalyze.MultiParallel(AnalysisNumber=100, NumberOfProcessors=3,)

   
   By this command users can analyze their model with multiple cores or CPUs. Depend on the number of the cores the analysis duration will be reduce more. 

   .. note::
   
      * If user define NumberOfProcessors more than the number of the available cores, it will be reduced to the available number of the cores.
      
      * Users should pay attention that this command should be used after (if __name__=='__main__':) and outside of that, it will be encounter with error!. Because of mentioned limitation it cannot be used inside the Jupyter NoteBook (for windows operating system). Here is an example of how should it be hire:
   
   
   .. admonition:: Example:
   
      **Python Code**
   
      .. code-block:: python
      
        import opensrane as opr
		
        if __name__=='__main__':
           opr.Analyze.ScenarioAnalyze.MultiParallel(AnalysisNumber=1_000_000, NumberOfProcessors=15)


Code Developed by: |bsz|