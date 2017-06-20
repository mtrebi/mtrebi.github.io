---
layout: page
title: Resume
permalink: /resume/
---

## Table of contents
&nbsp;[Education](https://mtrebi.github.io/resume/#education)  <br/> 
&nbsp;[Work Experience](https://mtrebi.github.io/resume/#work-experience)  <br/> 
&nbsp;[Projects](https://mtrebi.github.io/resume/#projects)  <br/> 
&nbsp;[Skills](https://mtrebi.github.io/resume/#skills)  <br/> 
&nbsp;[Awards](https://mtrebi.github.io/resume/#awards)  <br/> 


## Education

- __First Class honours__ in the __MSc in Computer Science__ at the University of Girona, 2014-2016
- __B.S. in Computer Science__ at the University of Girona, 2010-2014
- __Technological High School__ at IES Santiago Sobrequés, 2008-2010

## Work Experience

#### Participant, Recurse Center
_New York, USA — Fall 2016_

[The Recurse Center](https://www.recurse.com/){:target="_blank"} is a free, self-directed, educational retreat for people who want to get better at programming, whether they’ve been coding for three decades or three months.

I joined RC with the idea of improving my C++ skills as well as gaining a low-level understanding of games and games engines. During the firsts weeks I mainly solved C++ exercices to warm up and get ready for the first project: A __software Ray Tracer__ implemented in the CPU completely from scratch and without any external library. This program is able to simulate colors using the Phong shading model, multiple shadows using shadow rays, light attenuation, reflections and refractions.

Because the previous project seemed very interesting for me, I decided to dig deeper in rendering so I started an __OpenGL__ project. This project allowed me to learn the basics of OpenGL by implementing different shading methods like Gouraud, Phong and Blinn-Phong shading and other features like normal and shadow mapping.

Finally, after a long talk about games and memory allocations with a fellow RCer I decided to implement __several memory allocation algorithms__ for games to test against malloc. I implemented a linear and a stack, a linear, a pool and a free list allocator. Then I benchmarked it's efficiency against malloc. In all cases, my algorithms were far better than malloc.

#### Back-end developer, Wikiloc Outdoor, S.L.
_Girona, Spain — February 2015 to March 2016_

Due to the growth that Wikiloc was experiencing, they hired me to work on some features to improve and optimize their online platform. 

During the firsts months I worked autonomously on a project to __automatize server provisioning__ using Ansible. The goal was to be able to replicate machines to easily create test environments and also to turn on new servers in case of failures.

After that, I closely worked with the strategy team to design and implement (autonomously too) __a real-time metrics dashboard__ using Graphite and Grafana. The idea was to centralize all useful data to metric in a set of dashboards that would help the strategy team to take decisions. In order to centralize all data, I created multiple Python scripts to query several databases (Redis, MySQL and PostreSQL).

Finally, during the lasts months at Wikiloc, in order to improve the search engine performance and to add more search features I designed and developed (again, autonomously) __a SolrCold prototype__ along with a Java driver to ease the creation of Solr search queries from the back-end. The final prototype was able to perform all previous search queries plus geo-spatial searches with a better performance and was fault tolerant. 

#### Back-end developer (intern), University of Girona
_Girona, Spain — October 2014 to November 2015_

This project called +CooVol  started as my Degree Final Project along with four other students by the initiative of the University of Girona. After finishing the project and winning the __best degree final project__ (see [Awards](https://mtrebi.github.io/resume/#awards)) the university hired us as interns to keep working in the project in order to create a final product.

At +CooVol each one of us had a single responsability although we all took part in the requirement analysis, design and decision making process. My specific responsability was to implement and test the __REST API__ to connect the front-end application with Cassandra, a distributed database. This REST API was developed using pioneer technologies with the goal to create a distributed system that was easily replicated to scale horizontally and without a single point of failure. To do so I used Scala as a programming language, Spray to create a non-blocking API and AKKA to implement a concurrent and distributed computation model based on actors that allowed me to exploit to the maximum the different threads and cores of the CPU. 

#### Full-stack developer (intern), Infogestió Girona S.L.
_Girona, Spain — November 2013 to May 2014_

During my time here I just worked as a __"code power"__ in an ERP application. When something was needed to be implemented, either a bug or a new feature, I was there to do it. I worked on both products of the company, the desktop product implemented using VB. 6 and the mobile product using native Android.

#### Back-end developer (intern), ANPRO 21
_Girona, Spain — July 2013 to September 2013_

During this internship I exclusively worked in one single project below the supervision of a PhD student. The company needed an algorithm to perform sentimeny analysis on news with a better accuracy and performance than the previous system. Using Lucene and Java, I developed a __sentiment analyzer algorithm__ that was fast enough for the needs of the company: more than 300.000 news were analyzed every day. In order improve its accuracy, I iterated over a secret formula provided by the company.

#### NXT developer (intern), University of Girona
_Girona, Spain — November 2012 to April 2013_

This was my first professional job as a software developer. During the firsts months I implemented __a static web page__ using PHP to allow people upload their solutions to published problems on the website.

After that I developed (on my own) __a cooperative navigation algorithm based on a Bug0 for NXT robots__ using LabView, a visual programming language for electrical and mechanical engineers. The different robots communicated through a TCP/IP program.


## My Projects

### Software rasterizer
C++ forward and deferred rasterizer with depth buffering, textures, normal maps, shadow mapping and phong shading in the CPU

### MSc. thesis: AI system to simulate combat behaviors in FPS
MSc. thesis: AI system for simulating combat behaviors in FPS games using Behavior Trees, visibility algorithms, and influence maps in Unreal Engine 4

### Thread Pool

Thread pool implemented in C++11 using Threads, Futures, Packaged Tasks and type deductions

### Degree final project: +CooVol

Degree final project: +CooVol, a scalable and high available web application using pioneer technologies.

### Bug0 navigation algorithm for Turtlebot 2.0

Bug0 navigation algorithm in Python to move a Turtlebot 2 from one point to another avoiding obstacles using the depth sensor of XBOX Kinect

### Android app

Unofficial android app to vote for the 9N Referendum in Catalonia and generate demographics statistics

## Skills

C++, 3D Maths, Graphics, Dynamic memory, Threading, Unreal Engine 4, Behavior Trees, Git, OpenGL, OOP, Software patterns, Python, Java, Databases

## Awards

- [‘Why didn’t I think of that?’ award](http://lj.libraryjournal.com/2016/12/technology/american-museum-of-natural-history-hackathon-tackles-21st-century-library-challenges/#_){:target="_blank"} in the ‘Hack the Stacks’ hackathon at the American Museum of Natural History (2016)
- [Best academic results](http://enginyeriainformatica.cat/?p=19213){:target="_blank"} in the MSc. in CS at the University of Girona (2016)
- [Best degree final project](http://www.diaridegirona.cat/cultura/2015/07/01/projecte-dordenacio-urbana-figueres-premi/732359.html){:target="_blank"} for +CooVol in the B.S. in CS at the University of Girona (2014)
- (Sports) 1st Prize in the Paleo Girona sports competition (2016)


