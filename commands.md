# Merge von zwei Ordnern
Ordner1 anlegen
Ordner2 anlegen
Ordner1 mit 2 beispieldateien von Gutenberg.org befüllen
Ordner2 mit 3 beispieldateien von Gutenberg.org befüllen
Merge Befehl ausführen
Ergebnis auflisten

Ordner erstellen

```
[cloudera@quickstart ~]$ hdfs dfs -mkdir BDE/
[cloudera@quickstart ~]$ hdfs dfs -mkdir BDE/zusatzaufgaben/
[cloudera@quickstart ~]$ hdfs dfs -mkdir BDE/zusatzaufgaben/Kapitel_1_1/
[cloudera@quickstart ~]$ hdfs dfs -mkdir BDE/zusatzaufgaben/Kapitel_1_1/mergeExample
```

Überprüfen ob der Ordner „mergeExample“ erstellt wurde

```
[cloudera@quickstart ~]$ hadoop fs -ls BDE/zusatzaufgaben/Kapitel_1_1/
Found 1 items
drwxr-xr-x   - cloudera cloudera          0 2016-01-11 11:31 mergeExample
```

Ordner erstellen

```
[cloudera@quickstart ~]$ hadoop fs -mkdir BDE/zusatzaufgaben/Kapitel_1_1/mergeExample/FilesToMerge
```

Überprüfen ob der Ordner „FilesToMerge“ erstellt wurde

```

[cloudera@quickstart ~]$ hadoop fs -ls BDE/zusatzaufgaben/Kapitel_1_1/mergeExample
Found 1 items
drwxr-xr-x   - cloudera cloudera          0 2016-01-11 11:50 BDE/zusatzaufgaben/Kapitel_1_1/mergeExample/FilesToMerge
```

Beispiel Dateien downloaden:

```
#!shell
[cloudera@quickstart ~]$ wget http://www.gutenberg.org/cache/epub/2701/pg2701.txt
--2016-01-11 11:41:45--  http://www.gutenberg.org/cache/epub/2701/pg2701.txt
Resolving www.gutenberg.org... 152.19.134.47
Connecting to www.gutenberg.org|152.19.134.47|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1257296 (1.2M) [text/plain]
Saving to: “pg2701.txt”
100%[=======================================================================================================================================>] 1,257,296    294K/s   in 4.4s    
    
2016-01-11 11:41:50 (277 KB/s) - “pg2701.txt” saved [1257296/1257296]
```

```
#!shell

[cloudera@quickstart ~]$ wget http://www.gutenberg.org/cache/epub/4300/pg4300.txt
--2016-01-11 11:42:51--  http://www.gutenberg.org/cache/epub/4300/pg4300.txt
Resolving www.gutenberg.org... 152.19.134.47
Connecting to www.gutenberg.org|152.19.134.47|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1573151 (1.5M) [text/plain]
Saving to: “pg4300.txt”

100%[=======================================================================================================================================>] 1,573,151    352K/s   in 4.7s    

2016-01-11 11:42:58 (329 KB/s) - “pg4300.txt” saved [1573151/1573151]
```

Dateien in das HDFS legen

```
#!shell

[cloudera@quickstart ~]$ hadoop fs -put pg2701.txt BDE/zusatzaufgaben/Kapitel_1_1/mergeExample/FilesToMerge
[cloudera@quickstart ~]$ hadoop fs -put pg4300.txt BDE/zusatzaufgaben/Kapitel_1_1/mergeExample/FilesToMerge
```

Überprüfen, ob die Dateien abgelegt wurden

```
#!shell

[cloudera@quickstart ~]$ hadoop fs -ls BDE/zusatzaufgaben/Kapitel_1_1/mergeExample/FilesToMerge
Found 2 items
-rw-r--r--   1 cloudera cloudera    1257296 2016-01-11 12:02 BDE/zusatzaufgaben/Kapitel_1_1/mergeExample/FilesToMerge/pg2701.txt
-rw-r--r--   1 cloudera cloudera    1573151 2016-01-11 12:03 BDE/zusatzaufgaben/Kapitel_1_1/mergeExample/FilesToMerge/pg4300.txt
```

# Merge fehlt noch #
