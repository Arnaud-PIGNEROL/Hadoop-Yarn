# TP YARN MapReduce2 - Arnaud PIGNEROL

## 1.2 Run the wordcount example
### Connect to HADOOP cluster using ssh
```
C:\Users\Arnaud>ssh apignerol@hadoop-edge01.efrei.online
Welcome to EFREI Hadoop Cluster

Password:
Password:
Password:
Last login: Sat Oct 17 19:26:23 2020 from eth-east-parth2-46-193-65-212.wb.wifirst.net
-sh-4.2$
```

### Use the following command to list the samples
```
-sh-4.2$ yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar

An example program must be given as the first argument.
Valid program names are:
  aggregatewordcount: An Aggregate based map/reduce program that counts the words in the input files.
  aggregatewordhist: An Aggregate based map/reduce program that computes the histogram of the words in the input files.
  bbp: A map/reduce program that uses Bailey-Borwein-Plouffe to compute exact digits of Pi.
  dbcount: An example job that count the pageview counts from a database.
  distbbp: A map/reduce program that uses a BBP-type formula to compute exact bits of Pi.
  grep: A map/reduce program that counts the matches of a regex in the input.
  join: A job that effects a join over sorted, equally partitioned datasets
  multifilewc: A job that counts words from several files.
  pentomino: A map/reduce tile laying program to find solutions to pentomino problems.
  pi: A map/reduce program that estimates Pi using a quasi-Monte Carlo method.
  randomtextwriter: A map/reduce program that writes 10GB of random textual data per node.
  randomwriter: A map/reduce program that writes 10GB of random data per node.
  secondarysort: An example defining a secondary sort to the reduce.
  sort: A map/reduce program that sorts the data written by the random writer.
  sudoku: A sudoku solver.
  teragen: Generate data for the terasort
  terasort: Run the terasort
  teravalidate: Checking results of terasort
  wordcount: A map/reduce program that counts the words in the input files.
  wordmean: A map/reduce program that counts the average length of the words in the input files.
  wordmedian: A map/reduce program that counts the median length of the words in the input files.
  wordstandarddeviation: A map/reduce program that counts the standard deviation of the length of the words in the input files.
```

### Case of the wordcount sample
```
-sh-4.2$ yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar \wordcount
Usage: wordcount <in> [<in>...] <out>
```

### Count all words of a downloaded e-book (in Plain Text UTF-8) from Project Gutenberg
```
-sh-4.2$ hdfs dfs -put davinci.txt

-sh-4.2$ yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar \wordcount /user/apignerol/davinci.txt /user/apignerol/wordcount

20/10/19 10:42:47 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.100.24:10200
20/10/19 10:42:47 INFO hdfs.DFSClient: Created token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603096967348, maxDate=1603701767348, sequenceNumber=1248, masterKeyId=23 on ha-hdfs:efrei
20/10/19 10:42:47 INFO security.TokenCache: Got dt for hdfs://efrei; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603096967348, maxDate=1603701767348, sequenceNumber=1248, masterKeyId=23)
20/10/19 10:42:47 INFO client.ConfiguredRMFailoverProxyProvider: Failing over to rm2
20/10/19 10:42:47 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /user/apignerol/.staging/job_1602414795136_0812
20/10/19 10:42:47 INFO input.FileInputFormat: Total input files to process : 1
20/10/19 10:42:47 INFO mapreduce.JobSubmitter: number of splits:1
20/10/19 10:42:47 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1602414795136_0812
20/10/19 10:42:47 INFO mapreduce.JobSubmitter: Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603096967348, maxDate=1603701767348, sequenceNumber=1248, masterKeyId=23)]
20/10/19 10:42:48 INFO conf.Configuration: found resource resource-types.xml at file:/etc/hadoop/3.1.5.0-152/0/resource-types.xml
20/10/19 10:42:48 INFO impl.TimelineClientImpl: Timeline service address: hadoop-master03.efrei.online:8190
20/10/19 10:42:48 INFO impl.YarnClientImpl: Submitted application application_1602414795136_0812
20/10/19 10:42:48 INFO mapreduce.Job: The url to track the job: https://hadoop-master02.efrei.online:8090/proxy/application_1602414795136_0812/
20/10/19 10:42:48 INFO mapreduce.Job: Running job: job_1602414795136_0812
20/10/19 10:42:57 INFO mapreduce.Job: Job job_1602414795136_0812 running in uber mode : false
20/10/19 10:42:57 INFO mapreduce.Job:  map 0% reduce 0%
20/10/19 10:43:05 INFO mapreduce.Job:  map 100% reduce 0%
20/10/19 10:43:12 INFO mapreduce.Job:  map 100% reduce 100%
20/10/19 10:43:12 INFO mapreduce.Job: Job job_1602414795136_0812 completed successfully
20/10/19 10:43:12 INFO mapreduce.Job: Counters: 53
        File System Counters
                FILE: Number of bytes read=505026
                FILE: Number of bytes written=1503351
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=1276305
                HDFS: Number of bytes written=373018
                HDFS: Number of read operations=8
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=2
        Job Counters
                Launched map tasks=1
                Launched reduce tasks=1
                Data-local map tasks=1
                Total time spent by all maps in occupied slots (ms)=15996
                Total time spent by all reduces in occupied slots (ms)=19860
                Total time spent by all map tasks (ms)=5332
                Total time spent by all reduce tasks (ms)=4965
                Total vcore-milliseconds taken by all map tasks=5332
                Total vcore-milliseconds taken by all reduce tasks=4965
                Total megabyte-milliseconds taken by all map tasks=8189952
                Total megabyte-milliseconds taken by all reduce tasks=10168320
        Map-Reduce Framework
                Map input records=22333
                Map output records=215829
                Map output bytes=2113018
                Map output materialized bytes=505026
                Input split bytes=104
                Combine input records=215829
                Combine output records=33584
                Reduce input groups=33584
                Reduce shuffle bytes=505026
                Reduce input records=33584
                Reduce output records=33584
                Spilled Records=67168
                Shuffled Maps =1
                Failed Shuffles=0
                Merged Map outputs=1
                GC time elapsed (ms)=166
                CPU time spent (ms)=7690
                Physical memory (bytes) snapshot=1476640768
                Virtual memory (bytes) snapshot=7265624064
                Total committed heap usage (bytes)=1550843904
                Peak Map Physical memory (bytes)=1177120768
                Peak Map Virtual memory (bytes)=3394084864
                Peak Reduce Physical memory (bytes)=299520000
                Peak Reduce Virtual memory (bytes)=3871539200
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=1276201
        File Output Format Counters
                Bytes Written=373018
```

