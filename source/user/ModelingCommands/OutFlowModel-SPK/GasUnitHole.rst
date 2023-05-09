.. _GasUnitHole:

GasUnitHole Command **(Still its doc is not completed)**
********************************************************

.. function:: OutFlowModel.GasUnitHole(tag,Hole_Diameter=0.01, Total_t=20, Cd=1, Gas_Constant=8.31446261815324)
   
   This model considers a simultaneous release from Tank with a volume equal to the entered ratio of total amount of stored material by the user [Ref.1]_. 

   .. csv-table:: 
      :header: "Argument", "Type", "Description"
      :widths: 10, 10, 40
	  
      Tag, int, Unique integer value that will be used for referring to the defined elements or objects.
	  "Hole_Diameter", float, Diameter of the hole that gas is releasing from.
	  "Total_t", float, 
	  Cd, float, 
	  Gas_Constant, float, 


   .. admonition:: Example:
   
      **Python Code**
   
      .. code-block:: python
      
        import opensrane as opr
		
        opr.OutFlowModel.GasUnitHole(2, Hole_Diameter=0.02, Total_t=40, Cd=0.62, Gas_Constant=8.31446261815324,)

.. [Ref.1] `J. Casal, Evaluation of the Effects and Consequences of Major Accidents in Industrial Plants, vol. 8. 2018.`

Code Developed by: |bsz|