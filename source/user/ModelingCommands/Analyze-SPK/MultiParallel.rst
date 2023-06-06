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

   .. warning::
   
      Users should attention that **Never use MultiParallel inside a loop!**. MultiParallel uses **multiprocessing** package that contains commands for parallel proccessing but it do not let you to use it inside a loop and you probably encounter with errors. This issue happened on windows operating system and maybe on mac and linux you found no error!
      
      There are some tricks that you can use MultiParallel command inside a loop. Look at this example to get the idea.

Code Developed by: |bsz|