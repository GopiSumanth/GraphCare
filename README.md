
<h1 align="center">:microscope::stethoscope: GraphCare :robot::drop_of_blood:</h1>

<div align="center">

<img src="./logo.jpeg" width=250px height=225px/>

<br>

[![](https://img.shields.io/badge/Made_with-Python3-red?style=for-the-badge&logo=python)](https://www.python.org/ "Python3")
[![](https://img.shields.io/badge/Made_with-Keras-red?style=for-the-badge&logo=keras)](https://www.python.org/ "Python3")
[![](https://img.shields.io/badge/Made_with-Flask-red?style=for-the-badge&logo=flask)](https://flask.palletsprojects.com/en/1.1.x/)
[![](https://img.shields.io/badge/Made_with-Vue.js-red?style=for-the-badge&logo=vue.js)](https://www.vue.js/ "Vue.js")
[![](https://img.shields.io/badge/Made_with-Scikit_Learn-red?style=for-the-badge&logo=scikit-learn)](https://www.vue.js/ "Vue.js")
[![](https://img.shields.io/badge/Graph_Database-Neo4j-red?style=for-the-badge&logo=neo4j)](https://www.neo4j.com/ "Neo4j")

<br>

</div>


<h2>About:</h2>

GraphCare Bot is an AI-driven chatbot that will help you answer your basic medical queries, amidst the Covid-19 pandemic, where moving out to consult a doctor isn't a luxury anymore. The chatbot can respond to your medical queries only to the best of its **knowledge graph base**, so be mindful of that and always cross check the responses of GraphCare Bot with a medical professional!

<h2>Problem it solves:</h2>

Today, as the world faces the Covid-19 Pandemic, the world has entered lockdown mode, with partial lockdown varying across demography. People are confused about a lot of things and wish to consult medical professional advice. However, lockdown restricts this luxury and hence it becomes very convenient to have a chatbot that can answer your basic medical queries. 


GraphCare Bot can attempt to answer your queries about a limited set of diseases as of now. It can tell you about its symptoms, precaution and description of the disease. In case it can't answer your queries, or if you feel unsatisfied by the response, you are strongly adviced to consult a medical professional. Since this is a vanilla implementation of our chatbot, we strongly advice against blind faith in the responses.  

### How it works:

* [x] We have built a knowledge graph database of selected diseases, their symptoms, precautions and description. These relationships are stored in a Neo4j database, from where the results can be fetched. 
* [x] To understand user query, we make use of **Aho-Corasick** algorithm, to identify the patterns of type of question asked and fetch suitable results. 
* [x] Our Neo4j database is queried, and the  appropriate result is returned to the user.   
* [x] In case a question isn't found in our knowledge graph, we make use of question-answer pairs derived from [https://questiondoctors.com](https://questiondoctors.com) and use Question Similarity to see most probable question that matches the user query and return the answer correpsonding to that question.
* [x] For Question Similarity, we initially tried Bidirectional LSTM + Attention model, but we were having problems trying to use it as a predictor function. So, we now use Siamese-LSTM to make our predictions for most probable question. Dataset used was Quora-Question-Similarity, hosted on [Kaggle](https://www.kaggle.com/c/quora-question-pairs/data).
* [x] The result fetched through question-similarity method may not always be most apt, since a completely unrelated question, still may match with some queries from our dataset, based on similarity score. We look forward to improve this segment of our chatbot in future.



### Future scope of this project:

* [ ] Improve our Siamese LSTM model to perform better. 
* [ ] Try out other algorithms like XGBoost, etc. that did well in Quora challenge on Kaggle.
* [ ] We don't have a good medical dataset as of now for question similarity. So, we will look forward to contributing in this area, to improve our model.
* [ ] Handle non-medical queries or spam queries in a better way, i.e. provide better intent recognition and handling. 
* [ ] Integrate with RASA for better NLU, and move over current use of Aho-Corasick algorithm. 

### Tech Stack of this Project:

* Frontend: Vue.js
* Backend: Python3
* Framework: Flask
* Graph Database: Neo4j
* Machine Learning Model: Graph Knowledge Base, BiLSTM+Attention, Siamese-LSTM
* Libraries: Available in [requirements.txt](https://github.com/GopiSumanth/GraphCare/blob/master/requirements.txt).

### To run the project:

* [Fork](https://github.com/GopiSumanth/GraphCare) this Repository.
* cd into the directory in the terminal and run as:
  -`pip install -r requirements.txt`
* Install and run neo4j with instructions as mentioned [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-neo4j-on-ubuntu-20-04).

### Frontend and Backend
#### Neo4j
* Confirm that neo4j is running: `sudo service neo4j start`

#### API
* cd into `api/` folder and run   
	-`python3 build_medicalgraph.py`
* Run `export FLASK_APP=main.py`
* Run `flask run`

#### Frontend
* cd into `frontend/` folder and run `yarn serve`


#### This project still has scope of development, so you can also contribute to this Project as follows:
* [Fork](https://github.com/GopiSumanth/GraphCare) this Repository.
* Clone your Fork on a different branch:
	* `git clone -b <name-of-branch> https://github.com/GopiSumanth/GraphCare.git`
* After adding any feature:
	* Goto your fork and create a pull request.
	* We will test your modifications and merge changes.

This project was done `remotely with no pre-preparation in less than 40 hours under lockdown.`

---
<h3 align="center"><b>Developed with :heart: by Gopi Sumanth.</b></h1>
