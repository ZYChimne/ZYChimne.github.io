---
title: 'About Me'
description: 'Curriculum Vitae'
# date: "2022-05-10"
slug: 'about-me'
menu:
  main:
    weight: -90
    params:
      icon: user
---

# Education

- MS in Computer Science, Rice University, Aug 2022-Dec 2023 | GPA: 3.84/4.0
- BS in Computer Science, Wuhan University, Sept 2018-Jun 2022 | GPA: 3.69/4.0

# Work Experience

- **Teyvat Traveler**, Genshin Impact, _Sept 2021-Present_

  - Explored the seven nations of Teyvat, including Mondstadt, Liyue, Inazuma, Sumeru and Fontaine, and solved numerous puzzles and challenges along the way.
  - Battled against powerful enemies, including the Abyss Order, Fatui Harbingers, and other dangerous foes.
  - Collected and upgraded a wide variety of characters and weapons, and learned to use them effectively in combat.
  - Completed numerous quests and side missions, helping people and solving problems all over Teyvat.
  - Learned about the history and culture of each nation, and made many new friends along the way.

- **Web Developer**, Meituan, _Feb 2024-Present_

  - Develop and maintain product pages using WeChat Mini Program and TypeScript, implementing features that enhance user interaction and conversion rates.
  - Optimize frontend performance through unifying render process, reducing initial load time by 50%.
  - Conduct A/B testing and analyze user behavior metrics to drive data-informed UI/UX improvements.
  - Maintain and improve code quality through TypeScript type safety, unit testing, and code reviews.

