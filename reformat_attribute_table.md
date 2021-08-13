#### Step 0. Add new column
Select "Add +" in attribute table, then fill in a new field with Field Name, Alias, and data type (Text), then right click and save.

#### Step 1. Change null values to 0
Select "Cancer" column (change every  instance of "Cancer" to whatever focus is being worked on). To open, right click and select Calculate Field.

In "Cancer ="
```
updateValue(!Cancer!)
```

In "Code Block"
```
def updateValue(value):
  if value == None:
   return '0'
  else: return value
```
#### Step 2. Populate with 1 or 0 based on focus column

For Focus Column:
Select "Cancer" column

In "Code Block" for focus columns
```
def classify(focus):
    if 'Cancer' in focus:
        return 1
    elif 'Cancer' not in focus:
        return 0
```

In "Cancer ="
```
classify(!focus!)
```

For Type Column:
In "Code Block" for Activity columns
```
def classify(activity):
    if 'Advocacy' in activity:
        return 1
    elif 'Advocacy' not in activity:
        return 0
```

In "Advo_Pol_Consult ="
```
classify(!activity!)
```

#### Step 3. Replace 1s and 0s with Yes or No
Select "Cancer" column
```
!Cancer!.replace("1", "Yes")
!Cancer!.replace("0", "No")
```

#### Step 4. Create Focus_List Column that lists all focuses.
In "Code Block"

```
def writeOut(ACEs, Cancer, Cardiovascular, Data_Science, Healthcare_delivery_or_policy, Hematology, Infectious_Disease, Inflammation_and_Immune_Syste, Neurology, Mental_Health, Metabolic_and_endocrine, Other, Oral_and_Gastrointestinal, Pediatrics, Population_Health, Reproductive_urogenital_healt, Respiratory, Sequencing, Skin, Tech_pharm_med_devices):
  
  # define empty output list  
  output_list = []
  
  # populate list if 'Yes' is present in the category column for each asset  
  if ACEs == 'Yes':
     output_list.append('ACEs,')
      
  if Cancer == 'Yes':
    output_list.append('Cancer,')
    
  if Cardiovascular == 'Yes':
    output_list.append('Cardiovascular,')
    
  if Data_Science == 'Yes':
    output_list.append('Data Science,')
    
  if Healthcare_delivery_or_policy == 'Yes':
    output_list.append('Healthcare Delivery or Policy,')
    
  if Hematology == 'Yes':
    output_list.append('Hematology,')
    
  if Infectious_Disease == 'Yes':
    output_list.append('Infectious Disease,')
   
  if Inflammation_and_Immune_Syste == 'Yes':
    output_list.append('Inflammation and Immune System,')
    
  if Neurology == 'Yes':
    output_list.append('Neurology,')
    
  if Mental_Health == 'Yes':
    output_list.append('Mental Health,')
    
  if Metabolic_and_endocrine == 'Yes':
    output_list.append('Metabolic and endocrine,')
    
  if Other == 'Yes':
    output_list.append('Other,')
    
  if Oral_and_Gastrointestinal == 'Yes':
    output_list.append('Oral and Gastrointestinal,')
    
  if Pediatrics == 'Yes':
    output_list.append('Pediatrics,')
    
  if Population_Health == 'Yes':
    output_list.append('Population Health,')
    
  if Reproductive_urogenital_healt == 'Yes':
    output_list.append('Reproductive/Urogenital Health,')
    
  if Respiratory == 'Yes':
    output_list.append('Respiratory,')
    
  if Sequencing == 'Yes':
    output_list.append('Sequencing,')
    
  if Skin == 'Yes':
    output_list.append('Skin,')
    
  if Tech_pharm_med_devices == 'Yes':
    output_list.append('Technology, Pharmaceuticals, and Medical Devices,')
    
  # convert list to string, because only text strings can fill new attribute table cells based on "text" data type I set up
  output_string = ' '.join([str(elem) for elem in output_list])
 
  # remove last comma from string
  final_output = output_string[:-1]
  
  # populate column
  return output_string
```

In "All_Focuses" column

```
writeOut(!ACEs!, !Cancer!, !Cardiovascular!, !Data_Science!, !Healthcare_delivery_or_policy!, !Hematology!, !Infectious_Disease!, !Inflammation_and_Immune_Syste!, !Neurology!, !Mental_Health!, !Metabolic_and_endocrine!, !Other!, !Oral_and_Gastrointestinal!, !Pediatrics!, !Population_Health!, !Reproductive_urogenital_healt!, !Respiratory!, !Sequencing!, !Skin!, !Tech_pharm_med_devices!)
```

#### Step 5. Create All_Activity column that lists all focuses.
In "Code Block"

```
def writeOut(Advo_Pol_Consult, Clinical_care, Clinical_research, Direct_support, Education_outreach, Other_Activity, Research, Research_service, Venture_cap):
  
  # define empty output list  
  output_list = []
  
  # populate list if 'Yes' is present in the category column for each asset
  if Advo_Pol_Consult == 'Yes':
     output_list.append('Advocacy/Policy/Consulting,')
      
  if Clinical_care == 'Yes':
    output_list.append('Clinical Care,')
    
  if Clinical_research == 'Yes':
    output_list.append('Clinical Research,')
    
  if Direct_support == 'Yes':
    output_list.append('Direct Support,')
    
  if Education_outreach == 'Yes':
    output_list.append('Education/Outreach,')
    
  if Other_Activity == 'Yes':
    output_list.append('Other,')
    
  if Research == 'Yes':
    output_list.append('Research,')
   
  if Research_service == 'Yes':
    output_list.append('Research Service,')
    
  if Venture_cap == 'Yes':
    output_list.append('Venture Capitalism/Philanthropy/Granting,')
  
  # convert list to string, because only text strings can fill new attribute table cells based on "text" data type I set up
  output_string = ' '.join([str(elem) for elem in output_list])
  
  # remove last comma from string
  final_output = output_string[:-1]
  
  # populate column
  return output_string
```

In "All_Focuses" column

```
writeOut(!Advo_Pol_Consult!, !Clinical_care!, !Clinical_research!, !Direct_support!, !Education_outreach!, !Other_Activity!, !Research!, !Research_service!, !Venture_cap!)
```
