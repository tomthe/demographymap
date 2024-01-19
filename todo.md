# status
* It is super cool and responsive and nice already

# next 
* bug: names disappear when zoomed to far in 
  * only on Firefox! But why?
* bug: hover sometimes doesnt work in Brave browser
  * works good in Chrome on Hydra!?!?
  * Maybe ... memory?

* 


* Github and readme
* add topics to the vis
  * rows with type="t", author_name="fertility..." n_citations = very high number
  * show them as text from the beginning. what when zoomed in? hide or not?
  * to fix:
    * not super good labels
  * change colors!
* use url-parameters to share a position
* make it more generic and use url-parameters to load a specific datasource
  * have data subdir and for every datasource another subdir. This includes the primary tsv and the tiles.tsv and a js-file with configuration-variables(scalefactor, ntiles......)
* run the embeddings on a massive dataset
* better generation of topic labels and topic clusters
  * Maybe Bertopic was not bad after all? Can I get the embeddings and Umap values out?


* send to people/twitter


# Can do

* other data
  * ror - all institutions?
  * other disciplines 
    * Science of Science, vosviewer...
    * ML - they love embeddings
    * How to get good parts of data? Top journals?
  * all demographers, but wider: really all demographers
    * identify all demographers and then get all their papers from other journals as well
  * dem research only version?
  * so
  * from OpenAlex dump so that there is more information and bigger!
    * institution-coordinates: show all papers and authors near to the affiliation
      * --> a world map of all papers...
      * x,y <-- gps of affiliation + embedding scaled down to a few km
        * what if this intersects? make this dynamic? merge nearby affiliations?!
  * Hacker News
    * data:
      * all submissions with at least some comments or points, text embedding of submission title
        * Text embeddings might not be enough? because titles are sometimes too short and different...
        * users: 
          * average of their submissions or average of their comments or average of the submissions they commented on
      * embed all comments, users are the average of their comments, submissions are average of their comments...

* Show/Highlight links to other papers/authors on hover
  * Which data to show?
    * authors: all their papers
    * papers: all their authors
    * other possible stuff: 
  * How to query the right data?
    * links are a big list with [{source:id, target:id, ???},{}...]
    * option 1: load a big source-target list on start, filter on hover/click
      * Problem1: big file, bigger than the nodes, because every node will have several links
      * Problem2: which should be the id? Never mind - the openalex id
      * Problem3: Tiles. if i am in a tile, should I also have links to all other places?
  * change graphData,

  * what does anvanka use?
* use sql.js?
  * then be able to filter by:
    * year
    * journal
    * institute?
    * author?
    * dynamic position!?
  * have to add ui and some code. and sql.js
  * have to export as sqlite

* click on point/name/title --> do something
  * show more information in box
  * link to openAlex
  * highlight connections?

* transitions
  * possible, but we need other positions!
    * n_citations, n_works or n_authors?

* dynamic data loading
  * if zoomed in enough, fetch new data files and paint them.
  * remove that data when you move or zoom away
  * data layout
    * one global dataset that is always loaded. most important nodes
    * e.g. 8*8 tiles of more data, only loaded after some zooming in
    * even more tiles if zoomed in more....?
    * how in python:
      * get min,max x,y. divide into 16*16 squares...
      * get relevance --> relevance decides about zoom-level
      * for level in [0,1,3]... for ix in range(16) for iy in range(16) 
        * duckdb-copy select .... where ix*width/16>x>ix*width/16+width ....and relevance > level
  * How to do this with force-graph library?
    * Just change the data1 and then call Graph.graphData(data1)
    * to change the data:
      * data1.push(...data2) or data1 = [].concat(data1,data2)
      * remove: data1.splice(len(data1))
      * both in one operation: data1.splice(len(data1),...data2)
    * use onZoomEnd({ k, x, y }) event to check how far zoomed in we are, and where (is also triggered by panning)
  * Problem: searching is more difficult now.
    * static-server-search: create files based on the typed-in characters: aaa.json, aab.json .... and fetch them after typing
    * seems easy with autocomplete: change src from an array to a function that returns and array of objects - yes, works!
      * json-file: starts directly with [ and then a list of objects. [{author_name:"tom", fx:5.3,fy:-2.2}, {...},...]

* Make it generic/reusable/libary
  * non-dynamic version: just change the data-file and maybe some variables
  * dynamic version: a python(-library?): 
    * takes a dataframe with x and y columns (and more), then writes the html and the data files
      * import embeddomator
      * embeddomator.create_and_save_html(dataframe,xcol,ycol,hovercolumns,relevancecol)

* transition between different positions/columns:
  * https://github.com/vasturiano/3d-force-graph/issues/344
  * e.g. transition positions from x,y to n_works,averagecitations...

* use top2vec to create topics which give the plot more structure from scaled away
  * https://github.com/ddangelov/Top2Vec
    * older
  * https://github.com/MaartenGr/BERTopic
    * seems better?

## Old
* authors + papers in one graph?!
  * papers with umap, authors connected and placed to average?
  * Problem with performance?
  * Data layout?
    * nodes: id, text (either title or name), type, x, y
* search
  * when found, then:
    * zoom to result
      * how? Zoom to x,y is easy, but how to get xy?
    * filter or highlight result
      * with sqljs
        * highlight: modify size if search is true...
  * libraries
    * are they fast enough?
    * awesomeplete?
    * something with sqlite.js?
    * https://github.com/TarekRaafat/autoComplete.js

* render some as text and some as circles to save cpu
  * make it depend on the zoom level


* Why keeps cpu spinning?