- **Full Stack Engineering Intern**, Alibaba Cloud, _May 2023-Aug 2023_

  - Designed and developed an AI Question Answering System using LLMs, **Redis**, **PostgreSQL**, and **GRPC**, deployed in Apache RocketMQ Chinese Forum and Alibaba Cloud Developer Forum.
  - Created an [AI-native App Management System](https://github.com/devsapp/agentcraft) with **Python** and **NextJS**, with over 1K daily API calls in August 2023 and a growing user base.
  - Developed Serverless deployment templates for LLM-related applications, utilized by over 10K developers on Function Computing.
  - Contributed to the development of Kafka Console using **React**.

- **Android & Front-end Engineering Intern**, Sensetime, _Sept 2021-July 2022_

  - Led a mobile meeting room appointment system using **React** and **TypeScript**, becoming a widely adopted enterprise solution with 2 clients.
  - Developed an Elevator Visualization Platform and Big Intelligent Screen using **Kotlin**, improving elevator and meeting room status accessibility.
  - Introduced a logging module in Pyramid SDK, enabling online device log viewing and persistent storage, reducing reliance on Android Debug Bridge.
  - Contributed to the design of an authorization module in Pyramid SDK using **Java**, enhancing data security by limiting access to authorized devices.
  
- **Computer Graphics Engineering Intern**, CBIM, _Aug 2021-Sept 2021_

  - Developed water graphics and bank features using **Vulkan** and **C++** for architecture designers, undergoing successful beta testing with 10K users.
  - Achieved real-time water information synchronization with the web development team.

- **Front-end Engineering Intern**, CBIM, _Dec 2020-Jan 2021_
  - Created a website using **Vue.js** and **Vue-Router** for REST API interaction.
  - Designed the website layout using **ElementUI** to display widgets and visualized project information dynamically using **LayerUI.js**.

# Research Experience

- **Researcher**, SYSU (Advised by Ruixuan Wang), _Jun 2021-Nov 2021_
  - Investigated feature map smooth mapping with attention information.
  - Created visual representations of model architecture and experimental results.

- **Researcher**, WHU IR LAB (Advised by Chenliang Li), _Sept 2020-Jun 2021_
  - Enhanced model information retrieval in SQuAD 2.0 by integrating named entity information into the Embedding Layer.
  - Improved model performance by exploring cross-view training, assembling the origin model and summary model.
  - Achieved a 50% reduction in time consumption with minimal loss in accuracy by implementing the Linear Complexity Attention mechanism.
  - Enhanced a Chinese BERT Classification Model for debate datasets by 16% using Contrast Learning compared to the baseline BERT.

# Projects

## Instant | Social Media Platform

Golang, MongoDB, Gin, TypeScript, NextJS _Mar 2022-Present_, [github/instant-go](https://github.com/ZYChimne/instant-go)

- Developed a **Fan Out on Write** inbox in **Go** and **PostgreSQL**, reducing data retrieval time by over 3 times compared to Fan Out on Read.
- Created an efficient hierarchical web session cache system using **Redis** and **Local Cache**, delivering data retrieval speeds over 10 times faster than direct database access.
- Implemented a real-time messaging system using **HTTP 2**.
- Designed a high-performance web interface with **NextJS**, **TypeScript**, and **React**, achieving a 98 Lighthouse performance score.

## AgentCraft | AI-Native App Management System Using LLM

Python, FastAPI, PostgreSQL, Redis, _May 2023- Aug 2023, [github/agentcraft](https://github.com/devsapp/agentcraft)

- Designed and deployed a system with 1K daily API calls on Alibaba Cloud (Aug 2023).
- Enabled support for multiple LLMs, including native OpenAI API and Huggingface Models with [adapters](https://github.com/devsapp/fc-llm-image-source).
- Implemented text segmentation and vectorization using a [custom **SentenceTransformers** service](https://github.com/devsapp/fc-embedding-api) and **PostgreSQL**.
- Developed a distributed LLM cache and history system using **Redis**.

## macOS in TypeScript | Web Page with MacOS Interface

React, SCSS, Animation, Typescript, _Nov 2021-May 2022_, [github/macos-in-typescript](https://github.com/ZYChimne/macos-in-typescript)

- Utilized **React.js** for efficient state management and lazy initialization to enhance performance.
- Designed custom components including switches, image previewers, carousels, and pop-overs.
- Implemented **SCSS** and canvas animations for a user-friendly and smooth interface.
- Achieved outstanding Chrome Lighthouse scores: 95 for Performance, 100 for Accessibility, 100 for Best Practices, and 100 for SEO.

## CyDrive Windows Client | Cloud Drive Windows Client

C#, .Net Framework, WPF, XAML, _Sept 2021-Nov 2021_, [github/CyDrive-windows](https://github.com/ZYChimne/CyDrive-windows)

- Created page layouts and navigation logic for the application.
- Utilized a flexible grid-based design for optimal performance on various devices.
- Developed essential features such as user authentication, file management (new/delete/rename), multi-select, and file operations (upload/download).

## AI-Debater Classification Model | Text Classification Model

Python, Pytorch, Bert, Transformers, _Jun 2021_, [github/AI-Debater](https://github.com/ZYChimne/AI-Debater)

- Employed adapted contrast learning and smoothed dropout techniques to enhance Bert and its variants.
- Achieved significant performance improvements, raising accuracy from 78% to 92% in the original baseline test and from 74% to 80.3% in the test dataset setting.

## Dropout Against Deep Leakage from Gradients | Research

Python, Pytorch, _Jun 2021_

- Re-implemented Deep Leakage from Gradients (NeurIPS2019) and assessed data leakage issues on standard datasets.
- Innovated methods to thwart the detection and recovery of raw data, successfully utilizing Dropout to prevent Deep Leakage from Gradients from converging to original local data with minimal model performance loss.

## Cminus Compiler | Subset of _C_ Compiler

C, Flex, Linux, Bison, Cmake, Linux, _Mar 2021-Jun 2021_, [github/CMINUS-Compiler](https://github.com/ZYChimne/CMINUS-Compiler)

- Created rules and regular expressions for lexical and syntax analysis, generating Abstract Syntax Trees and computing expressions.
- Implemented error analysis, pinpointing error types, locations, and details in code.
- Developed regex patterns for handling scientific notation floats and binary, octal, and hexadecimal integers.

## Feature Cross Recommender with Attention | Research

Python, Tensorflow, DCN, _Mar 2021_, [github/Recommender-with-Attention](<(https://github.com/ZYChimne/Recommender-with-Attention)>)

- Re-implemented Deep & Cross Network on MovieLens, following the approach from Deep & Cross Network for Ad Click Predictions (KDD2017).
- Enhanced model performance by optimizing feature smoothing and adapting matrix production, reducing parameters, inference time, and RMSE by 0.004.

## Bert in Pytorch | Research

Python, Pytorch, Transformers, Bert, _Mar 2021_

- Developed a versatile Bidirectional Encoder Representations from Transformers (BERT) model in PyTorch, supporting tasks such as masked language modeling and question answering.

## Multi-elevator Control System | Embedding System

C, AT89C52, Keil, Proteus, _Sept 2020-Dec 2020_, [github/MultiElevator](https://github.com/ZYChimne/MultiElevator)

- Created a circuit blueprint for connecting AT89C52 microcontroller with various devices.
- Designed a multi-elevator control system for efficient elevator assignment in a four-floor building, optimizing passenger flow.

## Question Answering System | REST API

Full-stack, Java, SpringBoot, Bootstrap, Thymeleaf, JPA, _Sept 2020-Dec 2020_, [github/MRCWeb](https://github.com/ZYChimne/MRCWeb)

- Created an MVC application using SpringBoot, connecting to a MySQL database through JPA.
- Designed responsive grid-based pages with Bootstrap for desktop and mobile compatibility.
- Developed a Bert-based information retrieval model using Python and Transformers.

## MIPS Multi-cycle Central Processing Unit | CPU

Verilog HDL, Modelsim, _Mar 2020-Jun 2020_, [github/CPU-implement](https://github.com/ZYChimne/CPU-implement)

- Constructed a CPU supporting 26 MIPS instructions (e.g., add, sub, sw, lw, beq, bne, j, jr, jal).
- Implemented a prediction unit to prevent pipeline stalls.
- Designed a forward unit for data forwarding, enhancing performance.
- Developed a hazard unit to ensure proper execution of all instructions by flushing or stalling the pipeline as needed.

## I'm Hungry | Restaurant Order Placement Application

Swift, iOS, _Mar 2020-Jun 2020_, [github/I-m-Hungry](https://github.com/ZYChimne/I-m-Hungry)

- Used SQLite for data management.

## FTP Client

C++, Qt, Websocket, Multithread, _July 2019-Aug 2019_

- Created a client user interface with thread management for UI safety.
- Designed a download function with WebSocket support, enabling pause and resume capabilities.

## Draw and Guess | Android Application

Kotlin, Android, _Jan 2019-Feb 2019_

- Applied MVVM design pattern with LiveData and Data Binding for data updates.
- Utilized ViewModelFactory to construct ViewModels with parameters.

## Convolution Neural Network in Numpy

Python, Numpy, _Sept 2018-Dec 2018_

- Created a Convolutional Neural Network (CNN) using Numpy for matrix operations and backpropagation.
- Attained a 97% accuracy on the MNIST Dataset.
- Investigated various batch normalization and learning rate settings for optimization.

# Standard Test Scores

- **IELTS: 7.5** (Listening: 8.5, Reading: 8.5, Writing: 7.0, Speaking: 6.0)
- **GRE: 321+** (Verbal Reasoning: 151, Quantitative Reasoning: 170, Analytical Writing: 4)
- **CET-6: 594** (Listening: 208, Reading: 224, Writing: 162)
- **CET-4: 665** (Listening: 249, Reading: 249, Writing: 167)

# Skills

- **Programming Language:** (C++, Golang, Python, Java, TypeScript, Kotlin, SQL)
- **Databases:** (MySQL, MongoDB, PostgreSQL, Redis)
- **Front-end Development:** (Vue.js, React.js, Next.js, Node.js, Webpack, Vite, MUI, Element-UI, AntDesign)
- **Backend Development:** (Gin, FastAPI, SpringBoot)
- **AI Frameworks:** (Pytorch, Tensorflow, Transformers, Matplotlib, Numpy, Pandas)
- **Computer Vision:** (Image Classification, Semantic Segmentation, Incremental Learning)
- **Natural Language Processing:** (Transformers, Sentiment Analysis, Machine Reading Comprehension)
- **Recommenders:** (Feature Cross Learning, Knowledge Graph)

# Experiences

- Cambridge Winter Program, _Jan 2019-Feb 2019_
