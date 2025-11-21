# Project: Modeling Earthquake Damage
### Dataset Description

The data was collected during the post-earthquake field surveys conducted by the Nepal National Planning Commission and partners following the 2015 Gorkha earthquake. Trained enumerators visited the affected areas and collected information on the level of damage, structural characteristics (foundation, roof, building materials), household information, age, location information, and building use for over 250,000 buildings. The damage level for buildings is categorized from low damage to almost complete destruction.

The data was gotten from drivendata as part of the Earthquake Modeling Damage Competition. The totality of the data is available through the Nepal Earthquake Open Data Portal.

Originally, the data was provided in three seperate files:

    train_values
    train_labels
    test_values

The train_value files contains the feature describing each building, while train_labels provide the corresponding target variable, damage_grade, which indicates the level of structural damage. For this project, the train_values and the train_labels datasets were merged using the unique building identifier to form a single training dataset. The test_values file were not used since the target labels for it were not provided.

### Why the data was collected

Although the primary goal of the survey was to identify beneficiaries eligible for government assistance for housing reconstruction, it also collected other useful socio-economic information which serves different uses including training ML tasks. After disasters, government and humanitarian organization usually need rapid and reliable estimates of building damage to prioritize emergency response, assess vulnerability to guide future preparedness and plan recovery operations.

### Application Domain

The data was collected as part of a national post-disaster assesment effort so it's aplication domain falls under disaster risk management, specifically post-disaster damage assessment. By understanding which features contribute most to level of damages, the project can provide insight useful for improving building construction in earthquake-prone areas.

### Learning task to study

The target variable 'damage_grade' represents a discrete numerical value that indicates the level of damage to building. The damage_grade contains distinct values from 1-3. This problem is formulated as a multi-class classification task with the aim of predicting one of several damage grades for each building.
