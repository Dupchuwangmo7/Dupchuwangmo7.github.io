---
Title: DBS101 Flipped Class 8
categories: [DBS101, Flipped_Class8]
tags: [DBS101]
---

# Indexing

Indexing of Spatial and Temporal Data - Indexing spatial and temporal data is a vital tool for managing information with a physical location and a time dimension.

It is used in

- Traffic monitoring
- Location-based services
- Environmental monitoring
- Asset tracking and management
- GPS- and sensor-based data
- Sensor networks, among others.

Why it matters?
Imagine you have a giant dataset that shows where and when every single Uber ride occurred in a city. If you wanted to search this data to find a specific ride, every search would take forever if you had to go through all of the data one entry at a time. Instead, you can build indexes that act like a shortcut on top of our data. These indexes, which are built with a specific goal in mind, arrange our data based on the physical location and time for high-speed access into particular data.

Common Indexing Techniques

- R-trees and Quadtrees: These divide the space into grids and store data points within relevant grid cells.
- Space-Time Grids: Similar to grids, but with an additional layer for time intervals.
- B-trees: Traditional B-trees can be adapted to handle spatio-temporal data by incorporating spatial and temporal keys.

## Bitmap Indices

Bitmaps are a special type of index used in databases, especially on large scales, to accelerate queries. Essentially, a bitmap is a string of bits, which are 0s and 1s. In the context of spatial or temporal bitmap index, all the bits of a bitmap are in a one-to-one relationship with a location or a time interval.

Bitmap indices are appropriate for several scenarios;

- low-cardinality columns: these columns have very few unique values.Bitmap indices are perfect for such columns as they take up less space since the bitmaps are small, temporary data.
- Data warehouses: in this event, the database is read-only, but the amount of data acquired is enormous. Bitmap indices are beneficial in this situation as they are built for retrieval.

Below are the types of bitmap indices;
- improving query performance: such columns are involved in a large number of selections, e.g., gender or region.

One limitation, however, can be frequent updates in the stateful databases since it is resource-consuming to maintain the bitmaps for each update.

## Buffer Tree

A buffer tree is an advanced data structure designed for efficient processing of large datasets stored on external storage devices like hard drives.

Applications:

- External sorting algorithms
- Large-scale data processing

Addvantages

- I/O efficiency : By grouping multiple operations together in the buffer, it minimizes the number of disk accesses needed.

- Batch processing : Buffer trees excel at handling batched operations on the data.
- Flexibility : Buffer trees can be used to implement various external data structures like priority queues and range trees

# During Flipped Class

This flipped class was far better than other flipped classes we had. We were divided into 6 groups but grouping was done uniquely where each student was assigned with a song lyrics and students had to find group members by singing those lyrics. After group division, we had to discuss the given topic. After 30 minutes of discussion, 3 groups were combined into one forming two different groups. Each group had to present their topics to other members and after that we did quizzes on the topics we discuss on.
