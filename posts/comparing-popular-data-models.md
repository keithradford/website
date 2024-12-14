_This post is a paper that was written for CSC 482B (Algorithms and Data Models) at UVic during the Fall 2022 semester. Permission was granted by the professor to post this paper on my blog._

## ABSTRACT

Data modeling is an important aspect of database design as it determines how data is organized, stored, and accessed. There are various data models available, each with its own strengths and weaknesses.
In this paper, we compare three popular data models: the entity- relationship diagram model, the key-value model, and the labelled property graph model. We compare the complexity, data manipulation capabilities, flexibility, data structure, and use cases of each model to help readers understand the trade-offs and best practices for selecting the right data model for their needs. Our analysis shows that while each model has its own unique features and benefits, the most appropriate data model will depend on the specific requirements and goals of the project.

## 1. Introduction

Data modeling plays a vital role in the design and management of databases, as it determines how data is organized, stored, and accessed. In this report, we will be comparing three popular data models: the entity-relationship diagram model, the key-value model, and the labelled property graph model. By comparing the complexity, data manipulation capabilities, flexibility, data structure, and use cases of each model, we aim to provide readers with a better understanding of the trade-offs and best practices for selecting the right data model for their needs. Our conclusion is that while each model has its own unique features and benefits, the most appropriate data model will ultimately depend on the specific requirements and goals of the project.

## 2. Discussion

To compare the three models the following topics will be discussed for each: complexity, speed, flexibility, structure, and use cases. All models vary for each criterion to different degrees which is why several options must be considered.

### 2.1 Complexity

How easy to read, understand, implement, and maintain a model is all adds up into its complexity. Multiple factors play into complexity and what can make a model complex.

#### 2.1.1 Entity-Relationship Diagram

The entity-relationship diagram (ERD) is made up of three main elements: entities, relationships, and attributes [1]. Furthermore, relationships can have varying multiplicity. With a few more possible elements that make up an ERD, the model consists of several options. This means that more information included can quickly increase the complexity. Overall, as Jordan states in Practical Neo4j, “the ER[D] is fairly simple to create and can be understood...with minimal instruction” [2].

<img alt="Complex ERD" src="/comparing-popular-data-models/complex-erd.png">

**Figure 1: Complex ERD [3]**

#### 2.1.2 Labeled Property Graph

Like the ERD, the labelled property graph (LPG) consists of three elements: nodes, relationships, and properties [2]. Unlike the ERD, however, it does not go beyond that. With a small number of elements involved in the model the readability increases significantly. However, as Batini et. al mention “The degree of minimality of a model is also a trade-off, because the availability of a larger and richer set of concepts, which may overlap, helps the designer to perceive and model reality” [3].

<img alt="Complex LPG" src="/comparing-popular-data-models/complex-lpg.png">

**Figure 2: Complex LPG [2]**

#### 2.1.3 Key-Value

Perhaps the simplest structure discussed in this report is the Key-Value (KV) model. Storing a collection of key-value pairs, _(k, v)_, where k is a key and v represents a value. The structure allows for fetching, inserting, and deleting data in the form of the following methods: _get(k), put(k, v), and remove(k)_ [4]. The model is minimal and intuitive making it extremely simple.

### 2.2 Data Manipulation

Storing and reading data is an important part of a data model. Additionally, it may be important for whoever is modelling data to ensure it can be manipulated in the future [5]. This plays into the longevity of a data model.

#### 2.2.1 Entity-Relationship Diagram

ERDs are effective when working with constrained data which makes them effective for relational databases. However, they are insufficient when this is not the case. This introduces a challenge and inefficiency when the scope of the model must change frequently [2].

#### 2.2.2 Labeled Property Graph

The graph model and the lack of constraints allow for easy data manipulation. If values need to be changed to different types or if relationships between nodes need to be redirected, the process will not be time consuming. Overall, these changes can be made without facing detrimental consequences. The LPG are agile and workable when it comes to data manipulation [6].

