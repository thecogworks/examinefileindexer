# Cogworks.ExamineFileIndexer

Cogworks.ExamineFileIndexer is a custom indexer to index any umbraco MEDIA node. 
Under the hood it makes use of [apache tika](http://tika.apache.org/) to extract content and meta data from umbraco media files. 
Tika can handle the [following formats](http://tika.apache.org/1.2/formats.html)

##Installation

The preferred method for installation is via nuget 

install-package Cogworks.ExamineFileIndexer

After installation your ExamineIndex.config and ExamineSettings.config file will updated.  The following entries will be added

### ExamineIndex.config ###

  <IndexSet SetName="MediaIndexSet" IndexPath="~/App_Data/TEMP/ExamineIndexes/MediaIndexSet">
    <IndexAttributeFields>
      <add Name="id" />
      <add Name="nodeName" />
      <add Name="updateDate" />
      <add Name="writerName" />
      <add Name="path" />
      <add Name="nodeTypeAlias" />
      <add Name="parentID" />
    </IndexAttributeFields>
    <IncludeNodeTypes>
      <add Name="File" />
    </IncludeNodeTypes>
  </IndexSet>
  
### ExamineSettings.config ###
Under ExamineIndexProviders/providers
 <add name="MediaIndexer" type="Cogworks.ExamineFileIndexer.UmbracoMediaFileIndexer, Cogworks.ExamineFileIndexer" extensions=".pdf,.docx" umbracoFileProperty="umbracoFile" />

Under ExamineSearchProviders/providers

<add name="MediaSearcher" type="UmbracoExamine.UmbracoExamineSearcher, UmbracoExamine" indexSet="MediaIndexSet" analyzer="Lucene.Net.Analysis.Standard.StandardAnalyzer, Lucene.Net" />
 
### License ###

Copyright &copy; 2017 [The Cogworks Ltd](http://www.thecogworks.com/), and other contributors

Licensed under the MIT License.