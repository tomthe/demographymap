# next 
 * better averaged data
 * a version with mixed or paper data
 * OpenAlex data?



# Can do

* use sql.js?
  * then be able to filter by:
    * year
    * journal
    * institute?
    * author?
  * have to add ui and some code. and sql.js
  * have to export as sqlite
* other datasources
  * no citation information so far
  * scopus data issues!
* authors
* papers
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
* click on point/name/title --> do something
  * show more information in box
  * link to openAlex
  * highlight connections?

* transitions
  * possible, but we need other positions!
    * citation numbers...