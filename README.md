# Internship-Project on GNN
Here I did a Project on GNN to predict the link between the user and their attended events.

"mtags&event&tags" file has dictionaries, of users and events, which is actually feature vectors. Here for users' feature dimension is (125997,1001) and for event's feature dimension is (115571,1548).

"Json_read" has the feature vectors of users and events. Here I used PCA and reduced the dimensions to (125997,500) and (115571,500).

"New_GNN" file has the model where I create the adjacency list and create a general graph structure and predict the link between the edges and users.

