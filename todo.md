# status
* It is super cool and responsive and nice already

# next 
* Introduction text
  * Name
  * all authors that published in one of the leading demographic journals
  * exclude some for performance
  * The titles were fed to a deep learning model to create embeddings where similar titles should have similar embeddings
  * UMAP dimensionality reduction to 2d and then displayed with force-graph
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
* use sql.js?
  * then be able to filter by:
    * year
    * journal
    * institute?
    * author?
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