# Tomcat-Analysis

This application uses [Peass](https://github.com/DaGeRe/peass) and the [Peass-Ant plugin](https://github.com/stro18/peass-ant) to detect code-level performance 
changes between commits of [Apache Tomcat](https://github.com/apache/tomcat). Currently, the latest commit that can be analyzed is 
[6cf20b4](https://github.com/stro18/tomcat/commit/6cf20b4a83f1e5b2ae86525b6b96389e801776b2).

## Building

    mvn clean package  

## Configuration

Peass provides command options to configure the performance analysis, e.g. `startcommit` and `endcommit`. In this repository, the values for the command options are set in ./peasstomcat.

## Usage

1. Regression Test Selection:
   1. Delete ./results and ../tomcat_peass (if necessary)
   2. Execute `./peasstomcat select`
      - Selected tests in results/traceTestSelection_tomcat.json
2. Performance Measurement and Comparison:
   1. Copy commands from ./results/runall.sh to ./measureWrapper
   2. Execute `./measureWrapper`
   3. Execute `./peasstomcat getchanges`
      - Detected performance changes in results/changes.json
3. Root Cause Analysis:
   1. Copy commands from ./results/run-rca-tomcat.sh to ./rcaWrapper
   2. Execute `./rcaWrapper`
   3. Execute `./peasstomcat visualizerca`
      - Visualized root causes in results/\<analyzedCommit\>/\<analyzedTest>.html
