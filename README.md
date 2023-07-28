# LFS(Love-at-First-Sight) 
 The increasing number of large knowledge graphs
 now available online requires methods for their effective and
 efficient exploration. Most of these knowledge graphs offer
 online SPARQL endpoints for directly issuing queries. In a
 typical scenario, the users issue coarse exploratory queries at
 the beginning, refining them further in the sequel in order to
 find the answer to the question in mind. However, those coarse
 exploratory queries are hard to be answered as they usually
 involve many results and take too much time to be answered, or
 even worse they time out, limiting the exploration potential of
 the data they expose.
 In this paper, we present the LFS (Love-at-First-Sight) system, offering a unique solution to the aforementioned problem,
 enabling users to rapidly fast get example answers to such coarse
 exploratory queries. More specifically we define the problem of
 the first-sight query answering, a form of approximate query
 answering returning only a single example answer to the issued
 query. We provide an effective and efficient solution to the
 problem of the first-sight query answering through summaries
 generated based on past workloads. We experimentally show the
 big benefits of the proposed summaries as their size is minimal
 and they can efficiently provide answers to the first-sight query
 answering the problem, highly increasing the response time for
 query answering over online SPARQL endpoints.
 <p align="center">

</p>
<p align="center">
  <img src="https://github.com/giannisvassiliou/LFS-ICDE-2024/blob/main/Architecture.JPG?raw=true" alt="Sublime's custom image"/>
</p>

## LFS Data Creator

Firstly we need to create the data by accessing the endpoint of the desired dataset. The parserIT.py script has the following syntax
<br>
<br><b> USAGE:  parsertIT queryfile {flag 0/1 mf or non mf}  {basefilename} {limit} {urlendpoint} </b>

where
<li>
queryfile : The name of the original querylog (see data folder, choose e.g YAGO_orig_quer.txt) 
</li>
<li>
flag : 0 or 1  whether we need most frequent results 1 (yes) or  0(no)
</li>
<li>
basefilename: a string to base the output file names {e.g yago}
</li>



<li>
limit: a SPARQL limit {e.g. 500}
</li>
<li>
urlendpoint: a valid url endpoint ( e.g.  https://yago-knowledge.org/sparql/query )
</li>
<br>
<b> We have stored in data folder result-examples for the 3 datasets we used (DBPedia, YAGO, WikiData) </b>
<br> These files can be used directly from the LFS EVALUTATOR
## LFS Evaluator

You need to provide two INPUT files (<b> orig_summary_filename</b> and <b> queries_for_summary</b> ) and one filename for OUTPUT (the actual <b> .nt LFS Summary </b>) ,  finally  the <b> address_of_endpoint </b>{OPTIONAL}
<br><b> <br>
USAGE:  lfs orig_summary_filename queries_for_summary LFS_summary_output {url of endpoint-optional) </b>

<li>
 orig_summary_filename: The filename of the summary that parserIT produced
 </li>
 <li>
 queries_for_summary: The filename of the previous summary, corresponding queries
 
</li>
<li>
 LFS_summary_output: The final .nt file of the actual LFS summary
</li>

<li> address_of_endpoint: if given, the system will try to evaluate the queries cannot be answered by the LFS Summary, from the endpoint
</li>

<br>

<b>The previous script, will:</b>
<br>
<li> Create the train/test portions from the orig_summary_filename </li>
<li> Create the lfs .nt summary (from the train portion)</li>
<li> Query the .nt summary created with the test queries</li>
<li> Present the % of the first-sight queries replied, and the time consumed</li>

  
