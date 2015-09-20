Ship Data Science
=================

@IanOzsvald
ian.osvald@modelinsight.io

Company "elevate" - match CVs to jobs

Extract data

* tools: sql, elasticsearch, numpy, pandas, ...

Visualising data

* most data is boring
* requires human curation + detective skills to get good stuff
* prob needs engineer/researcher and business
* tools - bokeh ...

Extracting data from binary files

* PDF/PNG data
* tools - textract, Apache Tika, Sovren
* this might take months!

Augmenting data

* identify people, sentiment
* tools - opendata, datasift, NLTK, alchemyapi

machine learning

* tools: PyMC, scikit learn, statsmodels, sparkit-learn
* deep learning: theano, caffe
* text: spaCy, NTLK

Delivery - Keep it simple (stupid)

* we're prob not publishing the best result
* debuggability is key
* "cult of the imperfect" Watson-Watt
* dumb models + clean data beat other combinations

Don't Kill It!

* your data is missing, poor, it lies

  * missing data
  * log everything - eg segment.io
  * make dat quality tools & reports
  * Note! More data -> desynchronisation - BBAAADDD!

* R&D != Engineering

  * discovery based, iterative, learn from both success and failure

Internal deployment

* CSVs, reports
* database updates
* IPython Notebook (though note, not secure)
* Bokeh

Deploying live systems

* Spyre (locked down cf. ipython notebook)
* Microservices - Docker, Amazon ECS, Flask + Swagger