### Once the job completes, use the following command to view output
#### "..." means there were too much lines to show them all
```
-sh-4.2$ hdfs dfs -cat /user/apignerol/wordcount/part-r-00000

...

“‘Canallers,    1
“‘Come  1
“‘Cross 1
“‘Damn  1
“‘Down  1
“‘Excuse        1
“‘How?  1
“‘I     4
“‘Is    2
“‘Lakeman!—Buffalo!     1
“‘Let   1
“‘Like  1
“‘Look  1
“‘Moby  1
“‘Mr.   1
“‘My    1
“‘Nay,  2
“‘Nay,’ 1
“‘Oh    1
“‘Say   1
“‘Shall 1
“‘Shut  1
“‘Sink  1
“‘So    2
“‘Stern 1
“‘The   1
“‘Then  2
“‘This  1
“‘Though        1
“‘Turn  3
“‘Very  1
“‘Well  1
“‘What  3
“‘Where 1
“‘Who’s 1
“‘Why   1
“‘Will  2
“‘Yes,  1
“‘You   2
“’Bout  1
“’Hind  1
“’Tis   2
“’Twill 1
“’tis   1
```

## 1.3 The Sudoku example
```
-sh-4.2$ cat > sudoku.dta
8 5 ? 3 9 ? ? ? ?
? ? 2 ? ? ? ? ? ?
? ? 6 ? 1 ? ? ? 2
? ? 4 ? ? 3 ? 5 9
? ? 8 9 ? 1 4 ? ?
3 2 ? 4 ? ? 8 ? ?
9 ? ? ? 8 ? 5 ? ?
? ? ? ? ? ? 2 ? ?
? ? ? ? 4 5 ? 7 8

-sh-4.2$ yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar \sudoku sudoku.dta

Solving sudoku.dta
8 5 1 3 9 2 6 4 7
4 3 2 6 7 8 1 9 5
7 9 6 5 1 4 3 8 2
6 1 4 8 2 3 7 5 9
5 7 8 9 6 1 4 2 3
3 2 9 4 5 7 8 1 6
9 4 7 2 8 6 5 3 1
1 8 5 7 3 9 2 6 4
2 6 3 1 4 5 9 7 8

Found 1 solutions
```

