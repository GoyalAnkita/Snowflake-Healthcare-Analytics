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
    -> logging table will be craeted in SnowFlake

    -> In the logging table we have the predicted length of stay for each cases in the logging table and once the actual discharge happens, we add to the logging table, and then          we will know what is the actual length of stay and as we have the predicted length of stay so their difference is going to give us ethe accuracy of the model, if the               accuracy deteoriates over time we can retrain our model.


    **Problem Solving Approach**

    1) Data is not stored in csv format-> our data is in snowflake 
    2) Development environment is different from data environment-> In order for us to take data out, we need to take the data and built any MLL out of it, so we need to take data        out from data environment to my developing environment in order to do Machine Learning, so in this project our data resides in Snowflake database system and our development        environment is AWS SageMaker

    3) Healthcare Data -> Preprocess& EDA -> Feature Engineering -> Model Ready Data( here we use SQL and do as many simplifications in our data as possible)->SnowfLAKE pYTHON            cONNECTOR-> AWS Sagemaker environment-> Feature Selection-> Modelling Experiments -> Model Deployment ( As a scheduled notebook instance)<-> Model Retraining(as a scheduled        notebook instance) ( we can schedule the notebook at a specified time)
    4) We take this data daily and use these steps daily-> and overall teh data will be sent back to snowflake-> the predictions along with other features will be sent back to            SnowFlake to create logging table
    5) Over the time the model might gte detoriated, as new features will be coming, so we need to have a retraining pipeline which monitors the perfomance of teh model
    
    
