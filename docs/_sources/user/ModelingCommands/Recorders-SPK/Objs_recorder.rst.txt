.. _Objsrecorder:

Objs_recorder Command
*********************

.. function:: Recorders.Objs_recorder(tag, filename='', SaveStep=100, fileAppend=True,)

   
   Using this command, a file will be determined by the user to record all simulated scenarios objects. By every analyze, the created objects and results will be record in the mentioned file and user can call them using the load commands.

   .. csv-table:: 
      :header: "Argument", "Type", "Description"
      :widths: 10, 10, 40
   
      Tag, int, Unique integer value that will be used for referring to the defined elements or objects.
	  filename, str, Name of the file that user wants to record data in.
	  SaveStep, int, Number of steps that after that data will be move to the file and memory become empty. Bigger values cause faster analysis but it needs enough system memory.
	  fileAppend, boolean, "True says that if the filename exists, add the recorded scenarios to the existing file and false will clear the file if exists."


   .. admonition:: Example:
   
      The following demonstrates the use of the Objs_recorder command.
   
      **Python Code**
   
      .. code-block:: python
      
        import opensrane as opr
		
        opr.Recorders.Objs_recorder(tag=1, filename='ObjsRecorder', SaveStep=100, fileAppend=False,)


Code Developed by: |bsz|