## 1.4 The Pi example
```
-sh-4.2$ yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar \pi 16 10000000

Number of Maps  = 16
Samples per Map = 10000000
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Wrote input for Map #10
Wrote input for Map #11
Wrote input for Map #12
Wrote input for Map #13
Wrote input for Map #14
Wrote input for Map #15
Starting Job
20/10/19 10:49:36 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.100.24:10200
20/10/19 10:49:36 INFO hdfs.DFSClient: Created token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603097376687, maxDate=1603702176687, sequenceNumber=1250, masterKeyId=23 on ha-hdfs:efrei
20/10/19 10:49:36 INFO security.TokenCache: Got dt for hdfs://efrei; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603097376687, maxDate=1603702176687, sequenceNumber=1250, masterKeyId=23)
20/10/19 10:49:36 INFO client.ConfiguredRMFailoverProxyProvider: Failing over to rm2
20/10/19 10:49:36 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /user/apignerol/.staging/job_1602414795136_0814
20/10/19 10:49:36 INFO input.FileInputFormat: Total input files to process : 16
20/10/19 10:49:36 INFO mapreduce.JobSubmitter: number of splits:16
20/10/19 10:49:37 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1602414795136_0814
20/10/19 10:49:37 INFO mapreduce.JobSubmitter: Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603097376687, maxDate=1603702176687, sequenceNumber=1250, masterKeyId=23)]
20/10/19 10:49:37 INFO conf.Configuration: found resource resource-types.xml at file:/etc/hadoop/3.1.5.0-152/0/resource-types.xml
20/10/19 10:49:37 INFO impl.TimelineClientImpl: Timeline service address: hadoop-master03.efrei.online:8190
20/10/19 10:49:37 INFO impl.YarnClientImpl: Submitted application application_1602414795136_0814
20/10/19 10:49:37 INFO mapreduce.Job: The url to track the job: https://hadoop-master02.efrei.online:8090/proxy/application_1602414795136_0814/
20/10/19 10:49:37 INFO mapreduce.Job: Running job: job_1602414795136_0814
20/10/19 10:49:47 INFO mapreduce.Job: Job job_1602414795136_0814 running in uber mode : false
20/10/19 10:49:47 INFO mapreduce.Job:  map 0% reduce 0%
20/10/19 10:49:56 INFO mapreduce.Job:  map 63% reduce 0%
20/10/19 10:49:57 INFO mapreduce.Job:  map 100% reduce 0%
20/10/19 10:50:04 INFO mapreduce.Job:  map 100% reduce 100%
20/10/19 10:50:05 INFO mapreduce.Job: Job job_1602414795136_0814 completed successfully
20/10/19 10:50:05 INFO mapreduce.Job: Counters: 53
        File System Counters
                FILE: Number of bytes read=358
                FILE: Number of bytes written=4199876
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=4166
                HDFS: Number of bytes written=215
                HDFS: Number of read operations=69
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=3
        Job Counters
                Launched map tasks=16
                Launched reduce tasks=1
                Data-local map tasks=16
                Total time spent by all maps in occupied slots (ms)=347007
                Total time spent by all reduces in occupied slots (ms)=21000
                Total time spent by all map tasks (ms)=115669
                Total time spent by all reduce tasks (ms)=5250
                Total vcore-milliseconds taken by all map tasks=115669
                Total vcore-milliseconds taken by all reduce tasks=5250
                Total megabyte-milliseconds taken by all map tasks=177667584
                Total megabyte-milliseconds taken by all reduce tasks=10752000
        Map-Reduce Framework
                Map input records=16
                Map output records=32
                Map output bytes=288
                Map output materialized bytes=448
                Input split bytes=2278
                Combine input records=0
                Combine output records=0
                Reduce input groups=2
                Reduce shuffle bytes=448
                Reduce input records=32
                Reduce output records=0
                Spilled Records=64
                Shuffled Maps =16
                Failed Shuffles=0
                Merged Map outputs=16
                GC time elapsed (ms)=2749
                CPU time spent (ms)=39150
                Physical memory (bytes) snapshot=18790731776
                Virtual memory (bytes) snapshot=58159996928
                Total committed heap usage (bytes)=19538116608
                Peak Map Physical memory (bytes)=1167659008
                Peak Map Virtual memory (bytes)=3395858432
                Peak Reduce Physical memory (bytes)=292061184
                Peak Reduce Virtual memory (bytes)=3869880320
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=1888
        File Output Format Counters
                Bytes Written=97
Job Finished in 29.04 seconds
Estimated value of Pi is 3.14159155000000000000
```

