---
title: "About Me"
description: "Curriculum Vitae"
date: "2022-05-10"
slug: "about-me"
menu:
  main:
    weight: -90
    params:
      icon: user
---

# Education

- M.S. in Computer Science, Rice University, August 2022-Dec 2023 | GPA: 3.93/4.0
- B.S. in Computer Science, Wuhan University, September 2018-June 2022 | GPA: 3.69/4.0

# Work Experience

- **Android & Front-end Engineering Intern**, Sensetime, _September 2021-July 2022_

  - Oversaw and designed a mobile meeting room appointment system using **React** and **TypeScript**,  which became one of the most used enterprise applications within the company and with 2 clients.
  - Conceptualized and developed Elevator Visualization Platform and Big Intelligent Screen with **Kotlin**, making it easier for users to look up elevator status and meeting room reservation status.
  - Created and introduced logging module in Pyramid SDK; maintainers and developers could view device logs online rather than ADB and was able to store persistently.
  - Contributed to design of authorization module in Pyramid SDK with **Java** and ensured only authorized devices could access internal data.
  
- **Computer Graphics Engineering Intern**, CBIM, _August 2021-September 2021_

  - Programmed water graphics (surface, body and waves) and water bank with **Vulkan** and **C++** for architecture designers; beta tested for 10K users.
  - Implemented water real-time information synchronization with front-end team

- **Front-end Engineering Intern**, CBIM, _December 2020-January 2021_
  - Developed a website using **Vue.js** and Vue-Router to interact with the REST API.
  - Built the layout of website with **ElementUI** to show widgets and visualized project information in a dynamic map with **LayerUI.js**.

# Research Experience

- **Researcher**, WHU IR LAB (Advised by Chenliang Li), _September 2020-June 2021_
  - Tried to intergrade Entity information in Embedding Layer using Named Entity Information to improve the model information retrieval performance on SQuAD 2.0
  - Explored cross view training by training the origin model and summary model together and assembling their result to improve model performance
  - Explored Linear Complexity Attention mechanism with minimal loss on accuracy performance while time consumption reduced by 50%
  - Used Contrast Learning and improved Chinese BERT Classification Model on debate dataset by 16% comparing to baseline BERT
- **Researcher**, SYSU (Advised by Ruixuan Wang), _June 2021-November 2021_
  - Explored feature map smooth mapping with attention information
  - Visualized model architecture and experiment results

# Projects

## Instant

