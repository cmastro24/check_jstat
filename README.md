# check_jstat
Non intrusive nagios check for java JVMs

This is currently a **DRAFT**

## Output
The code will output a small message informing the user what the current state of the JVM is.
It will return a nagios return code so that the state of the check will change if the user defined thresholds are breached.
It will return the following performance metrics:

### totalHeap
This metric is the current total heap **usage** and the maximum size of the heap (set by Xmx).

## heapBalloon
This metric is the current size of the heap in use by the JVM. This will vary if Xms is not the same as Xmx because the JVM will dynamically resize it.

## edenUsage
This metric shows part of the young generation space. It is the usage of the heap space that is used when creating new objects. This is where a minor GC will look to regain space.

## survivorUsage
This metric shows the other part of the young generation space (see edenUsage). If is the usage of the heap space that has survived a minor GC event.

## tenuredUsage
This metric shows the old generation space usage. It is the usage of the heap space that is for objects which survive several minor GC events. These are where the long lived objects are stored. This is where a major GC will look to regain memory.

## minorGCAmount
This metric is a simple count of the amount of times a minor GC has been triggered.

## minorGCTime
This metric is the amount of time that minor GC events have taken within this JVM.

## majorGCAmount
This metric is a simple count of the amount of times a major GC has been triggered.

## majorGCTime
This metric is the amount of time that major GC events have taken within this JVM.

## Requirements
* java (provides jps and jstat)
* Bash
* sudo (if user running the check != to user running the jvm)
* - !requiretty
* awk
* egrep
* uniq