## 1.5 GB GraySort example
### Generate 10 GB of data, which is stored to your home directory at /user/apignerol/data/10GB-sort-input
```
-sh-4.2$ yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar \teragen -Dmapred.map.tasks=50 10000000 /user/apignerol/data/10GB-sort-input

20/10/19 10:53:39 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.100.24:10200
20/10/19 10:53:39 INFO hdfs.DFSClient: Created token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603097619365, maxDate=1603702419365, sequenceNumber=1252, masterKeyId=23 on ha-hdfs:efrei
20/10/19 10:53:39 INFO security.TokenCache: Got dt for hdfs://efrei; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603097619365, maxDate=1603702419365, sequenceNumber=1252, masterKeyId=23)
20/10/19 10:53:39 INFO client.ConfiguredRMFailoverProxyProvider: Failing over to rm2
20/10/19 10:53:39 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /user/apignerol/.staging/job_1602414795136_0815
20/10/19 10:53:39 INFO terasort.TeraGen: Generating 10000000 using 50
20/10/19 10:53:39 INFO mapreduce.JobSubmitter: number of splits:50
20/10/19 10:53:39 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1602414795136_0815
20/10/19 10:53:39 INFO mapreduce.JobSubmitter: Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603097619365, maxDate=1603702419365, sequenceNumber=1252, masterKeyId=23)]
20/10/19 10:53:40 INFO conf.Configuration: found resource resource-types.xml at file:/etc/hadoop/3.1.5.0-152/0/resource-types.xml
20/10/19 10:53:40 INFO impl.TimelineClientImpl: Timeline service address: hadoop-master03.efrei.online:8190
20/10/19 10:53:40 INFO impl.YarnClientImpl: Submitted application application_1602414795136_0815
20/10/19 10:53:40 INFO mapreduce.Job: The url to track the job: https://hadoop-master02.efrei.online:8090/proxy/application_1602414795136_0815/
20/10/19 10:53:40 INFO mapreduce.Job: Running job: job_1602414795136_0815
20/10/19 10:53:48 INFO mapreduce.Job: Job job_1602414795136_0815 running in uber mode : false
20/10/19 10:53:48 INFO mapreduce.Job:  map 0% reduce 0%
20/10/19 10:53:58 INFO mapreduce.Job:  map 2% reduce 0%
20/10/19 10:53:59 INFO mapreduce.Job:  map 12% reduce 0%
20/10/19 10:54:00 INFO mapreduce.Job:  map 36% reduce 0%
20/10/19 10:54:01 INFO mapreduce.Job:  map 44% reduce 0%
20/10/19 10:54:02 INFO mapreduce.Job:  map 52% reduce 0%
20/10/19 10:54:03 INFO mapreduce.Job:  map 60% reduce 0%
20/10/19 10:54:04 INFO mapreduce.Job:  map 62% reduce 0%
20/10/19 10:54:05 INFO mapreduce.Job:  map 76% reduce 0%
20/10/19 10:54:06 INFO mapreduce.Job:  map 100% reduce 0%
20/10/19 10:54:07 INFO mapreduce.Job: Job job_1602414795136_0815 completed successfully
20/10/19 10:54:07 INFO mapreduce.Job: Counters: 33
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=12315140
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=4247
                HDFS: Number of bytes written=1000000000
                HDFS: Number of read operations=300
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=100
        Job Counters
                Launched map tasks=50
                Other local map tasks=50
                Total time spent by all maps in occupied slots (ms)=754353
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=251451
                Total vcore-milliseconds taken by all map tasks=251451
                Total megabyte-milliseconds taken by all map tasks=386228736
        Map-Reduce Framework
                Map input records=10000000
                Map output records=10000000
                Input split bytes=4247
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=5143
                CPU time spent (ms)=152970
                Physical memory (bytes) snapshot=12788146176
                Virtual memory (bytes) snapshot=169727807488
                Total committed heap usage (bytes)=14428930048
                Peak Map Physical memory (bytes)=264073216
                Peak Map Virtual memory (bytes)=3400929280
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=21472776955442690
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=1000000000
```
### Use the following command to sort the data
```
-sh-4.2$ yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar \terasort -Dmapred.map.tasks=50 -Dmapred.reduce.tasks=25 /user/apignerol/data/10GB-sort-input /user/apignerol/data/10GB-sort-sorted

20/10/19 10:59:50 INFO terasort.TeraSort: starting
20/10/19 10:59:51 INFO hdfs.DFSClient: Created token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603097991402, maxDate=1603702791402, sequenceNumber=1253, masterKeyId=23 on ha-hdfs:efrei
20/10/19 10:59:51 INFO security.TokenCache: Got dt for hdfs://efrei; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603097991402, maxDate=1603702791402, sequenceNumber=1253, masterKeyId=23)
20/10/19 10:59:51 INFO input.FileInputFormat: Total input files to process : 50
Spent 325ms computing base-splits.
Spent 1ms computing TeraScheduler splits.
Computing input splits took 326ms
Sampling 10 splits of 50
Making 25 from 100000 sampled records
Computing parititions took 318ms
Spent 645ms computing partitions.
20/10/19 10:59:52 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.100.24:10200
20/10/19 10:59:52 INFO client.ConfiguredRMFailoverProxyProvider: Failing over to rm2
20/10/19 10:59:52 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /user/apignerol/.staging/job_1602414795136_0816
20/10/19 10:59:52 INFO mapreduce.JobSubmitter: number of splits:50
20/10/19 10:59:52 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1602414795136_0816
20/10/19 10:59:52 INFO mapreduce.JobSubmitter: Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603097991402, maxDate=1603702791402, sequenceNumber=1253, masterKeyId=23)]
20/10/19 10:59:52 INFO conf.Configuration: found resource resource-types.xml at file:/etc/hadoop/3.1.5.0-152/0/resource-types.xml
20/10/19 10:59:52 INFO impl.TimelineClientImpl: Timeline service address: hadoop-master03.efrei.online:8190
20/10/19 10:59:53 INFO impl.YarnClientImpl: Submitted application application_1602414795136_0816
20/10/19 10:59:53 INFO mapreduce.Job: The url to track the job: https://hadoop-master02.efrei.online:8090/proxy/application_1602414795136_0816/
20/10/19 10:59:53 INFO mapreduce.Job: Running job: job_1602414795136_0816
20/10/19 11:00:01 INFO mapreduce.Job: Job job_1602414795136_0816 running in uber mode : false
20/10/19 11:00:01 INFO mapreduce.Job:  map 0% reduce 0%
20/10/19 11:00:10 INFO mapreduce.Job:  map 16% reduce 0%
20/10/19 11:00:20 INFO mapreduce.Job:  map 52% reduce 0%
20/10/19 11:00:21 INFO mapreduce.Job:  map 100% reduce 0%
20/10/19 11:00:22 INFO mapreduce.Job:  map 100% reduce 2%
20/10/19 11:00:23 INFO mapreduce.Job:  map 100% reduce 3%
20/10/19 11:00:24 INFO mapreduce.Job:  map 100% reduce 15%
20/10/19 11:00:25 INFO mapreduce.Job:  map 100% reduce 68%
20/10/19 11:00:26 INFO mapreduce.Job:  map 100% reduce 96%
20/10/19 11:00:27 INFO mapreduce.Job:  map 100% reduce 100%
20/10/19 11:00:27 INFO mapreduce.Job: Job job_1602414795136_0816 completed successfully
20/10/19 11:00:28 INFO mapreduce.Job: Counters: 54
        File System Counters
                FILE: Number of bytes read=1040013350
                FILE: Number of bytes written=2098615605
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=1000006300
                HDFS: Number of bytes written=1000000000
                HDFS: Number of read operations=275
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=50
        Job Counters
                Launched map tasks=50
                Launched reduce tasks=25
                Other local map tasks=4
                Data-local map tasks=46
                Total time spent by all maps in occupied slots (ms)=2363568
                Total time spent by all reduces in occupied slots (ms)=916284
                Total time spent by all map tasks (ms)=787856
                Total time spent by all reduce tasks (ms)=229071
                Total vcore-milliseconds taken by all map tasks=787856
                Total vcore-milliseconds taken by all reduce tasks=229071
                Total megabyte-milliseconds taken by all map tasks=1210146816
                Total megabyte-milliseconds taken by all reduce tasks=469137408
        Map-Reduce Framework
                Map input records=10000000
                Map output records=10000000
                Map output bytes=1020000000
                Map output materialized bytes=1040007500
                Input split bytes=6300
                Combine input records=0
                Combine output records=0
                Reduce input groups=10000000
                Reduce shuffle bytes=1040007500
                Reduce input records=10000000
                Reduce output records=10000000
                Spilled Records=20000000
                Shuffled Maps =1250
                Failed Shuffles=0
                Merged Map outputs=1250
                GC time elapsed (ms)=18988
                CPU time spent (ms)=447690
                Physical memory (bytes) snapshot=68165197824
                Virtual memory (bytes) snapshot=267096735744
                Total committed heap usage (bytes)=69172985856
                Peak Map Physical memory (bytes)=1205567488
                Peak Map Virtual memory (bytes)=3407986688
                Peak Reduce Physical memory (bytes)=373694464
                Peak Reduce Virtual memory (bytes)=3892629504
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=1000000000
        File Output Format Counters
                Bytes Written=1000000000
20/10/19 11:00:28 INFO terasort.TeraSort: done
```
### Use the following command to validate the data generated by the sort
```
-sh-4.2$ yarn jar /usr/hdp/current/hadoop-mapreduce-client/hadoop-mapreduce-examples.jar \teravalidate -Dmapred.map.tasks=50 -Dmapred.reduce.tasks=25 /user/apignerol/data/10GB-sort-sorted /user/apignerol/data/10GB-sort-final

20/10/19 11:04:27 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.100.24:10200
20/10/19 11:04:27 INFO hdfs.DFSClient: Created token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603098267314, maxDate=1603703067314, sequenceNumber=1255, masterKeyId=23 on ha-hdfs:efrei
20/10/19 11:04:27 INFO security.TokenCache: Got dt for hdfs://efrei; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603098267314, maxDate=1603703067314, sequenceNumber=1255, masterKeyId=23)
org.apache.hadoop.mapred.FileAlreadyExistsException: Output directory hdfs://efrei/user/apignerol/data/10GB-sort-final already exists
        at org.apache.hadoop.mapreduce.lib.output.FileOutputFormat.checkOutputSpecs(FileOutputFormat.java:164)
        at org.apache.hadoop.mapreduce.JobSubmitter.checkSpecs(JobSubmitter.java:277)
        at org.apache.hadoop.mapreduce.JobSubmitter.submitJobInternal(JobSubmitter.java:143)
        at org.apache.hadoop.mapreduce.Job$11.run(Job.java:1570)
        at org.apache.hadoop.mapreduce.Job$11.run(Job.java:1567)
        at java.security.AccessController.doPrivileged(Native Method)
        at javax.security.auth.Subject.doAs(Subject.java:422)
        at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1730)
        at org.apache.hadoop.mapreduce.Job.submit(Job.java:1567)
        at org.apache.hadoop.mapreduce.Job.waitForCompletion(Job.java:1588)
        at org.apache.hadoop.examples.terasort.TeraValidate.run(TeraValidate.java:178)
        at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:76)
        at org.apache.hadoop.examples.terasort.TeraValidate.main(TeraValidate.java:185)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:498)
        at org.apache.hadoop.util.ProgramDriver$ProgramDescription.invoke(ProgramDriver.java:71)
        at org.apache.hadoop.util.ProgramDriver.run(ProgramDriver.java:144)
        at org.apache.hadoop.examples.ExampleDriver.main(ExampleDriver.java:74)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:498)
        at org.apache.hadoop.util.RunJar.run(RunJar.java:318)
        at org.apache.hadoop.util.RunJar.main(RunJar.java:232)
```

