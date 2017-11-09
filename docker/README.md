Setup
=====

```
$ docker build -t gdmello/esrally:0.1 .
$ docker run -it gdmello/esrally:0.1 /bin/bash
root@81a7fb4e76fd:/# esrally list tracks

    ____        ____
   / __ \____ _/ / /_  __
  / /_/ / __ `/ / / / / /
 / _, _/ /_/ / / / /_/ /
/_/ |_|\__,_/_/_/\__, /
                /____/

[INFO] Writing logs to /root/.rally/logs/rally_out_20171011T192610Z.log
Available tracks:

Name        Description                                                                   Documents  Compressed Size    Uncompressed Size    Default Challenge        All Challenges
----------  --------------------------------------------------------------------------  -----------  -----------------  -------------------  -----------------------  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
geonames    Standard track in Rally (11.4M POIs from Geonames)                             11396505  252.4 MB           3.3 GB               append-no-conflicts      append-no-conflicts,append-no-conflicts-index-only,append-no-conflicts-index-only-1-replica,append-sorted-no-conflicts,append-fast-with-conflicts,scripts-only,append-no-conflicts-no-large-terms,search-only
nested      Nested query benchmark using up to 11,203,029 questions from StackOverflow     11203029  663.1 MB           3.4 GB               nested-search-challenge  nested-search-challenge,index-only
geopoint    60.8M POIs from PlanetOSM                                                      60844404  481.9 MB           2.3 GB               append-no-conflicts      append-no-conflicts,append-no-conflicts-index-only,append-no-conflicts-index-only-1-replica,append-fast-with-conflicts
noaa        Daily weather measurement summaries from around the globe.                     33659481  947.3 MB           9.0 GB               append-no-conflicts      append-no-conflicts,append-no-conflicts-index-only
logging     Logging benchmark                                                             247249096  1.2 GB             31.1 GB              append-no-conflicts      append-no-conflicts,append-no-conflicts-index-only,append-no-conflicts-index-only-1-replica,append-sorted-no-conflicts
nyc_taxis   Trip records completed in yellow and green taxis in New York in 2015          165346692  4.5 GB             74.3 GB              append-no-conflicts      append-no-conflicts,append-no-conflicts-index-only,append-sorted-no-conflicts-index-only,append-no-conflicts-index-only-1-replica
percolator  Percolator benchmark based on 2M AOL queries                                    2000000  102.7 kB           104.9 MB             append-no-conflicts      append-no-conflicts,append-no-conflicts-index-only
pmc         Full text benchmark containing 574.199 papers from PMC                           574199  5.5 GB             21.7 GB              append-no-conflicts      append-no-conflicts,append-no-conflicts-index-only,append-no-conflicts-index-only-1-replica,append-sorted-no-conflicts,append-fast-with-conflicts

-------------------------------
[INFO] SUCCESS (took 1 seconds)
-------------------------------
root@81a7fb4e76fd:/#
```

Run A Performance Test
======================
Performance tests in Rally include 'races' around one or more 'tracks'.
```
$ docker run gdmello/esrally:0.1 --track=geopoint --target-hosts=10.7.18.21:31018 --user-tag="test-type:baseline-geopoint-append-no-conflicts" --pipeline=benchmark-only --challenge=append-no-conflicts
$ esrally --track=geopoint --challenge=append-fast-with-conflicts --user-tag= --pipeline=benchmark-only
# run against existing ES cluster
$ esrally --track=nyc_taxis --target-hosts=10.5.5.10:9200,10.5.5.11:9200,10.5.5.12:9200 --pipeline=benchmark-only

