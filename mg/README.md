
# Bonus

Here are the test results without logs, only the results.

It looks like the kernel with mg-LRU only distinguishes three `vm.swappiness` values:
- 2-200 - changing the `vm.swappiness` values in the 2-200 range does not have a noticeable effect on the result.
- 1 - the result with swapines 1 is noticeable, but does not differ much from the cases of installing swapines from the range 2-200
- 0 - no progress regardless of `vm.watermark_scale_factor`

15 tests were performed with different `vm.swappiness` values (1, 2, 10, 100, 200).

The config is still the same, only the values of the `vm.swappiness` are changed.

---

## cache-bench -w 300

```
cache-bench -w 300
cache-bench -r 25000
```

#### Results of tests execution with mg-LRU

```C
# vm.swappiness=200

read 25000.0M in 83.3s (avg 300.0M/s); src: 300 files, 300.0M
read 25000.0M in 79.4s (avg 314.8M/s); src: 300 files, 300.0M
read 25000.0M in 82.2s (avg 304.2M/s); src: 300 files, 300.0M
read 25000.0M in 79.5s (avg 314.6M/s); src: 300 files, 300.0M
read 25000.0M in 80.3s (avg 311.3M/s); src: 300 files, 300.0M
read 25000.0M in 83.9s (avg 298.0M/s); src: 300 files, 300.0M
read 25000.0M in 100.8s (avg 248.0M/s); src: 300 files, 300.0M
read 25000.0M in 81.7s (avg 306.1M/s); src: 300 files, 300.0M
read 25000.0M in 83.4s (avg 299.9M/s); src: 300 files, 300.0M
read 25000.0M in 98.7s (avg 253.2M/s); src: 300 files, 300.0M
read 25000.0M in 86.7s (avg 288.4M/s); src: 300 files, 300.0M
read 25000.0M in 86.3s (avg 289.7M/s); src: 300 files, 300.0M
read 25000.0M in 98.1s (avg 254.8M/s); src: 300 files, 300.0M
read 25000.0M in 85.0s (avg 294.0M/s); src: 300 files, 300.0M
read 25000.0M in 87.4s (avg 286.1M/s); src: 300 files, 300.0M

# (83.3+79.4+82.2+79.5+80.3+83.9+100.8+81.7+83.4+98.7+86.7+86.3+98.1+85.0+87.4)/15
# = 86.4
```

```C
# vm.swappiness=100

read 25000.0M in 82.1s (avg 304.5M/s); src: 300 files, 300.0M
read 25000.0M in 96.2s (avg 259.9M/s); src: 300 files, 300.0M
read 25000.0M in 78.6s (avg 318.0M/s); src: 300 files, 300.0M
read 25000.0M in 80.6s (avg 310.1M/s); src: 300 files, 300.0M
read 25000.0M in 81.4s (avg 307.0M/s); src: 300 files, 300.0M
read 25000.0M in 87.8s (avg 284.8M/s); src: 300 files, 300.0M
read 25000.0M in 101.2s (avg 247.1M/s); src: 300 files, 300.0M
read 25000.0M in 86.0s (avg 290.8M/s); src: 300 files, 300.0M
read 25000.0M in 85.5s (avg 292.5M/s); src: 300 files, 300.0M
read 25000.0M in 86.6s (avg 288.5M/s); src: 300 files, 300.0M
read 25000.0M in 85.8s (avg 291.3M/s); src: 300 files, 300.0M
read 25000.0M in 98.0s (avg 255.0M/s); src: 300 files, 300.0M
read 25000.0M in 87.0s (avg 287.4M/s); src: 300 files, 300.0M
read 25000.0M in 85.6s (avg 292.1M/s); src: 300 files, 300.0M
read 25000.0M in 87.2s (avg 286.7M/s); src: 300 files, 300.0M

# (82.1+96.2+78.6+80.6+81.4+87.8+101.2+86.0+85.5+86.6+85.8+98.0+87.0+85.6+87.2)/15
# = 87.3
```