# 2 MapReduce2

## 2.3.1 Map step: Mapper.py
### Python program
```Python
#!/usr/bin/env python
"""mapper.py"""

import sys

for line in sys.stdin:
        line = line.strip()

        words = line.split()

        for word in words:
                print '%s\t%s' % (word, 1)
```
### Test to check the Mapper
```
-sh-4.2$ chmod +x mapper.py
-sh-4.2$ echo "foo foo quux labs foo bar quux" | /home/apignerol/mapper.py
foo     1
foo     1
quux    1
labs    1
foo     1
bar     1
quux    1
```

## 2.3.2 Reduce step: Reducer.py
### Python program
```Python
#!/usr/bin/env python
"""reducer.py"""

from operator import itemgetter
import sys

current_word = None
current_count = 0
word = None

for line in sys.stdin:
        line = line.strip()

        word, count = line.split('\t', 1)

        count = int(count)

        if current_word == word:
                current_count += count
        else:
                if current_word:
                        print '%s\t%s' % (current_word, current_count)
                current_word = word
                current_count = count

if current_word == word:
        print '%s\t%s' % (current_word, current_count)
```
### Test to check the Reducer
```
-sh-4.2$ chmod +x reducer.py
-sh-4.2$ echo "foo foo quux labs foo bar quux" | /home/apignerol/mapper.py | sort -k1,1 | /home/apignerol/reducer.py
bar     1
foo     3
labs    1
quux    2
```

