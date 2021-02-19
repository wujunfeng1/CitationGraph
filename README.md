# CitationGraphs

This is a package for saving and loading citation graphs.

### Examples:

```
using CitationGraphs

# Load citation graph from csv data. 
# The csv data are stored in three csv files:
# ijcai-citation-graph-nodes.csv
# ijcai-citation-graph-edges.csv
# ijcai-citation-graph-labels.csv
# Here, ijcai is the prefix. Since the files are in "." (current) directory,
# we pass "." (the path of these files) as the first argument to the following
# function call. The second argument is the prefix.
citationGraph = loadCitationGraph(".", "ijcai")

# The return value of the function call above, i.e., citationGraph, is of the
# following type:
# 
# struct CitationGraph
#     nodes::Dict{Int, CitationNode}
#     toBeAnalyzed::Vector{Int}
# end
# 
# where the node type is defined as:
# 
# struct CitationNode
#     id::Int
#     year::Int
#     title::String
#     labels::Vector{String}
#     refs::Vector{Int}
#     cites::Vector{Int}
# end
# 
# Therefore, to access the data in citationGraph, we could do it like this:
node = citationGraph.nodes[id]
# like this:
citationGraph.nodes[citeID] = CitationNode(citeID, citeYear, citeTitle, String[], Int[], Int[])
# like this:
push!(node.cites, citeID)
# and like this:
saveCitationGraph(".", "ijcai", citationGraph)
```