```C
# vm.swappiness=10

read 25000.0M in 79.9s (avg 313.0M/s); src: 300 files, 300.0M
read 25000.0M in 77.4s (avg 323.0M/s); src: 300 files, 300.0M
read 25000.0M in 81.9s (avg 305.2M/s); src: 300 files, 300.0M
read 25000.0M in 82.9s (avg 301.7M/s); src: 300 files, 300.0M
read 25000.0M in 78.8s (avg 317.4M/s); src: 300 files, 300.0M
read 25000.0M in 85.7s (avg 291.7M/s); src: 300 files, 300.0M
read 25000.0M in 85.2s (avg 293.3M/s); src: 300 files, 300.0M
read 25000.0M in 85.4s (avg 292.7M/s); src: 300 files, 300.0M
read 25000.0M in 86.8s (avg 288.0M/s); src: 300 files, 300.0M
read 25000.0M in 99.0s (avg 252.5M/s); src: 300 files, 300.0M
read 25000.0M in 84.9s (avg 294.6M/s); src: 300 files, 300.0M
read 25000.0M in 100.9s (avg 247.7M/s); src: 300 files, 300.0M
read 25000.0M in 86.1s (avg 290.5M/s); src: 300 files, 300.0M
read 25000.0M in 82.4s (avg 303.4M/s); src: 300 files, 300.0M
read 25000.0M in 82.7s (avg 302.4M/s); src: 300 files, 300.0M

# (79.9+77.4+81.9+82.9+78.8+85.7+85.2+85.4+86.8+99.0+84.9+100.9+86.1+82.4+82.7)/15
# = 85.3
```

```C
# vm.swappiness=2

read 25000.0M in 81.7s (avg 306.0M/s); src: 300 files, 300.0M
read 25000.0M in 80.8s (avg 309.5M/s); src: 300 files, 300.0M
read 25000.0M in 81.7s (avg 306.1M/s); src: 300 files, 300.0M
read 25000.0M in 80.3s (avg 311.3M/s); src: 300 files, 300.0M
read 25000.0M in 93.3s (avg 267.9M/s); src: 300 files, 300.0M
read 25000.0M in 79.3s (avg 315.3M/s); src: 300 files, 300.0M
read 25000.0M in 87.8s (avg 284.7M/s); src: 300 files, 300.0M
read 25000.0M in 86.2s (avg 290.1M/s); src: 300 files, 300.0M
read 25000.0M in 87.7s (avg 285.1M/s); src: 300 files, 300.0M
read 25000.0M in 89.1s (avg 280.7M/s); src: 300 files, 300.0M
read 25000.0M in 85.9s (avg 291.0M/s); src: 300 files, 300.0M
read 25000.0M in 85.5s (avg 292.4M/s); src: 300 files, 300.0M
read 25000.0M in 99.8s (avg 250.6M/s); src: 300 files, 300.0M
read 25000.0M in 85.4s (avg 292.7M/s); src: 300 files, 300.0M
read 25000.0M in 86.3s (avg 289.6M/s); src: 300 files, 300.0M

# (81.7+80.8+81.7+80.3+93.3+79.3+87.8+86.2+87.7+89.1+85.9+85.5+99.8+85.4+86.3)/15
# 86.1
```

```C
# vm.swappiness=1

read 25000.0M in 97.7s (avg 255.9M/s); src: 300 files, 300.0M
read 25000.0M in 88.5s (avg 282.4M/s); src: 300 files, 300.0M
read 25000.0M in 95.1s (avg 262.8M/s); src: 300 files, 300.0M
read 25000.0M in 96.4s (avg 259.3M/s); src: 300 files, 300.0M
read 25000.0M in 92.9s (avg 269.0M/s); src: 300 files, 300.0M
read 25000.0M in 98.0s (avg 255.2M/s); src: 300 files, 300.0M
read 25000.0M in 97.7s (avg 255.9M/s); src: 300 files, 300.0M
read 25000.0M in 102.1s (avg 244.9M/s); src: 300 files, 300.0M
read 25000.0M in 92.8s (avg 269.5M/s); src: 300 files, 300.0M
read 25000.0M in 97.7s (avg 255.9M/s); src: 300 files, 300.0M
read 25000.0M in 105.2s (avg 237.6M/s); src: 300 files, 300.0M
read 25000.0M in 99.9s (avg 250.3M/s); src: 300 files, 300.0M
read 25000.0M in 98.5s (avg 253.8M/s); src: 300 files, 300.0M
read 25000.0M in 94.9s (avg 263.4M/s); src: 300 files, 300.0M
read 25000.0M in 95.6s (avg 261.5M/s); src: 300 files, 300.0M

# (97.7+88.5+95.1+96.4+92.5+98.0+97.7+102.1+92.8+97.7+105.2+99.9+98.5+94.9+95.6)/15
# = 96.8
```

#### Results of tests execution with classic LRU

With classic LRU, `vm.swappiness` have a big impact on the result, as expected.

