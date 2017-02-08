In order to give more meaning to your Contents and to enrich the knowledge structure, a tag system has been set up. It is structured similarly to the knowledge part: there is a **Tag Set** which incorporates the whole domain of Tags. It is composed of **Tags** which are related between each other thanks to **Tag Edges**. The Tag Edges shows that one Tag is more difficult, or includes, another Tag.
By default, one Tag Set exists to categorize the Contents. This way, one can indicate if a Content is a question type or not.
The tag system will come in handy when we will deal with the learning rules and adaptive learning functionalities.
The following image describe the tag structure:

![URL Creation](https://raw.githubusercontent.com/Celumproject/domoscio-docs/master/uploads/tags.jpg)

<br/><br/>

# 4.1 Tag Set

In parallel of creating your knowledge\'s structure, you can create any Tag that you want. To structure those Tags, they can be grouped by Tag Set. Therefore, when setting up your own tag system, the Tag Set is the first object to declare.

<br/><br/>

# 4.2 Tag

Once you have created a Tag Set, you can start create the actual Tags related to it. They can be used to give any additional information you want to your Content, to the Knowledge Nodes, to the Knowledge Graphs...

<br/><br/>

# 4.3 Tag Edge

To create a link between two Tags because one includes the other, you can create a Tag Edge from one to the other. As such you are creating a DAG (directed acyclic graph) of Tags. For performance purposes, when you create an Edge we will create a bunch of indirect Edges to fully describe the graph. Please bear this in mind in you try to fetch the Tag Edges at some point.



<br/><br/>

# 4.4 Taggings

At this point, your Tags are structured and set. They can now be used to tag the objects, and this is done through Taggings, which make the bridge between one Tag and one object.