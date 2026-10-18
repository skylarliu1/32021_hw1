# 32021_hw1

Part A

Choose 2 open-source data versioning tools from

    lakeFS (https://lakefs.io/)
    DVC (https://dvc.org/)
    Git-LFS (https://git-lfs.com)
    Delta Lake (https://delta.io/ )
    Quilt (https://www.quilt.bio/open-source).

Data: athletes.csv.zipDownload athletes.csv.zip

Clean data using following code:

    # Remove not relevant columns
    data = data.dropna(subset=['region','age','weight','height','howlong','gender','eat', \
                               'train','background','experience','schedule','howlong', \
                               'deadlift','candj','snatch','backsq','experience',\
                               'background','schedule','howlong'])
    data = data.drop(columns=['affiliate','team','name','athlete_id','fran','helen','grace',\
                              'filthy50','fgonebad','run400','run5k','pullups','train'])

    # Remove Outliers

    data = data[data['weight'] < 1500]
    data = data[data['gender'] != '--']
    data = data[data['age'] >= 18]
    data = data[(data['height'] < 96) & (data['height'] > 48)]

    data = data[(data['deadlift'] > 0) & (v2['deadlift'] <= 1105)|((data['gender'] == 'Female') \
                 & (data['deadlift'] <= 636))]
    data = data[(data['candj'] > 0) & (data['candj'] <= 395)]
    data = data[(data['snatch'] > 0) & (data['snatch'] <= 496)]
    data = data[(data['backsq'] > 0) & (data['backsq'] <= 1069)]

    # Clean Survey Data

    decline_dict = {'Decline to answer|': np.nan}
    data = data.replace(decline_dict)
    data = data.dropna(subset=['background','experience','schedule','howlong','eat'])

 

For each tool -

    Work with given machine learning dataset - call this dataset version 1 (v1).
    Clean the dataset such as removing outliers, cleaning survey responses, introducing new features - call this dataset version 2 (v2).
    For both versions calculate total_lift and divide dataset into train and test, keeping the same split ratio.
    Use tool to version the dataset.
    Run EDA (exploratory data analysis) of the dataset v1.
    Use the dataset v1 to build a baseline machine learning model to predict total_lift.
    Run metrics for this model.
    Update the dataset version to go to dataset v2 without changing anything else in the training code.
    Run EDA (exploratory data analysis) of dataset v2.
    Build a machine learning model with "new" dataset v2 to predict total_lift.
    Run metrics for this model.
    Compare and comment on the accuracy/metrics of the models using v1 and v2.
    Use a linter on your code.
    Use tensor flow privacy library with the dataset v2 and calculate the metrics for the new DP model.
    Compute the DP using TensorFlow privacy compute_dp_sgd_privacy (https://www.tensorflow.org/responsible_ai/privacy/tutorials/classification_privacy)
    Compare and comment on the accuracy/metrics of the non-DP and DP models using dataset v2 - submit 1 slide

After doing the above for the 2 tools, compare the tools using the experience from above and comment on - submit 1 slide

    ease of installation
    ease of data versioning
    ease of switching between versions for the same model
    effect of DP on model accuracy/metrics

Deliverables:

    Submit a python script or notebooks for Tasks 1 - 15.
    Submit 1 slide containing output for 13.
    Submit 1 slide for 16 and 1 slide on the tool comparison.

Part B

Choose any dataset for reporting analysis (no prediction, only descriptive analytics).

Do EDA and transformations on the data as necessary.

Report on insights from the data.

Use any open-source data lineage tool such as https://marquezproject.ai/, https://www.grai.io/, https://datahub.com/ to build data lineage diagram highlighting data source, transformations, and how it is getting used for reporting analysis.

Deliverables:

    Submit the report(s) and insights in 1 slide.
    Submit the data lineage diagram in 1 slide.