```C
# vm.swappiness=200

read 25000.0M in 25.4s (avg 983.7M/s); src: 300 files, 300.0M
read 25000.0M in 25.3s (avg 987.1M/s); src: 300 files, 300.0M
read 25000.0M in 25.3s (avg 988.0M/s); src: 300 files, 300.0M
read 25000.0M in 25.2s (avg 990.5M/s); src: 300 files, 300.0M
read 25000.0M in 25.0s (avg 998.1M/s); src: 300 files, 300.0M
read 25000.0M in 25.1s (avg 995.8M/s); src: 300 files, 300.0M
read 25000.0M in 25.1s (avg 996.3M/s); src: 300 files, 300.0M
read 25000.0M in 25.1s (avg 994.3M/s); src: 300 files, 300.0M
read 25000.0M in 25.5s (avg 978.6M/s); src: 300 files, 300.0M
read 25000.0M in 25.1s (avg 997.7M/s); src: 300 files, 300.0M
```

```C
# vm.swappiness=100

read 25000.0M in 48.1s (avg 519.7M/s); src: 300 files, 300.0M
read 25000.0M in 47.9s (avg 521.9M/s); src: 300 files, 300.0M
read 25000.0M in 47.9s (avg 522.3M/s); src: 300 files, 300.0M
read 25000.0M in 48.7s (avg 513.0M/s); src: 300 files, 300.0M
read 25000.0M in 48.5s (avg 515.7M/s); src: 300 files, 300.0M
read 25000.0M in 48.3s (avg 517.6M/s); src: 300 files, 300.0M
read 25000.0M in 48.6s (avg 514.0M/s); src: 300 files, 300.0M
read 25000.0M in 48.8s (avg 512.5M/s); src: 300 files, 300.0M
read 25000.0M in 47.7s (avg 523.7M/s); src: 300 files, 300.0M
```

```C
# vm.swappiness=60

read 25000.0M in 70.7s (avg 353.5M/s); src: 300 files, 300.0M
read 25000.0M in 71.0s (avg 352.3M/s); src: 300 files, 300.0M
read 25000.0M in 70.4s (avg 354.9M/s); src: 300 files, 300.0M
read 25000.0M in 70.3s (avg 355.6M/s); src: 300 files, 300.0M
read 25000.0M in 70.9s (avg 352.5M/s); src: 300 files, 300.0M
```

```C
# vm.swappiness=50

read 25000.0M in 78.7s (avg 317.6M/s); src: 300 files, 300.0M
read 25000.0M in 79.3s (avg 315.2M/s); src: 300 files, 300.0M
read 25000.0M in 78.9s (avg 316.9M/s); src: 300 files, 300.0M
read 25000.0M in 79.1s (avg 316.1M/s); src: 300 files, 300.0M
read 25000.0M in 79.7s (avg 313.5M/s); src: 300 files, 300.0M
```

```C
# vm.swappiness=45

read 25000.0M in 84.5s (avg 295.8M/s); src: 300 files, 300.0M
read 25000.0M in 84.4s (avg 296.2M/s); src: 300 files, 300.0M
read 25000.0M in 84.9s (avg 294.4M/s); src: 300 files, 300.0M
read 25000.0M in 83.5s (avg 299.3M/s); src: 300 files, 300.0M
read 25000.0M in 84.4s (avg 296.3M/s); src: 300 files, 300.0M
```

```C
# vm.swappiness=40

read 25000.0M in 90.5s (avg 276.3M/s); src: 300 files, 300.0M
read 25000.0M in 89.7s (avg 278.6M/s); src: 300 files, 300.0M
read 25000.0M in 89.9s (avg 278.0M/s); src: 300 files, 300.0M
read 25000.0M in 90.0s (avg 277.7M/s); src: 300 files, 300.0M
read 25000.0M in 88.7s (avg 281.9M/s); src: 300 files, 300.0M
```

```C
# vm.swappiness=10

read 25000.0M in 174.0s (avg 143.7M/s); src: 300 files, 300.0M
read 25000.0M in 167.4s (avg 149.3M/s); src: 300 files, 300.0M
read 25000.0M in 172.5s (avg 145.0M/s); src: 300 files, 300.0M
read 25000.0M in 170.7s (avg 146.4M/s); src: 300 files, 300.0M
read 25000.0M in 173.0s (avg 144.5M/s); src: 300 files, 300.0M
```

```C
# vm.swappiness=2

read 25000.0M in 340.1s (avg 73.5M/s); src: 300 files, 300.0M
read 25000.0M in 337.4s (avg 74.1M/s); src: 300 files, 300.0M
read 25000.0M in 348.9s (avg 71.7M/s); src: 300 files, 300.0M
```