#### 2.2.3 Key-Value

While the simplicity of the KV model allows for fast lookups and an understandable model, it is not well equipped for complex data manipulation operations. You cannot query the KV model without a key which shows why large-scale manipulation is close to unachievable in this model [7].

### 2.3 Flexibility

A flexible data model allows for the use of a model across different scenarios. Whether this be for changing requirements or if a final target is unclear, it can be an important feature for whoever oversees creating a data model. This attribute is closely related to the data manipulation of a model however it extends further than making changes to data.

#### 2.3.1 Entity-Relationship Diagram

2.2.1 Entity-Relationship Diagram. An ERD is mostly used for the logical design of a relational database. In this case, a logical schema is created as a singular graphical representation of the data’s structure [3]. Therefore, a strict outline is enforced. As discussed under data manipulation, this restricts large-scale changes from effectively taking place. A tradeoff is introduced while using this model as flexibility is decreased in exchange for consistency.

#### 2.3.2 Labeled Property Graph

With LPGs being based on the graph data structure, they manage to be consistent and able to analyze dense relationships while being incredibly flexible [2]. This is largely in part from the schema-less approach that comes with using LPGs. Flexibility in an LPG allows for the data model to scale while not putting speed at risk and ensuring the creators of the model are not slowed down by the process.

#### 2.3.3 Key-Value

Falling under the schema-less category like the LPG, the KV model allows for more flexibility than an ERD. There are no strict layouts to be followed when using this model as data can be stored in any format [4]. Furthermore, this means each value can have different structures.

### 2.4 Structure of Data

The structure of each of the three models differ greatly. Comparing how each are built up gives insight into when it may be appropriate to use a specific one. Specifically, we will look at how data is structured in each model and which operations (if any) are available.

#### 2.4.1 Entity-Relationship Diagram

The structure of ERDs lines up closely to that of a relational database. The three main elements are entities, relationships, and attributes. An entity represents a concept, for example “person”. A relationship represents how n concepts relate to each other, for example “person owns a house”. Lastly, attributes can be assigned to both entities and relationships to provide further context into the portrayed concepts [3]. See Figure 1 for an example ERD.

#### 2.4.2 Labeled Property Graph

An LPG is structured with three elements: nodes, relationships, and properties. A node is used to represent some collection of data, and in the LPG model it is classified with a label. An example could be “person”. Relationships tie together two nodes and are the focus of the LPG. They allow for the representation of concepts such as “person **is friends with** another person”. Like the ERD, additional context (more data) can be provided through properties which could add attributes such as _{name, height, weight}_ to a person node [2]. See Figure 2 for an example LPG.

#### 2.4.3 Key-Value

The KV model has a very simple structure. The important concept is that each data item is stored as a “key- value” pair. This means that any chunk of data is represented by a singular “key” which is unique and only used to identify the data. It is up to the implementation how the data is structured within the model if it conforms to the KV pairing.

<img alt="Overview of how the KV model works" src="/comparing-popular-data-models/kv-model-overview.png">

**Figure 3: Overview of how the KV model works [4]**

There are three operations that can be performed on the model [4]:

1. _put(k, v)_- assign _v_ to key _k_.
2. _get(k)_ - fetch data at key _k_.
3. _remove(k)_ - delete data at key _k_.

### 2.5 Use Cases

Common use cases of each data model can be used to help guide decisions. For most cases, they can be abstracted down into simple concepts which accurately reflect when someone may be interested in using a model.

#### 2.5.1 Entity-Relationship Diagram

The primary use case for an ERD is when creating a logical design of a relational database [8]. What this means is data that is being stored often relates to other data concepts. Typically, the data format is strict as it must conform to a predefined schema [9]. Therefore, an ERD can be used when the data concepts derived from requirements can be interconnected. Lastly, this model should be used when the requirements are clear and not likely to change due to the complexity of modifying a schema.

