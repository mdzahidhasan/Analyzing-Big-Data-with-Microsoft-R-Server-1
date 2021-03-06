---
layout: page
title: Overview of RevoScaleR
---
# Deploying and scaling

Once a model is built, we're usually interested in using it to make predictions on future data, a process sometimes referred to as **scoring**. This is not very different from how we used the model in the last section to make predictions on the test data using the `rxPredict` function. But future data may be sitting in a different environment from the one used to develop the model. 

For example, let's say we want to regularly score new data as it arrives in a SQL Server. Without `RevoScaleR`, we may need to bring the new data out of the SQL Server (e.g. as a flat file or using an ODBC connection) into a machine with R installed. We would then load the data in R to score it and send the scores back to SQL Server. Moving data around is both inefficient and can often breaks security protocols around data governance. Additionally, if the data we are trying to score is too large to fit in the R session, we would also have to perform this process peace-wise using a chunk of the data each time. Microsoft R Server can eliminate all three problems by scoring new data in the machine the data is already sitting in. It uses the efficient `rxPredict` function which can score data without having to load it in an R session in its entirety.

Because `RevoScaleR` comes with parallel modeling and machine learning algorithms, we can also use them to develop models on much larger datasets sitting in SQL Server or on HDFS. This narrows the gap between the development and production environment considerably.
