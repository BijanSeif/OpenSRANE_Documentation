.. _PostProcessSPK:

*************************
PostProcess SubPackage
*************************

Using this subpackage, user can export some specific data or results from the recorders. Currently there are ObjsRecorder and Recorder modules for recording. In the following, some commands are described for exporting some results from recorded data are presented.

.. note::

   Using the results in the form of this section for post processing is not mandatory and users can use their own code on the resulted values from analysis of the software. Also, users can develope the current module for post proccessing or add their modules to the source code for futher usages. 
   

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
   
DamagedLevelList key
^^^^^^^^^^^^^^^^^^^^

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
