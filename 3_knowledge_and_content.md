

The first step to start is to declare the learning objects. They can be anything : a video, a quizz, an image... In the API, a learning object is called a **Content**. Those objects deal with different concepts. The concepts are registered in the API as **Knowledge Nodes**. The Knowledge Nodes dealing with a common topic are organized and in **Knowledge Graph**. This structure is made through **Knowledge Edges**.

![URL Creation](https://raw.githubusercontent.com/Celumproject/domoscio-docs/master/uploads/graph.jpg =923x460)

<br/><br/>

# 3.1 Knowledge Graph

The content’s structure is gathered into Knowledge Graphs. A Knowledge Graph is the first object to instantiate while setting up your content on our API. It is the higher level of structuration.

</br>
</br>

# 3.2 Knowledge Node

Knowledge Nodes are the second objects to instantiate while setting up your content on our API. They represent concepts. It can be "Least Common Multiple" in a Math course context or "Delegating Style" in a Management course context.

</br>
</br>

# 3.4 Knowledge Edge

The Knowledge Edge are here to structure the Knowledge Nodes between one another. They indicate pre-requisite relationships between a source and a destination. In other words, the source Knowledge Node has to be mastered for the learner to understand the destination Knowledge Node.
For instance, the addition has to be understood before starting to learn multiplication.

</br>
</br>

# 3.5 Content

A Content is anything that allows the learner to learn or to be evaluated. It can be an image, some text...

</br>
</br>

# 3.6 Knowledge Node Content

The Knowledge Node Content makes the link between a Content and a Knowledge Node. Especially when a learning object is large (such as a long video or a book), it can deal with several Knowledge Nodes. Therefore, a Content can have one or several Knowledge Node Content(s). 


</br>
</br>








