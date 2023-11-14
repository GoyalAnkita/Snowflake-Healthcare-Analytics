# Snowflake-Healthcare-Analytics
Leveraging Snowflake on AWS to predict patient length of stay and predict if one wants to improve the efficiency of the healthcare management in hospital

This parameter helps hospital to idnetify patients of high LOS risk and once identified, patients with high LOS risk can have their treatment plan optimized to minimize LOS and lower the chance of staff/visitor infection.

Prior knowledge of LOS can aid in logistics such as room and bed allocation planning

Data Understanding

TIMELINE:

  Based on admission date-> 08-01-2022 to 11-30-2022
  Number of columns: 11
  Number of Records: 236, 704

  Description of columns:

  Case_ID: Unique id of hospital
  Hospital_Code: Code associated or attached to a particular hospital
  Hospital_Type_Code: Type of hospital
  City_code_hospital: City in which the hospitak is present
  Hospital_region: In which region is present
  Available_extra_room: Ata time of admission of case_id , how many extra rooms are there
  Department: in which dept the patient has been admitted
  Ward_Type: ICU, Normal
  Ward_Facility: Facilities available
  Bed_Grade:quality of beds, eg: reclining beds, normal beds
  PatientID: unique identity for each patient
  City_Code_patient: in which city is the patient from
  Severity_of_illness:
  Visitors_with_patients: how many visitors came along when the patient came
  Admission_date: The date when the patient came
  Discharge_date: The day when that patient was discharged.

  Visualizing the solution:

  We trained an ML model on all the different features to predict the LOS using the historical data

  After Deployment:
    -> Everyday new cases will come to the hospital for admission and we will have all the details except for the discharge_date
    -> Our model should take those new cases everyday and give us the predicted LOS (in days) for each of the cases, which helps us in managing the resources optimally
    -> The prediction for each cases along with the other features should be stored in a logging table
    -> Once we get the actual discharge_date for each case, that should also be added to the logging table (This helps in identifying the perfomance of the model on ongoing basis        & retrain if needed) 
    