#### 2.5.2 Labeled Property Graph

The freeform structure of a graph database makes for a good option when requirements are changing. Additionally, this structure is beneficial when it is not clear how the data should be formatting. However, the major use case for the LPG model is when gaining insights from the data is important. The model treats relationships as first-class citizens which makes relationship analysis efficient [10].

#### 2.5.3 Key-Value

Due to its quick access times, the KV model is appropriate when speed is important. The model also excels if requirements lay out data in a way that conforms to the key-value approach [11]. As simple as it may sound, it is important to look out for. Common examples of this model include session stores. Each session on a website can typically be associated with a unique identifier which conforms to the key-value model [12].

## 3. Results

Tying together the main points discussed above make it unclear if any singular model is superior. However, with each model being so different, this means it all comes down to provided requirements to determine which model is best. Through this discussion, cases were realized that each model excels in different areas.
The ERD is a solid and popular data modelling choice. While it has difficulties scaling it provides a method of communicating logical design that is very familiar. One major takeaway is the flexibility of both the LPG and KV model. While the two serve different purposes, being schema-less provides many options. As discussed, this can be important and beneficial in many cases.

## 4. Conclusion

Data modeling is a crucial aspect of database design and management as it determines how data is organized, stored, and accessed. There are various data models available, each with its own strengths and weaknesses. In this paper, we compared three popular data models: the entity-relationship diagram (ERD) model, the key-value model, and the labelled property graph model. We compare the complexity, data manipulation capabilities, flexibility, data structure, and use cases of each model to help readers understand the trade-offs and best practices for selecting the right data model for their needs. We conclude that while each model has its own unique features and benefits, the most appropriate data model will depend on the specific requirements and goals of the project.

## REFERENCES

[1] H. Garcia-Molina, J. D. Ullman, and J. Widom, Database systems: The complete book. Pearson, 2014.

[2] G. Jordan, Practical neo4j. Apress, 2014.

[3] C. Batini, S. Ceri, and S. B. Navathe, Conceptual database design: An entity- relationship approach. Redwood City, CA: Benjamin/Cummings, 1998.

[4] M. T. Goodrich and R. Tamassia, Algorithm design and applications. Wiley, 2015.

[5] “Data manipulation: Definition, purpose, examples: Unext jigsaw,” Jigsaw Academy, 25-Nov-2022. [Online]. Available: https://www.jigsawacademy.com/blogs/data-science/data-manipulation/. [Accessed: 19-Dec-2022].

[6] “Graph based data model in nosql,” GeeksforGeeks, 30-Mar-2022. [Online]. Available: https://www.geeksforgeeks.org/graph-based-data-model-in-nosql/. [Accessed: 19-Dec-2022].

[7] “Key-value data model in nosql,” GeeksforGeeks, 17-Feb-2022. [Online]. Available: https://www.geeksforgeeks.org/key-value-data-model-in-nosql/. [Accessed: 20-Dec-2022].

[8] “Entity relationship diagram (ERD),” Entity Relationship Diagram (ERD) - What is an ER Diagram? [Online]. Available: https://www.smartdraw.com/entity- relationship-diagram/. [Accessed: 21-Dec-2022].

[9] “What is a relational database?,” Oracle. [Online]. Available: https://www.oracle.com/database/what-is-a-relational-database/. [Accessed: 21- Dec-2022].

[10] “Why graph databases?,” Neo4j Graph Data Platform, 21-May-2022. [Online]. Available: https://neo4j.com/why-graph-databases/. [Accessed: 21-Dec-2022].

[11] “What is a key-value database?,” MongoDB. [Online]. Available: https://www.mongodb.com/databases/key-value-database. [Accessed: 22-Dec- 2022].

[12] “NOSQL,” Amazon, 2018. [Online]. Available: https://aws.amazon.com/nosql/key-value/. [Accessed: 22-Dec-2022].
