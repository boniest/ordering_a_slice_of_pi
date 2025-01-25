i discovered a pattern in pi.

algorithm:

1. multiply integer and decimal parts of pi (ie. 3 * (pi-3)).
2. split between occurences of double zeros (these are "slices"), leaving one zero of each double-zero to each slice.
3. split on single zeros (these are "bites").
4. add digits of either slices or bites and see the beauty.

i have only done the first slice before committing.

the first slice is 216 = 42 * 4 + 24 * 2 characters long (removing decimal and counting the zero to the left of the decimal)

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

see where this is going?

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

take a look in the notebook. supposing i have not screwed anything up i think this is pretty darn remarkable.

i stopped here (for now) but the next slice is 42 digits long!

thanks for reading.
