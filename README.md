i discovered a pattern in pi.

algorithm:

1. multiply integer and decimal parts of pi (ie. 3 * (pi-3)).
2. split between occurences of triple, double, and single 0s. (i call a split on 000 a "chunk", a split on 00 a "slice", and a split on 0 a "bite".)
4. add cohesive digits and look out!

the first slice is 216 = 42 * 4 + 24 * 2 characters long (removing the decimal and counting the zero to the left of the decimal)

here is the first slice:
042477796076937971538793014983850865259150819812531746292483377692344921885862699588410447602635120394644425953984691994128153382865174669517607822438544335235085230810581556331667893386884686479114589328643292699780

note: the next digit is a 0 (...780033...) which is why i sliced there.

the first bite is 42477796
with checksum of 
```
4+2+4+7+7+7+9+6 = 46 = 42 + 4
```

(note also '424', 777 => 7+7+7 = 42/2, 96 = 4 * 24)

the next bite is 76937971538793
with check sum of 
```
7+6+9+3+7+9+7+1+5+3+8+7+9+3 = 84 = 42 * 2
```

the next bite is 1498385
with check sum of 
```
1+4+9+8+3+8+5 = 38 = 42 - 4
```

those three total to 
```
46 + 84 + 38 = 168 = 42 * 4
```

it gets more convoluted after that (which can you see in the notebook) but eventually it builds up bite by bite to...

the total of the digits of the first slice is 1051.

which can be expressed as the following:

```
a = ((42 * 4) - (42 + 4))  
b = ((4 * 24) - (4 + 24))  
assert 1051 == +(+(+2 * +2**+2 * +a) + b) -(-(-2 * -2**-2 * -a) - b)  
```

rearranged for clarity:
```
1051 == +(+(+2 * +2**+2 * +a) + b) \
        -(-(-2 * -2**-2 * -a) - b)
```

or if i add 1s for each implied 1 then:
```
1051 == +1 * (+1 * (+2 * +2**+2 * + 1*a) + 1*b) \
        -1 * (-1 * (-2 * -2**-2 * - 1*a) - 1*b)
```

the sum of those coefficients is 10 and -10 which cancel.

the sum of the digits of a and b, respecting the signs, are:
```
(4 + 2 + 4) - (4 + 2 + 4) = 10 - 10 = 0  
(4 + 2 + 4) - (4 + 2 + 4) = 10 - 10 = 0  
```

the second slice is 42 digits long. i haven't analysed beyond the first yet.

but i did take a look all the way to the first occurence of a 000 and found in the first chunk of 856 digits (leaving a 0 on both left and right) there are:

```
8 slices = 4 * 2
66 bites = 42 + 24
856 digits = 4 * ((42*4) + (42+4))
```

take a look in the notebook. supposing i have not screwed anything up i think this is pretty darn remarkable.

thanks for reading.
