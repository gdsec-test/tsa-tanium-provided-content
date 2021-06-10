# Leveraging Recorder DB Stats Content for Tuning Recorder and Index
## Introduction
**Recorder DB Stats** is Tanium Custom Content that allows sensors to be used to determine the current state of the Recorder Databases in the environment. The provided XML file must be signed and imported into Tanium Production environments. Once imported, the content can be used.

## Table of Contents
- [Leveraging Recorder DB Stats Content for Tuning Recorder and Index](#leveraging-recorder-db-stats-content-for-tuning-recorder-and-index)
  - [Introduction](#introduction)
  - [Table of Contents](#table-of-contents)
  - [Recorder DB Stats – Overview](#recorder-db-stats--overview)
  - [Recorder DB Stats – Distribution](#recorder-db-stats--distribution)
  - [Recorder DB Stats – [File, Network, Registry, Process]](#recorder-db-stats--file-network-registry-process)
  - [Tuning the Recorder](#tuning-the-recorder)
  - [Tuning Index](#tuning-index)
  - [Support](#support)

## Recorder DB Stats – Overview
The `Recorder DB Stats – Overview` sensor shows some basic information about the use of the Recorder database. If Recorder is functioning, the first column will be a 0. The next column informs you of how much information is being retained, and then the size of the DBs is in the next column. This can be used to identify machines that require tuning.

## Recorder DB Stats – Distribution 
The `Recorder DB Stats – Distribution` sensor shows the amount of space in the local Recorder rounded to the nearest 5%. Note that because of rounding errors, you can have less than 100% in a row. This will tell you which type event takes the most database space, and may require tuning.

## Recorder DB Stats – [File, Network, Registry, Process]
The `Recorder DB Stats - <event type>` sensors analyze the most recent 10000 events of that type and return data on anything that takes up more than 3% of the sample. This can be used to generate exclusions.

## Tuning the Recorder
Start by asking the `Recorder DB Stats – Overview` question to identify systems that are not retaining data. Drill down on the desired systems and ask the `Recorder DB Stats – Distribution` question to identify what is taking the most space. Ask the appropriate `Recorder DB Stats` question and analyze the returned data to identify potential exclusions. 

## Tuning Index
Index should be tuned before Recorder, as Recorder exclusions will influence the data returned. In this case, we only need to see the files that are being written the most frequently. The targeted machines must have the workloads that are desired to be filtered. Looking at the output of the `Recorder DB Stats – File` sensor, the files that are frequently written can be identified and filters can be created.

## Support
This content is provided by Tanium, but not supported. Please ask your TAM for best-effort assistance with this content.