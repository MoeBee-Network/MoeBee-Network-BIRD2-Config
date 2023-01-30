> This repository is forked from MoeQing-Network/MoeQing-Network-Config

# MoeBee Network | AS139328

The bird2 config for Moebee Network


## Internal Community:

>(139328, <999,  0)            Community for all my node
>
>(139328, <999,  1)            Community only for this node

```
(139328,   1, *)   do not send to ibgp
(139328,   2, *)   do not send to ebgp
(139328,   3, *)   do not send to kernel
(139328,   4, *)   send to kernel but mark unreachable
(139328,   5, *)   send to kernel but mark blackhole
(139328, 101, *)   allow bgp_local_perf
(139328, 201, *)   transit routes
(139328, 202, *)   ixp rs routes
(139328, 203, *)   peer routes
(139328, 204, *)   customer routes
(139328, 209, *)   ibgp routes
```

## Control Community:
```
 Actions:
  * = 0   do not announce to target
  * = 1   prepend 1 to target
  * = 2   prepend 2 to target
  * = 4   prepend 4 to target
  * = 8   prepend 8 to target
 Action target selector:
  * = Action
  (139328, 1*00, 0)            Do action to everyone
  (139328, 1*01, asn)          Don't do action to this asn
  (139328, 1*02, asn)          Do action to this asn
  (139328, 1*10, 0)            Do action to every region
  (139328, 1*11, region_code)  Don't do action to this region
  (139328, 1*12, region_code)  Do action to this region
  (139328, 1019, 0)            Disable (asn, 1010, 0),  (asn, 1011, local_region) as default value
  (139328, 1*20, 0)            Do action to every country
  (139328, 1*21, country_code) Don't do action to this country
  (139328, 1*22, country_code) Do action to this country
  (139328, 1*30, 1)            Do action to upstreams
  (139328, 1*30, 2)            Do action to ixp rs
  (139328, 1*30, 3)            Do action to peers
  (139328, 1*30, 4)            Do action to downstreams
  (139328, 1*30, 8)            Do action to route collectors
```

## Examples:
```
  prepend 11 to AS6939: 
     (139328, 1102, 6939): prepend 1 to AS6939
     (139328, 1202, 6939): prepend 2 to AS6939
     (139328, 1802, 6939): prepend 8 to AS6939
                 Total : 1+2+8 = 11
  prepend 2 to everyone but 6939:
    (139328, 1200, 0):     prepend 2 to everyone
    (139328, 1201, 6939):  don't do this action(prepend 2) to AS6939
  do not announce to anyone: 
    (139328, 1000, 0):     do not announce to everyone
  announce to all locations:
    (139328, 1019, 0):     announce to all locations
  announce in Asia-E only:
    (139328, 1011, 52):    announce to Asia-E location
```

## Informational Community
```
(139328, 10000, region_code)    Received from region
(139328, 10001, country_code)   Received from country
```

## Region code:
```
* 41: Europe
* 42: North America-East
* 43: North America-Central
* 44: North America-West
* 45: Central America
* 46: South America-Central
* 47: South America-West
* 48: Africa-N (above Sahara)
* 49: Africa-S (below Sahara)
* 50: Asia-S (IN, PK, BD)
* 51: Asia-SE (TH, SG, PH, ID, MY)
* 52: Asia-E (JP, KR, TW, HK, CN)
* 53: Pacific&Oceania (AU, NZ, FJ)
* 54: Antarctica
* 55: Asia-N (RU)
* 56: Asia-W (IR, TR, UAE)
* 57: Central Asia (AF, UZ, KZ)
```

## Country code:
ISO-3166 numeric-3 country code

## Credits

* Special thanks [KusakabeShi](https://github.com/KusakabeShi)
