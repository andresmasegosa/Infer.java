
<p align="center">
<img style="center" src="https://d3ansictanv2wj.cloudfront.net/PP-Figure.002-a4b8991929205945dbc850ce4dafc845.png" width="500">
</p>


# Project Scope

In this open source software project we aim to develop a probabilistic programming language that supports a distributed computational model like MapReduce. This language will be implemented as a Java API, so that the user can mix probabilistic and non-probabilistic code in the application, and will be integrated into Spark and Flink, two platforms for big data processing. This programming language will be developed as an open software project freely available to the scientific and professional community interested in the use of machine learning techniques (ML) for big data problems.


ML is a field of research that is widely established providing many solutions to major problems of society such as web search engines, genetic data analysis, self-driven cars, etc. The current availability by governments, institutions and corporations of large volumes of data is accelerating the development of such applications. However, developing a ML algorithm that fits a specific problem requires of programmers with expertise in various fields such as statistics, probabilistic modeling, optimization algorithms, etc. This translates, in most of the cases, to the need of highly qualified people who either are not available in the labor market or represent a high cost for the project. In the case of dealing with large volumes of data, these problems are exacerbated since it also requires that the designed ML algorithm to be parallelizable and scalable. All these factors are weighing on the process of ML applications development. So, usually, only large corporations have the technical and financial capacity to carry them out.


<p align="center">
<img style="center" src="http://www.visualisingdata.com/blog/wp-content/uploads/2010/03/DataDeluge.png" width="200">
</p>


For these reasons, the prestigious US Defense Advanced Research Projects Agency (DARPA) is currently funding a major programme in the area of probabilistic programming languages (PPLs). According to this agency, the PPLs could offer a solution to all these problems, since they allow to separate the model specification from the learning algorithm. For many experts, the PPLs could revolutionize the field of ML and scientific modeling in the same way that the appearance of the general-purpose programming languages revolutionized the field of software development fifty years ago, by freeing developers from the need to know the details of the hardware on which the program was running.

One of the main problems still unresolved in this field is the definition of PPLs with an inference engine that is scalable and has the capacity to process large volumes of data. In this project we aim to extend and adapt the developments of the European research project AMIDST (FP7-ICT-619 209) to achieve this goal. The AMIDST project, where both the main researcher and the supervisor are involved, is based on the development of scalable inference and learning algorithms for probabilistic graphical models, in the context of massive data streams. The project INFER.java aims to define a PPL whose programs can be compiled to a probabilistic graphical model and to build a scalable inference engine for this PPL on top of the AMIDST's algorithms.


# Why PPLs?

Machine learning (ML) [1,2] is, at present, a fundamental part of many artificial intelligence techniques [3]. According to this field of research, it is much more effective to develop methods that allow machines to learn to perform tasks on their own, than to program them specifically for each one. This idea has been a real revolution in many other fields of research such as natural language processing [4], predictive analysis [2], cybersecurity [5], bioinformatics [6], and so on. In addition, it has allowed the development of highly innovative applications such as self-employed cars [7], image search [8], junk e-mail filters [9], recommendation systems [10], etc.

One of the main catalysts of this technology has been the current availability by governments, institutions and corporations of large data volumes [11]. This has allowed ML algorithms to have a greater predictive and modeling capacity [10].

