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
Select "Cancer" column

In "Code Block" for focus columns
```
def classify(focus):
    if 'Cancer' in focus:
        return 1
    elif 'Cancer' not in focus:
        return 0
```

In "Code Block" for type columns
```
def classify(type):
    if 'Advocacy' in type:
        return 1
    elif 'Advocacy' not in type:
        return 0
```

In "Cancer ="
```
classify(!focus!)
```

#### Step 3. Replace 1s and 0s with Yes or No
Select "Cancer" column
```
!Cancer!.replace("1", "Yes")
!Cancer!.replace("0", "No")
```
