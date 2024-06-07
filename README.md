# Pyspark

SparkSession is the entry point to Spark functionality.
VectorAssembler is used to combine multiple columns into a single vector column, which is required for machine learning models.
DecisionTreeClassifier is our machine learning algorithm.
MulticlassClassificationEvaluator is used to evaluate the performance of our model.



spark = SparkSession.builder.appName("IrisClassifier").getOrCreate()
.SparkSession.builder is used to create a new Spark session.
.appName("IrisClassifier") names our application "IrisClassifier".
.getOrCreate() gets an existing Spark session or creates a new one if none exists.


For simplicity, let's create the Iris dataset manually within our script.


StringIndexer converts the species (string) column into a label (numeric) column.
VectorAssembler combines the feature columns into a single vector column named "features".
df.select("features", "label") selects only the necessary columns for our model.



df.randomSplit([0.8, 0.2]) splits the DataFrame into 80% training data and 20% test data.



DecisionTreeClassifier(featuresCol="features", labelCol="label") initializes the classifier.
model = dt.fit(train_df) trains the model on the training data.



model.transform(test_df) applies the model to the test data to make predictions.


MulticlassClassificationEvaluator evaluates the model based on accuracy.
accuracy = evaluator.evaluate(predictions) calculates the accuracy of the predictions.