Another reason is the availability of open-source platforms that allow a low-cost cluster of computers to be controlled in a transparent and comparatively simple manner using data replication and hardware failure resistance techniques [12]. This has greatly reduced the cost of storing and processing large volumes of data. Most of these platforms have been developed in the last decade and come from the United States. Those based on the MapReduce programming model [12] are those that are currently being used more and have a higher level of development. Notably Hadoop [13], an open source version of the original model submitted by Google in 2004 [12]; Spark [14] (http://spark.apache.org/), a more modern and recent platform with greater processing capacity, which is being widely adopted in the business and scientific world; and Flink [15] (https://flink.apache.org), probably the only relevant initiative in Europe right now, which is receiving a lot of attention from the free software community and which is the result of several research projects, including an FP7 framework project (http://stratosphere.eu). All these technological advances have greatly accelerated the development of ML applications over large volumes of data.


<p align="center">
<img style="center" src="https://image.slidesharecdn.com/ismdatascientistfinal2-150323081840-conversion-gate01/95/take-aways-from-data-scientist-the-sexiest-job-of-the-21st-century-6-638.jpg?cb=1427098883" width="400">
</p>

Unfortunately, for a company or an institution, the development of ML models specific to their problems requires enormous effort, mainly for the following reasons [16,17]:

* **It is necessary to have highly qualified experts**. Develop ML models requires knowledge in various fields such as statistics, probabilistic modeling, optimization algorithms, specialized software, parallel and distributed computing, etc.
* **Programming a ML model is a complex task where many problems are intermingled**, such as the difficulty of testing the correct functioning of the implementation (a ML model is approximate in nature and the optimal response is unknown in most cases) and the shortage of reusable tools. For this reason, ML applications are often created from scratch.
* **It is difficult to find the ML model most suitable for an application**. The chosen models tend to have limited expressivity (ie, linear or non-linear, probabilistic or non-probabilistic approach, ...). In addition, the code that implements the model usually inherits these limitations, making it difficult to inspect, maintain or improve. This also makes it complex to integrate the expert knowledge about the domain of the application. As a result, applications often use generic modeling hypotheses instead of being specific to the application domain.


All these factors are weighing the development of ML applications and making it only available for large corporations that have the technical and financial capacity to carry them out.

For all these reasons, the prestigious American Agency for Advanced Research Projects (DARPA) has today opened a research funding program in the area of **probabilistic programming languages** (PPLs)[16]. According to this agency, PPLs could offer a solution to all these problems.


#What's a PPL?

Broadly speaking, a PPL is like a standard programming language but has two added constructs [16]: (1) the ability to sample random values from a random variable, and (2) the ability to condition the value of a random variable of the program through observations of other random variables. In this way, a program written with a PPL is able to define a probabilistic model [2]. Models in areas as diverse as artificial vision, coding theory, cryptographic protocols and biology can be expressed using PPLs [1,2,17].


<p align="center">
<img style="center" src="https://image.slidesharecdn.com/probprogramming-151219161159/95/probabilistic-programming-in-python-5-638.jpg?cb=1450541578" width="200">
</p>


The central element of a PPL is its inference engine [16], which allows to explicitly query the probability distribution specified in the probabilistic program. Depending on the application, the output of the inference engine may be the expected value of a function with respect to this probability distribution, the mode of the distribution, or simply a set of sampled values from the distribution.

In this way, a programmer can directly construct a ML model of the phenomenon of interest using the appropriate PPL commands. When the model depends on an unknown quantity, developers introduce a random variable that can be associated with a wide range of probability distributions [2]. 

Consider the following example. A programmer has access to a flow of measurements of various temperature and smoke sensors in a given area and wants to develop a program that alerts the presence of a fire based on these measurements. The programmer has the following expert knowledge:

* He knows that the presence of a fire is a rare and very unusual event.
* He knows that if there is a fire, the temperature will rise and smoke will occur, and that this situation is going to be captured by the sensors.

* He also knows that the sensors are not accurate and may contain noise in their measurements.

* It is not clear what the temperature range is when there is no fire, since a requirement is that the software is valid for different geographical areas with different climates.

These four elements of expert knowledge could be modeled, respectively, by a probabilistic model as follows:

* Fire as a rare element: Using a binary variable with a Beta distribution as a priori distribution that expresses that the probability that this binary variable is active is quite low.

* Increased temperature and smoke as signs of fire: These relationships can be defined through the use of graphic models with qualitative links [18,19].

* Noise in measurements: This is a standard relationship that can be modeled by introducing a standard noise model for Gaussian and binary variables, respectively, where the noise level is modeled with another hidden transparent variable to the programmer [20].


