---
author: Souhil Zaida
title: Data Warehouse
date: 2021-07-14
description: Why we need data warehouse
math: false
thumbnail: https://cdn.hashnode.com/res/hashnode/image/upload/v1641641507119/6NxNJhO7S.png?w=1600&h=840&
---

# Why we need data warehouse

Assume you have an organization or a company that contains various applications and their data is stored in various databases. If you want to get a report from these sources, it will take time, so you must integrate the data from these sources and store it in a single location known as a data warehouse, so we can say that a data warehouse is simply a centralized database that allows the organization to gain an overview of the business.

![dw.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1641640397102/VWtxKUnGi.png)
One of the reasons that a data warehouse is a better solution for your business is that when users try to get reports directly from operational systems, it causes performance issues. Furthermore, having a single version of the truth allows each department to produce results that are consistent with the results of all other departments.
Data warehouse allows users to create their own reports without having to get IT involved.

# Data Warehouse architecture

![BG_Architecture.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1641641530941/R-QQyyLef.png)

## Data source :

The data source contains the company's OLTP database, which could be CRM, HR, or another type of database. The data source is updated on a daily basis and is available in a variety of formats, including file format, relation data base, cloud app, and excel....

## Data Preparation :

The preparation partition is divided into two sections: staging area and data warehouse. In this article, we'll go over the staging area in detail.

## Semantic Layer:

This layer aggregates the data warehouse's data and stores it in cubes.

## Presentation :

We employ visualization tools in this phase to tell stories about data or reports.

# Modern Data Warehouse architecture:

![dw-2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1641642645808/JngN4zvBi.png)

Does the architecture alter now that most organizations store data in the cloud? No, the technique remains the same, but the method for storing data has changed. We can use a cloud or on-premises data base as a data source. Meanwhile, the name of the staging area has been changed to data lack, and the data is saved in file format before being loaded into the data warehouse using an ETL. The semantic layer is unchanged, but the nomenclature varies depending on which technology firm supplies the ETL tools and cloud service, such as Microsoft Azure:


The staging area : Relational Sotrag => Storage Blob : Data Lacke

Data warehouse :  Relational Sotrage ⇒ Azure synapse  Analytics

ETL : Data Factory

Semantic Layer : SSAS : Azure Analysis Services

# ETL

![do-perfect-etl-ssis-data-automation-ssis-related-work.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1641642736447/QMzsoy5M4.jpeg)

Let us now discuss the tool that will assist us in creating the data warehouse. ETL is an acronym that stands for Extract, Load, and Transform. Many ETL tools are available on the market, including SSIS, Talend, DataStagge, Knime, and Airflow. For cloud architecture, we have Azure Data Factory, AWS Glue, Hevo Data, and Fivetran.

If ETL stands for Extract, Load, and Transform, what does ELT stand for and what is the difference between them?

ELT is simply a process of extracting and loading data before transforming it. The main difference between ETL and ELT is that ELT is used for big data solutions because we extract and load data directly to the data lack and then transform the data when we need it for any reason.
We use the same tools to apply these techniques, so whether you're using Talend, SSIS, or Azure Data Factory, you can use ETL or ELT.

# Staging Area

The staging area, also known as the landing zone, is a temporary storage area used for data processing during the extract, transform, and load process. It sits in the middle of the data sources and the data warehouse. You're probably wondering why we can't use the ETL process directly from our source to the data warehouse! Let's look at some examples to help you understand:

Assume you're loading 1 million rows from a source into your DW and the process abruptly fails due to a network issue. So you'll have to touch the source again to load this data, but first you'll have to figure out which rows were changed before the failure, or you'll have to re-extract all 1 million rows. The issue here is that you're constantly disturbing the source. However, if the data is loaded and processed in the staging area, and it fails 1,000 times when loading to the data warehouse, it won't matter because the data is already in the staging area, and we won't have to reprocess it from the source.

Another difficulty is that when you try to integrate numerous sources, computing the join of those sources in the ETL becomes too complicated to manage, and performance suffers as a result.

# ODS 

An operational data store, or **ODS**,  is a central database that stores a snapshot of the most recent data from several transactional systems for operational reporting.

It is a copy of the data source that is used as a source for the enterprise data warehouse; it is a complementary element that not all companies have. So the **ODS ** serve the same purpose as the staging area, which begs the question, 
> What's the difference?

Assume we don't have **ODS** and instead load our data to staging before proceeding to the data warehouse. Because the staging area is a temporary data base, there are two options: allowing the data to remain or clearing it.

If your business logic changes, and you get your data from a data source on a daily basis, and the staging area is cleared, you won't be able to update your DW because the old data doesn't exist in the staging area, or we'll have to load them from the source, which will take a long time due to the volume of data, and it will disrupt the data source.

Even if we keep the history in the staging area, reloading the history from the data source disturbs the sources, resulting in poor performance. Meanwhile, if you have the **ODS** system, which is a clone of the data source system, whatever actions we make will never disrupt the data source, and it will increase performance.