```C
# vm.swappiness=1

read 25000.0M in 523.3s (avg 47.8M/s); src: 300 files, 300.0M
read 25000.0M in 550.7s (avg 45.4M/s); src: 300 files, 300.0M
```

---

## cache-bench -w 50

```
cache-bench -w 50 -p test50
cache-bench -r 25000 -p test50
```

#### Results of tests execution with mg-LRU

```C
# vm.swappiness=200

read 25000.0M in 40.6s (avg 615.6M/s); src: 50 files, 50.0M
```

```C
# vm.swappiness=10

read 25000.0M in 40.7s (avg 614.4M/s); src: 50 files, 50.0M
```

```C
# vm.swappiness=1

read 25000.0M in 42.8s (avg 584.0M/s); src: 50 files, 50.0M
```

#### Results of tests execution with classic LRU

```C
# vm.swappiness=200

read 25000.0M in 19.5s (avg 1279.1M/s); src: 50 files, 50.0M
read 25000.0M in 20.1s (avg 1241.6M/s); src: 50 files, 50.0M
```

```C
# vm.swappiness=100

read 25000.0M in 21.5s (avg 1160.8M/s); src: 50 files, 50.0M
read 25000.0M in 21.7s (avg 1152.3M/s); src: 50 files, 50.0M
```

```C
# vm.swappiness=50

read 25000.0M in 26.6s (avg 938.5M/s); src: 50 files, 50.0M
```

```C
# vm.swappiness=40

read 25000.0M in 28.8s (avg 867.5M/s); src: 50 files, 50.0M
```

```C
# vm.swappiness=30

read 25000.0M in 34.0s (avg 735.5M/s); src: 50 files, 50.0M
```

```C
# vm.swappiness=20

read 25000.0M in 45.7s (avg 547.5M/s); src: 50 files, 50.0M
```

```C
# vm.swappiness=10

read 25000.0M in 70.8s (avg 352.9M/s); src: 50 files, 50.0M
read 25000.0M in 69.8s (avg 358.3M/s); src: 50 files, 50.0M
```

```C
# vm.swappiness=1

read 25000.0M in 477.7s (avg 52.3M/s); src: 50 files, 50.0M
```

---

## cache-bench -w 1

```
cache-bench -w 1 -p test1
cache-bench -r 25000 -p test1
```

#### Results of tests execution with mg-LRU

```C
# vm.swappiness=200

read 25000.0M in 20.1s (avg 1246.6M/s); src: 1 files, 1.0M
read 25000.0M in 20.6s (avg 1211.1M/s); src: 1 files, 1.0M
```

```C
# vm.swappiness=1

read 25000.0M in 18.8s (avg 1327.2M/s); src: 1 files, 1.0M
read 25000.0M in 18.6s (avg 1346.9M/s); src: 1 files, 1.0M
```

#### Results of tests execution with classic LRU

```C
# vm.swappiness=200

read 25000.0M in 17.6s (avg 1422.0M/s); src: 1 files, 1.0M
```

```C
# vm.swappiness=100

read 25000.0M in 17.7s (avg 1415.3M/s); src: 1 files, 1.0M
```

```C
# vm.swappiness=10

read 25000.0M in 38.6s (avg 648.3M/s); src: 1 files, 1.0M
```

```C
# vm.swappiness=1

read 25000.0M in 110.7s (avg 225.9M/s); src: 1 files, 1.0M
```

---

## cache-bench -w 1000

```
cache-bench -w 1000 -p test1000
cache-bench -r 25000 -p test1000
```

#### Results of tests execution with mg-LRU

```C
# vm.swappiness=200

read 25000.0M in 167.7s (avg 149.1M/s); src: 1000 files, 1000.0M
```

```C
# vm.swappiness=100

read 25000.0M in 172.6s (avg 144.8M/s); src: 1000 files, 1000.0M
```

```C
# vm.swappiness=10

read 25000.0M in 172.8s (avg 144.7M/s); src: 1000 files, 1000.0M
```

```C
# vm.swappiness=1

read 25000.0M in 222.9s (avg 112.2M/s); src: 1000 files, 1000.0M
```

#### Results of tests execution with classic LRU

```C
# vm.swappiness=200

read 25000.0M in 42.6s (avg 587.3M/s); src: 1000 files, 1000.0M
```

```C
# vm.swappiness=100

read 25000.0M in 130.5s (avg 191.6M/s); src: 1000 files, 1000.0M
```

```C
# vm.swappiness=10

read 25000.0M in 289.5s (avg 86.3M/s); src: 1000 files, 1000.0M
```

