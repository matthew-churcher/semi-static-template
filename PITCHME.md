# Influxdb: what you need to know!
## a crunchy presentation
---
# why are we here?
- Influxdb has been unstable
- not for the first time
- took too long to resolve
- metrics are important

---
# why was it unstable
* A single measure had excessive cardinality
* A tag was accidently added for a GUID which had over a million keys
* total cardinality in excess of 1.5 million
* Influxdb holds indexes in memory
* Influxdb killed with OOM
* Internal processes also don't scale

---
# what is cardinality
- number of unique timeseries
- 10 hostnames + 10 accounts = 100
- 10 hostnames + 10 fqdn = 10

---
# what is too high?
- 1 million is too much
- 6 Tags with just 10 unique values
- just 3 tags with 100 unique values
- just 2 tags with 1K unique values
- just 1 tags with 1M: (don't do it)
- unique tags
-  **GUIDS**, ProcessIDs & hashes

---
# why so long to resolve?
- support supposed to be 24/7 but wasn't
- support team growing, not experienced
- support upgraded cluster with more memory  but didn't initially identify cardinality issue
- pretty much left to us find source of cardinality
- limited visibility into influxdb
- data 2 weeks to expire
- avoiding causing more problems

---
# what we did...
- meetings with support engineer
- kully had meeting with support manager
- fixed likely culprits
- waited...
- wrote custom tooling
- dropped offending measurement

---
# What's coming?
- Co-monitoring dashboards for influxdb
- and kapacitor (I've been asked for input from design team)
- UK based 24/7 support (at some point)
- influxdb support for monitoring cardinality
- alerts on cardinality ( by us)

---
# the future
- things getting better
- keeping options open
- monitor all the things!
- keep cardinality low
- keeping options open
- use other tools when appropriate ( logging, Aws Kinesis with Athena)

---
# questions

@crunchy

👯👯👯

