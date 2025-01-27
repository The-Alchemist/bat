## Bro Analysis Tools (BAT) [![travis](https://travis-ci.org/SuperCowPowers/bat.svg?branch=master)](https://travis-ci.org/SuperCowPowers/bat) [![Coverage Status](https://coveralls.io/repos/github/SuperCowPowers/bat/badge.svg?branch=master)](https://coveralls.io/github/SuperCowPowers/bat?branch=master) [![supported-versions](https://img.shields.io/pypi/pyversions/bat.svg)](https://pypi.python.org/pypi/bat) [![license](https://img.shields.io/badge/License-Apache%202.0-green.svg)](https://choosealicense.com/licenses/apache-2.0)


The BAT Python package supports the processing and analysis of Bro data
with Pandas, scikit-learn, and Spark

## BroCon 2017 Presentation

Data Analysis, Machine Learning, Bro, and You!
([Video](https://www.youtube.com/watch?v=pG5lU9CLnIU))

## Why BAT?

Bro already has a flexible, powerful scripting language why should I use
BAT?

**Offloading:** Running complex tasks like statistics, state machines,
machine learning, etc.. should be offloaded from Bro so that Bro can
focus on the efficient processing of high volume network traffic.

**Data Analysis:** We have a large set of support classes that help
bridge from raw Bro data to packages like Pandas, scikit-learn, and
Spark. We also have example notebooks that show step-by-step how to get
from here to there.

### Example: Pull in Bro Logs as Python Dictionaries

```python
from bat import bro_log_reader
...
    # Run the bro reader on a given log file
    reader = bro_log_reader.BroLogReader('dhcp.log')
    for row in reader.readrows():
        pprint(row)
```

**Output:** Each row is a nice Python Dictionary with timestamps and
types properly converted.

    {'assigned_ip': '192.168.84.10',
    'id.orig_h': '192.168.84.10',
    'id.orig_p': 68,
    'id.resp_h': '192.168.84.1',
    'id.resp_p': 67,
    'lease_time': datetime.timedelta(49710, 23000),
    'mac': '00:20:18:eb:ca:54',
    'trans_id': 495764278,
    'ts': datetime.datetime(2012, 7, 20, 3, 14, 12, 219654),
    'uid': 'CJsdG95nCNF1RXuN5'}
    ...

### Example: Bro log to Pandas DataFrame (in one line of code)

```python
from bat.log_to_dataframe import LogToDataFrame
...
    # Create a Pandas dataframe from a Bro log
    bro_df = LogToDataFrame('/path/to/dns.log')

    # Print out the head of the dataframe
    print(bro_df.head())
```

**Output:** All the Bro log data is in a Pandas DataFrame with proper
types and timestamp as the index

```
                                                    query      id.orig_h  id.orig_p id.resp_h
ts
2013-09-15 17:44:27.631940                     guyspy.com  192.168.33.10       1030   4.2.2.3
2013-09-15 17:44:27.696869                 www.guyspy.com  192.168.33.10       1030   4.2.2.3
2013-09-15 17:44:28.060639   devrubn8mli40.cloudfront.net  192.168.33.10       1030   4.2.2.3
2013-09-15 17:44:28.141795  d31qbv1cthcecs.cloudfront.net  192.168.33.10       1030   4.2.2.3
2013-09-15 17:44:28.422704                crl.entrust.net  192.168.33.10       1030   4.2.2.3
```

## More Examples

-   Easy ingestion of any Bro Log into Python (dynamic tailing and log
    rotations are handled)
-   Bro Logs to Pandas Dataframes and Scikit-Learn
-   Dynamically monitor files.log and make VirusTotal Queries
-   Dynamically monitor http.log and show 'uncommon' User Agents
-   Running Yara Signatures on Extracted Files
-   Checking x509 Certificates
-   Anomaly Detection
-   See [BAT
    Examples](https://bat-tools.readthedocs.io/en/latest/examples.html)
    for more details.

## Analysis Notebooks

BAT enables the processing, analysis, and machine learning of realtime
data coming from Bro.

-   Bro to Scikit-Learn: [Bro to
    Scikit](https://nbviewer.jupyter.org/github/SuperCowPowers/bat/blob/master/notebooks/Bro_to_Scikit_Learn.ipynb)
-   Bro to Matplotlib: [Bro to
    Plot](https://nbviewer.jupyter.org/github/SuperCowPowers/bat/blob/master/notebooks/Bro_to_Plot.ipynb)
-   Bro to Parquet to Spark:
    [Bro-&gt;Parquet-&gt;Spark](https://nbviewer.jupyter.org/github/SuperCowPowers/bat/blob/master/notebooks/Bro_to_Parquet_to_Spark.ipynb)
-   Bro to Kafka to Spark:
    [Bro-&gt;Kafka-&gt;Spark](https://nbviewer.jupyter.org/github/SuperCowPowers/bat/blob/master/notebooks/Bro_to_Kafka_to_Spark.ipynb)
-   Clustering: Picking K (or not): [Clustering K
    Hyperparameter](https://nbviewer.jupyter.org/github/SuperCowPowers/bat/blob/master/notebooks/Clustering_Picking_K.ipynb)
-   Anomaly Detection Exploration: [Anomaly
    Detection](https://nbviewer.jupyter.org/github/SuperCowPowers/bat/blob/master/notebooks/Anomaly_Detection.ipynb)
-   Risky Domains Stats and Deployment: [Risky
    Domains](https://nbviewer.jupyter.org/github/SuperCowPowers/bat/blob/master/notebooks/Risky_Domains.ipynb)

Install
-------

    $ pip install bat

Documentation
-------------

[bat-tools.readthedocs.org](https://bat-tools.readthedocs.org/)

Thanks
------

-   The DummyEncoder is based on Tom Augspurger's great PyData Chicago
    2016 [Talk](https://youtu.be/KLPtEBokqQ0)