## 2.4 Running the Python Code on Hadoop
### 2.4.1: Download the input data
```
-sh-4.2$ wget www.gutenberg.org/cache/epub/20417/pg20417.txt
-sh-4.2$ wget www.gutenberg.org/files/5000/5000-8.txt
-sh-4.2$ wget www.gutenberg.org/files/4300/4300-0.txt
```
### 2.4.2: Copy local to example to HDFS
```
-sh-4.2$ hdfs dfs -copyFromLocal pg20417.txt
-sh-4.2$ hdfs dfs -copyFromLocal 4300-0.txt
-sh-4.2$ hdfs dfs -copyFromLocal 5000-8.txt

-sh-4.2$ hdfs dfs -mkdir gutenberg
-sh-4.2$ hdfs dfs -mv pg20417.txt gutenberg/pg20417.txt
-sh-4.2$ hdfs dfs -mv 4300-0.txt gutenberg/4300-0.txt
-sh-4.2$ hdfs dfs -mv 5000-8.txt gutenberg/5000-8.txt
```
### 2.4.3: Run the MapReduce job
```
-sh-4.2$ hadoop jar /usr/hdp/3.1.5.0-152/hadoop-mapreduce/hadoop-streaming.jar -file /home/apignerol/mapper.py -mapper /home/apignerol/mapper.py -file /home/apignerol/reducer.py -reducer /home/apignerol/reducer.py -input gutenberg/* -output gutenberg-output

20/10/19 11:54:20 WARN streaming.StreamJob: -file option is deprecated, please use generic option -files instead.
packageJobJar: [/home/apignerol/mapper.py, /home/apignerol/reducer.py] [/usr/hdp/3.1.5.0-152/hadoop-mapreduce/hadoop-streaming-3.1.1.3.1.5.0-152.jar] /tmp/streamjob7751088370270472135.jar tmpDir=null
20/10/19 11:54:20 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.100.24:10200
20/10/19 11:54:20 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.100.24:10200
20/10/19 11:54:21 INFO hdfs.DFSClient: Created token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603101261093, maxDate=1603706061093, sequenceNumber=1258, masterKeyId=23 on ha-hdfs:efrei
20/10/19 11:54:21 INFO security.TokenCache: Got dt for hdfs://efrei; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603101261093, maxDate=1603706061093, sequenceNumber=1258, masterKeyId=23)
20/10/19 11:54:21 INFO client.ConfiguredRMFailoverProxyProvider: Failing over to rm2
20/10/19 11:54:21 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /user/apignerol/.staging/job_1602414795136_0820
20/10/19 11:54:21 INFO mapred.FileInputFormat: Total input files to process : 3
20/10/19 11:54:21 INFO mapreduce.JobSubmitter: number of splits:3
20/10/19 11:54:21 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1602414795136_0820
20/10/19 11:54:21 INFO mapreduce.JobSubmitter: Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1603101261093, maxDate=1603706061093, sequenceNumber=1258, masterKeyId=23)]
20/10/19 11:54:21 INFO conf.Configuration: found resource resource-types.xml at file:/etc/hadoop/3.1.5.0-152/0/resource-types.xml
20/10/19 11:54:21 INFO impl.TimelineClientImpl: Timeline service address: hadoop-master03.efrei.online:8190
20/10/19 11:54:22 INFO impl.YarnClientImpl: Submitted application application_1602414795136_0820
20/10/19 11:54:22 INFO mapreduce.Job: The url to track the job: https://hadoop-master02.efrei.online:8090/proxy/application_1602414795136_0820/
20/10/19 11:54:22 INFO mapreduce.Job: Running job: job_1602414795136_0820
20/10/19 11:54:31 INFO mapreduce.Job: Job job_1602414795136_0820 running in uber mode : false
20/10/19 11:54:31 INFO mapreduce.Job:  map 0% reduce 0%
20/10/19 11:54:39 INFO mapreduce.Job:  map 33% reduce 0%
20/10/19 11:54:40 INFO mapreduce.Job:  map 100% reduce 0%
20/10/19 11:54:47 INFO mapreduce.Job:  map 100% reduce 100%
20/10/19 11:54:47 INFO mapreduce.Job: Job job_1602414795136_0820 completed successfully
20/10/19 11:54:47 INFO mapreduce.Job: Counters: 53
        File System Counters
                FILE: Number of bytes read=6096860
                FILE: Number of bytes written=13194301
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=3690200
                HDFS: Number of bytes written=887453
                HDFS: Number of read operations=14
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=2
        Job Counters
                Launched map tasks=3
                Launched reduce tasks=1
                Data-local map tasks=3
                Total time spent by all maps in occupied slots (ms)=55659
                Total time spent by all reduces in occupied slots (ms)=18092
                Total time spent by all map tasks (ms)=18553
                Total time spent by all reduce tasks (ms)=4523
                Total vcore-milliseconds taken by all map tasks=18553
                Total vcore-milliseconds taken by all reduce tasks=4523
                Total megabyte-milliseconds taken by all map tasks=28497408
                Total megabyte-milliseconds taken by all reduce tasks=9263104
        Map-Reduce Framework
                Map input records=78753
                Map output records=630075
                Map output bytes=4836704
                Map output materialized bytes=6096872
                Input split bytes=301
                Combine input records=0
                Combine output records=0
                Reduce input groups=82555
                Reduce shuffle bytes=6096872
                Reduce input records=630075
                Reduce output records=82555
                Spilled Records=1260150
                Shuffled Maps =3
                Failed Shuffles=0
                Merged Map outputs=3
                GC time elapsed (ms)=362
                CPU time spent (ms)=12630
                Physical memory (bytes) snapshot=3787780096
                Virtual memory (bytes) snapshot=14064865280
                Total committed heap usage (bytes)=3932684288
                Peak Map Physical memory (bytes)=1155145728
                Peak Map Virtual memory (bytes)=3395457024
                Peak Reduce Physical memory (bytes)=326217728
                Peak Reduce Virtual memory (bytes)=3880828928
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=3689899
        File Output Format Counters
                Bytes Written=887453
20/10/19 11:54:47 INFO streaming.StreamJob: Output directory: gutenberg-output
```
### 2.4.5: Improved Mapper
```Python
#!/usr/bin/env python
"""A more advance Mapper, using Python iterators and generators"""

import sys

def read_input(file):
        for line in file:
                yield line.split()

def main(separator='\t'):
        data = read_input(sys.stdin)

        for words in data:

                for word in words:
                        print "%s%s%d" % (word, separator, 1)

if __name__ == "__main__":
        main()
```
### Testing mapper to script on local
```
-sh-4.2$ echo "foo foo quux labs foo bar quux" | /home/apignerol/mapper.py
foo     1
foo     1
quux    1
labs    1
foo     1
bar     1
quux    1
```
### 2.4.6: Improved Reducer
```Python
#!/usr/bin/env python
"""A more advanced Reducer, using Python iterators and generators"""

from itertools import groupby
from operator import itemgetter
import sys

def read_mapper_output(file, separator='\t'):
        for line in file:
                yield line.rstrip().split(separator, 1)

def main(separator = '\t'):
        data = read_mapper_output(sys.stdin, separator=separator)

        for current_word, group in groupby(data, itemgetter(0)):
                total_count = sum( int(count) for current_word, count in group)
                print "%s%s%d" % (current_word, separator, total_count)

if __name__ == "__main__":
        main()
```
### Testing both scripts on local
```
-sh-4.2$ echo "foo foo quux labs foo bar quux" | /home/apignerol/mapper.py | sort -k1,1 | /home/apignerol/reducer.py
bar     1
foo     3
labs    1
quux    2
```
## 2.4 bis: Testing both scripts on HDFS
```
-sh-4.2$ chmod 777 new-reducer.py
-sh-4.2$ chmod 777 new-mapper.py


-sh-4.2$ hadoop jar /usr/hdp/3.1.5.0-152/hadoop-mapreduce/hadoop-streaming.jar -file /home/apignerol/mapper.py -mapper /home/apignerol/mapper.py  -file /home/apignerol/new-reducer.py -reducer /home/apginerol/new-reducer.py -input gutenberg/* -output gutenberg-new-output

20/10/19 14:15:09 WARN streaming.StreamJob: -file option is deprecated, please use generic option -files instead.
packageJobJar: [/home/apignerol/mapper.py, /home/apignerol/new-reducer.py] [/usr/hdp/3.1.5.0-152/hadoop-mapreduce/hadoop-streaming-3.1.1.3.1.5.0-152.jar] /tmp/streamjob7031560925322871651.jar tmpDir=null
220/10/14 18:37:23 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.100.24:10200
20/10/14 18:37:23 INFO client.AHSProxy: Connecting to Application History server at hadoop-master03.efrei.online/163.172.100.24:10200
20/10/14 18:37:24 INFO hdfs.DFSClient: Created token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1602693444107, maxDate=1603298244107, sequenceNumber=641, masterKeyId=18 on ha-hdfs:efrei
20/10/14 18:37:24 INFO security.TokenCache: Got dt for hdfs://efrei; Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1602693444107, maxDate=1603298244107, sequenceNumber=641, masterKeyId=18)
20/10/14 18:37:24 INFO client.ConfiguredRMFailoverProxyProvider: Failing over to rm2
20/10/14 18:37:24 INFO mapreduce.JobResourceUploader: Disabling Erasure Coding for path: /user/apignerol/.staging/job_1602414795136_0363
20/10/14 18:37:24 INFO mapred.FileInputFormat: Total input files to process : 3
20/10/14 18:37:24 INFO mapreduce.JobSubmitter: number of splits:3
20/10/14 18:37:24 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1602414795136_0363
20/10/14 18:37:24 INFO mapreduce.JobSubmitter: Executing with tokens: [Kind: HDFS_DELEGATION_TOKEN, Service: ha-hdfs:efrei, Ident: (token for apignerol: HDFS_DELEGATION_TOKEN owner=apignerol@EFREI.ONLINE, renewer=yarn, realUser=, issueDate=1602693444107, maxDate=1603298244107, sequenceNumber=641, masterKeyId=18)]
20/10/14 18:37:24 INFO conf.Configuration: found resource resource-types.xml at file:/etc/hadoop/3.1.5.0-152/0/resource-types.xml
20/10/14 18:37:24 INFO impl.TimelineClientImpl: Timeline service address: hadoop-master03.efrei.online:8190
20/10/14 18:37:25 INFO impl.YarnClientImpl: Submitted application application_1602414795136_0363
20/10/14 18:37:25 INFO mapreduce.Job: The url to track the job: https://hadoop-master02.efrei.online:8090/proxy/application_1602414795136_0363/
20/10/14 18:37:25 INFO mapreduce.Job: Running job: job_1602414795136_0363
20/10/14 18:37:34 INFO mapreduce.Job: Job job_1602414795136_0363 running in uber mode : false
20/10/14 18:37:34 INFO mapreduce.Job:  map 0% reduce 0%
20/10/14 18:37:41 INFO mapreduce.Job:  map 100% reduce 0%
20/10/14 18:37:50 INFO mapreduce.Job:  map 100% reduce 100%
20/10/14 18:37:50 INFO mapreduce.Job: Job job_1602414795136_0363 completed successfully
20/10/14 18:37:50 INFO mapreduce.Job: Counters: 53
        File System Counters
                FILE: Number of bytes read=6096860
                FILE: Number of bytes written=13194205
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=3690191
                HDFS: Number of bytes written=887453
                HDFS: Number of read operations=14
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=2
        Job Counters
                Launched map tasks=3
                Launched reduce tasks=1
                Data-local map tasks=3
                Total time spent by all maps in occupied slots (ms)=50898
                Total time spent by all reduces in occupied slots (ms)=25372
                Total time spent by all map tasks (ms)=16966
                Total time spent by all reduce tasks (ms)=6343
                Total vcore-milliseconds taken by all map tasks=16966
                Total vcore-milliseconds taken by all reduce tasks=6343
                Total megabyte-milliseconds taken by all map tasks=26059776
                Total megabyte-milliseconds taken by all reduce tasks=12990464
        Map-Reduce Framework
                Map input records=78753
                Map output records=630075
                Map output bytes=4836704
                Map output materialized bytes=6096872
                Input split bytes=292
                Combine input records=0
                Combine output records=0
                Reduce input groups=82555
                Reduce shuffle bytes=6096872
                Reduce input records=630075
                Reduce output records=82555
                Spilled Records=1260150
                Shuffled Maps =3
                Failed Shuffles=0
                Merged Map outputs=3
                GC time elapsed (ms)=388
                CPU time spent (ms)=12700
                Physical memory (bytes) snapshot=3792629760
                Virtual memory (bytes) snapshot=14058168320
                Total committed heap usage (bytes)=3945791488
                Peak Map Physical memory (bytes)=1157844992
                Peak Map Virtual memory (bytes)=3394277376
                Peak Reduce Physical memory (bytes)=326012928
                Peak Reduce Virtual memory (bytes)=3876859904
        Shuffle Errors
                BAD_ID=0
                CONNECTION=0
                IO_ERROR=0
                WRONG_LENGTH=0
                WRONG_MAP=0
                WRONG_REDUCE=0
        File Input Format Counters
                Bytes Read=3689899
        File Output Format Counters
                Bytes Written=887453
20/10/14 18:37:50 INFO streaming.StreamJob: Output directory: gutenberg-output
```