# MOB Suite IRIDA Plugin


# Table of Contents

   * [IRIDA Example Pipeline Plugin](#irida-example-pipeline-plugin)
   * [Building/Packaging](#buildingpackaging)
      * [Installing IRIDA to local Maven repository](#installing-irida-to-local-maven-repository)
      * [Building the plugin](#building-the-plugin)
   * [Dependencies](#dependencies)
   * [Using as a template for developing a plugin](#using-as-a-template-for-developing-a-plugin)
      * [1. Place necessary pipeline files in <a href="src/main/resources/workflows">src/main/resources/workflows</a>](#1-place-necessary-pipeline-files-in-srcmainresourcesworkflows)
         * [1.1. Creating pipeline files](#11-creating-pipeline-files)
         * [1.2. Updating pipeline files](#12-updating-pipeline-files)
            * [1.2.1. Modifying irida_workflow.xml](#121-modifying-irida_workflowxml)
            * [1.2.2. Modifying messages_en.properties](#122-modifying-messages_enproperties)
      * [2. Update <a href="src/main/java/ca/corefacility/bioinformatics/irida/plugins/ExamplePlugin.java">src/main/java/ca/corefacility/bioinformatics/irida/plugins/ExamplePlugin.java</a>](#2-update-srcmainjavacacorefacilitybioinformaticsiridapluginsexamplepluginjava)
      * [3. (Optional) Implement an <a href="src/main/java/ca/corefacility/bioinformatics/irida/plugins/ExamplePluginUpdater.java">Updater</a> class](#3-optional-implement-an-updater-class)
      * [4. Update the <a href="pom.xml">pom.xml</a> file](#4-update-the-pomxml-file)
         * [4.1. Update the Maven version/info](#41-update-the-maven-versioninfo)
         * [4.2. Update the properties section/plugin info](#42-update-the-properties-sectionplugin-info)
      * [5. Build and Test](#5-build-and-test)
      * [6. Distribute](#6-distribute)

# Building/Packaging

Building and packaging this code is accomplished using [Apache Maven][maven]. However, you will first need to install [IRIDA][] to your local Maven repository.

## Installing IRIDA to local Maven repository

To install IRIDA to your local Maven repository please do the following:

1. Clone the IRIDA project

```bash
git clone https://github.com/phac-nml/irida.git
cd irida
```

2. Install IRIDA to local repository

```bash
mvn clean install -DskipTests
```

## Building the plugin

Once you've installed IRIDA as a dependency, you can proceed to building this plugin. Please run the following commands:

```bash
cd cpo-pipeline-irida

mvn clean package
```

Once complete, you should end up with a file `target/cpo-pipeline-irida-1.0-SNAPSHOT.jar` which can be installed as a plugin to IRIDA.

If you have previously [setup IRIDA][irida-setup] before you may copy this JAR file to `/etc/irida/plugins` and restart IRIDA.  The plugin should now show up in the **Analyses > Pipelines** section of IRIDA.

![example-plugin-pipeline.png][]  

You should be able to run a pipeline with this plugin and get analysis results.

![example-plugin-results.png][]

And, you should be able to save and view these results in the IRIDA metadata table.

![example-plugin-metadata.png][]

# Dependencies

The following dependencies are required in order to make use of this plugin.

* [IRIDA][] >= 0.23.0
* [Java][] >= 1.8 and [Maven][maven] (for building)


## 6. Distribute

Once you've successfully built your plugin, you can distribute the JAR file to other IRIDA users to install in their instances.

[maven]: https://maven.apache.org/
[IRIDA]: http://irida.ca/
[Galaxy]: https://galaxyproject.org/
[Java]: https://www.java.com/
[irida-pipeline]: https://irida.corefacility.ca/documentation/developer/tools/pipelines/
[irida-pipeline-galaxy]: https://irida.corefacility.ca/documentation/developer/tools/pipelines/#galaxy-workflow-development
[irida-wf-ga2xml]: https://github.com/phac-nml/irida-wf-ga2xml
[pom.xml]: pom.xml
[workflows-dir]: src/main/resources/workflows
[workflow-structure]: src/main/resources/workflows/0.1.0/irida_workflow_structure.ga
[example-plugin-java]: src/main/java/ca/corefacility/bioinformatics/irida/plugins/ExamplePlugin.java
[irida-plugin-java]: https://github.com/phac-nml/irida/tree/development/src/main/java/ca/corefacility/bioinformatics/irida/plugins/IridaPlugin.java
[irida-updater]: src/main/java/ca/corefacility/bioinformatics/irida/plugins/ExamplePluginUpdater.java
[irida-setup]: https://irida.corefacility.ca/documentation/administrator/index.html
[properties]: https://en.wikipedia.org/wiki/.properties
[messages]: src/main/resources/workflows/0.1.0/messages_en.properties
[maven-min-pom]: https://maven.apache.org/guides/introduction/introduction-to-the-pom.html#Minimal_POM
[pf4j-start]: https://pf4j.org/doc/getting-started.html
[example-plugin-results.png]: doc/images/example-plugin-results.png
[example-plugin-pipeline.png]: doc/images/example-plugin-pipeline.png
[example-plugin-metadata.png]: doc/images/example-plugin-metadata.png
[pipeline-parameters.png]: doc/images/pipeline-parameters.png
[example-plugin-save-results.png]: doc/images/example-plugin-save-results.png