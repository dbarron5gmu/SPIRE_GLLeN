To build Neo4j database:<br>
 Edit the destination for the C files in 1_exeBenchToC.py and change the directories for 2_gccToCFG.py, 03_cfg_to_json.py, 04_json_to_neo4j.py and then run 1_exeBenchToC.py<br>
 Next run 2_gccToCFG.py which will run gcc on all c files and build CFG's<br>
 Then run 03_cfg_to_json.py to convert te CFG's to Json for neo4j<br>
 Next run 04_json_to_neo4j.py to import all json files into the Neo4J database<br>
 Then run 08_one_off_embeddings.py which will convert the DOT file into a NetworkX graph, number of nodes, edges, loops, and decision points, and update these values.<br>
To run the RAG pipeline:<br>
 Go to the demo directory<br>
 Run assemblySearchHandler.py<br>
