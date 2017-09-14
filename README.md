# Logstash tutorial

The `tutorial` folder contains a fully working example that I use in the presentation of this pipeline: ~insert_link here later~, you can use it to play around and familiarize yourself with the ELK stack and it contains as well an excercice to test your comprehension of Logstash.

We assume that you already have installed:

[Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup.html)

[Logstash](https://www.elastic.co/guide/en/logstash/current/installing-logstash.html)

This tutorial allow you to put in application your knowledge of Logstash in order to create your own pipeline for some random tweets and adding in the pipeline some Machine Learning. First of all if it's not already done:

    git clone https://github.com/melvynator/ELK_twitter.git
    cd Logstash_tutorial
    virtualenv -p python3 venv
    source venv/bin/activate

In the file `Logstash_tutorial/tutorial/ml-example/tutorial-ml.conf` please change: `/YOUR/ABSOLUTE/PATH/TO/YOUR/FILE/fake_tweet_sample.txt` by the real absolute path to this file.

Now have a look to the file: `Logstash_tutorial/tutorial/ml-example/readme.txt`

The first thing you should do is to design your API in the file: `Logstash_tutorial/tutorial/ml-example/api.py`

To let you focus on the comprehension of Logstash we already have created the Machine learning model and the vectorizer you just have to load them and return the prediction. If you are stuck feel free to have a look to this file: https://github.com/melvynator/ELK_twitter/blob/master/src/sentiment_service/sentiment_server.py it will give you some hints.

Once your API has been built you should start your server by running the following in your terminal:

`python api.py`

Now you can finally focus on building the filters in the logstash configuration file: `Logstash_tutorial/tutorial/ml-example/tutorial-ml.conf`

You can try your pipeline by typing in your terminal the following:

`logstash --debug -f tutorial-ml.conf`