Golang, MySQL, Gin, Vue, TypeScript _March 2022-Present_, [GitHub](https://github.com/ZYChimne/instant-go)

- Designed and implemented a **Fan Out on Write** inbox using **Go** and **MongoDB** to retrieve user feed, decreasing time to fetch data comparing to Fan out on Read by over 3 times.
- Designed and built hierarchical web session cache system with **Redis** and **MongoDB**; over 10 times faster than retrieving data from database directly.
- Launched instant messaging system with **Web Socket**.
- Managed a fast web interface with **Vue 3**, **TypeScript**, and **Vite 3**; achieved 98 on performance in lighthouse on the main page.

## macOS in TypeScript

React, SCSS, Animation, Typescript, _November 2021-May 2022_, [GitHub](https://github.com/ZYChimne/macos-in-typescript)

- Used **React.js** for state management and lazy initialization to achieve better performance.
- Built components from scratch, such as switch, image previewer, carousal and pop-over
- Developed **SCSS** and canvas animations to make the interface friendly and smooth
- Achieved 95 (Performance), 100 (Accessibility), 100 (Best Practice), 100 (SEO) in Chrome lighthouse

## CyDrive Windows Client

C#, .Net Framework, WPF, XAML, _September 2021-November 2021_, [GitHub](https://github.com/ZYChimne/CyDrive-windows)

- Implemented all page layouts and set up navigation logic of the application
- Page design was completely grid-based, showing great flexibility and robustness on all kinds of devices
- Built basic functions including login/out, sign up, new/delete, rename, multi-select, upload/download and etc.

## Music Player

Kotlin, Android, _June 2021-August 2021_

- Implemented MVVM design pattern, updating data by Live Data and Data Binding
- Built a database to keep the user information and recover them on Application opens
- Used Repository to interact with the database to implement querying and search data of the database
- Integrated RxJava to check whether permission is granted and notify the activity
- Used ContentResolver to query the MP3 file in the device and filter the media file whose length is shorter than two minutes
- Built with Launch and Dispatch for multi-thread to improve application performance and thread safety when updating notification and obtaining permissions
- Implemented module development pattern by dividing the music player model into permissionModule, mediaModule, repositoryModule and etc.

## Ai-Debater Classification Model

Python, Pytorch, Bert, Transformers, _June 2021_, [GitHub](https://github.com/ZYChimne/AI-Debater)

- Used adapted contrast learning and smoothed dropout strategies and evaluate our method on Bert and variances of Bert
- Improved model performance from 78% to 92% in original baseline test setting and from 74% to 80.3% in test dataset setting

## Dropout Against Deep Leakage from Gradients

Python, Pytorch, _June 2021_

- Re-implemented Deep Leakage from Gradients (NeurIPS2019) and evaluate the data leaking problem on commonly used datasets
- Explored new ways to prevent detecting and recovering original raw data, and eventually used Dropout to prevent Deep Leakage from Gradients converges to original local data with minimal model performance loss

## Cminus Compiler

C, Flex, Linux, Bison, Cmake, Linux, _March 2021-June 2021_, [GitHub](https://github.com/ZYChimne/CMINUS-Compiler)

- Designed rules and regular expressions for lexical analysis and syntax analysis to generate Abstract Syntax Tree and calculate expression results
- Implemented exception analysis to find out and highlight error types locations, and details in code
- Built regular expression match patterns to support float in scientific notation and integers in binary, octonary and hexadecimal

## Feature Cross Recommender with Attention

Python, Tensorflow, DCN, _March 2021_, [GitHub](<(https://github.com/ZYChimne/Recommender-with-Attention)>)

- Re-implemented Deep & Cross Network on MovieLens, referring to Deep & Cross Network for Ad Click Predictions (KDD2017)
- Explored ways of feature smooth and adapt matrix production in the end, which is able to reduce the parameters and inference time of the model, while increasing its performance by reducing RMSE by 0.004

## Bert in Pytorch

Python, Pytorch, Transformers, Bert, _March 2021_

- Implemented a Bidirectional Encoder Representations from Transformers in Pytorch, which is able to run a variety of tasks, including mask language modeling and question answering

## Multi-elevator Control System

C, AT89C52, Keil, Proteus, _September 2020-December 2020_, [GitHub](https://github.com/ZYChimne/MultiElevator)

- Designed circuit blueprint connecting AT89C52 and devices
- Designed multi-elevator control system which is able to assign the most appropriate one of the two elevators in a four-floor building

## Question Answering System

Full-stack, Java, SpringBoot, Bootstrap, Thymeleaf, JPA, _September 2020-December 2020_, [GitHub](https://github.com/ZYChimne/MRCWeb)

- Developed a MVC application with SpringBoot and Access MYSQL Database with JPA
- Designed and implemented grid-based pages with Bootstrap that were adaptive to both desktop and mobile devices
- Used Python and Transformers to build Bert-based information retrieval model

## MIPS Multi-cycle Central Processing Unit

Verilog HDL, Modelsim, _March 2020-June 2020_, [GitHub](https://github.com/ZYChimne/CPU-implement)

- Built a CPU supporting 26 MIPS instructions, including add, sub, sw, lw, beq, bne, j, jr, jal
- Implemented prediction unit so that pipeline did not have to be stalled
- Designed a forward unit and it was able to forward data to the next unit to improve performance
- Developed a hazard unit that was able to flush or stall pipeline to ensure that every instruction was executed properly

## I'm Hungry

Swift, iOS, _March 2020-June 2020_, [GitHub](https://github.com/ZYChimne/I-m-Hungry)

- A restaurant order application
- Used SQLite to store order data and restaurant data

## FTP Client

C++, Qt, Websocket, Multithread, _July 2019-August 2019_

- Implemented client user interface and logics using multi-thread and event to ensure the safety of UI thread
- Developed download function supporting pause and resume using websocket

## Draw and Guess

Kotlin, Android, _January 2019-February 2019_

- Used MVVM design pattern, updating data by Live Data and Data Binding
- Used ViewModelFactory as the constructor for ViewModel with Parameters

## Convolution Neural Network in Numpy

Python, Numpy, _September 2018-December 2018_

- Implemented a Convolution Neural Network using Numpy to calculate matrix production and back propagation
- Achieved an accuracy of 97% on MNIST Dataset
- Explored different settings of batch normalization and learning rate

# Standard Test Scores

- **IELTS: 7.5** (Listening: 8.5, Reading: 8.5, Writing: 7.0, Speaking: 6.0)
- **GRE: 321+** (Verbal Reasoning: 151, Quantitative Reasoning: 170, Analytical Writing: 4)
- **CET-6: 594** (Listening: 208, Reading: 224, Writing: 162)
- **CET-4: 665** (Listening: 249, Reading: 249, Writing: 167)

# Skills

- **Programing:** (C++, Golang, Python, Java, TypeScript, Kotlin, C#, SQL)
- **Front-end Development:** (Vue.js, React.js, Redux, Next.js, Node.js, Webpack, Vite, Element-UI, AntDesign)
- **Libraries:** (SpringBoot, Redis, MongoDB, MySQL, Pytorch, Tensorflow, Matplotlib, Numpy, Pandas)
- **Tools:** (Visual Code, Visual Studio, IDEA, Android Studio)
- **Computer Vision:** (Image Classification, Semantic Segmentation, Incremental Learning)
- **Natural Language Processing:** (Transformers, Sentiment Analysis, Machine Reading Comprehension)
- **Recommenders:** (Feature Cross Learning, Knowledge Graph)
- **Computer Graphics:** (Vulkan, OpenGL)
- **Mobile Development** (Android, iOS)

# Experiences

- Cambridge Winter Program, _January 2019-February 2019_
