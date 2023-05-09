.. _Objsrecorderloader:

Objs_recorder_loader Command
============================


   
   This command contains the following subcommands that are used to load the recorded data using :ref:`Objs_recorder <Objsrecorder>`. In the following each subcommand with their usage are described.
   
   Bank method is another way to load scenarios. It loads all scenarios into the memory and so calling them are so much fast but if there were no enough memory probably user encounter with system problem!
   So just use it when a powerful system is available.

   .. note::
   
      **THIS METHOD USES HUGE AMOUNT OF MEMORY AND NOT RECOMMENDED FOR LARGE SIMULATIONS NUMBER**. 

loadScenarioBank SUBCOMMAND
---------------------------

   .. function:: Recorders.Objs_recorder_loader.loadScenarioBank(filename)
   
      This command loads all recorder scenarios using :ref:`Objs_recorder <Objsrecorder>` in to the system memory. User can send all recorded scenarios (ScenarioBank) to the memory and call them faster. It is obvious that weak systems with low memory capcity, this method may encounter with system hanging. Also, it returns all scenarios as a dictionary that keys are the number of the simulation.
   
      .. csv-table:: 
         :header: "Argument", "Type", "Description"
         :widths: 10, 10, 40
      
         filename, str, Name of the :ref:`Objs_recorder <Objsrecorder>` created file.
     

load1ScenarioOfBank SUBCOMMAND
------------------------------

   .. function:: opr.Recorders.Objs_recorder_loader.load1ScenarioOfBank(ScenarioTag)
   
      By defining the file name to previous command (loadScenarioBank), all the recorded scenarios with all their objects will be load in the memory. **After loading the scnario bank using loadScenarioBank**, Using this command, user can load a scenario into the memory. **By loading a scenario into the memory, it is ready to be investigated and ready to plot and also all anlysis results are accessable**.
   
      .. csv-table:: 
         :header: "Argument", "Type", "Description"
         :widths: 10, 10, 40
      
         ScenarioTag, int, The number of desired scenario.      
   

load1ScenarioOfBank SUBCOMMAND
------------------------------

   .. function:: opr.Recorders.Objs_recorder_loader.ClearScenarioBank()
   
      By the this command memory will be clear from loaded Scenario Bank.
   


Code Developed by: |bsz|