# text2num
Python library to convert textual numbers to integers

## Testing

With [nose](http://nose.readthedocs.io/en/latest/):

```sh
nosetests --config=.noserc
```

or without:

```sh
python -m doctest -o IGNORE_EXCEPTION_DETAIL -o NORMALIZE_WHITESPACE text2num.py
```

## Usage

```py
>>> text2num("zero")
0

>>> text2num("one")
1

>>> text2num("twelve")
12

>>> text2num("nineteen")
19

>>> text2num("twenty nine")
29

>>> text2num("seventy two")
72

>>> text2num("three hundred")
300

>>> text2num("twelve hundred")
1200

>>> text2num("nineteen hundred eighty four")
1984

>>> text2num("one thirty")
130

>>> text2num("six sixty two")
662

>>> text2num("ten twelve")
1012

>>> text2num("nineteen ten")
1910

>>> text2num("nineteen eighty four")
1984

>>> text2num("twenty ten")
2010

>>> text2num("twenty twenty")
2020

>>> text2num("twenty twenty one")
2021

>>> text2num("fifty sixty three")
5063

>>> text2num("one thirty thousand")
Traceback (most recent call last):
    ...
NumberException: 'thousand' may not proceed implied hundred 'one thirty'

>>> text2num("nineteen eighty thousand")
Traceback (most recent call last):
    ...
NumberException: 'thousand' may not proceed implied hundred
'nineteen eighty'

>>> text2num("twelve thousand three hundred four")
12304

>>> text2num("six million")
6000000

>>> text2num("six million four hundred thousand five")
6400005

>>> text2num("one hundred twenty three billion four hundred fifty six "
...          "million seven hundred eighty nine thousand twelve")
123456789012

>>> text2num("four decillion")
4000000000000000000000000000000000

>>> text2num("one hundred thousand")
100000

>>> text2num("one hundred two thousand")
102000

>>> text2num("thousand")
Traceback (most recent call last):
    ...
NumberException: magnitude 'thousand' must be preceded by a number

>>> text2num("hundred one")
Traceback (most recent call last):
    ...
NumberException: magnitude 'hundred' must be preceded by a number

>>> text2num("one thousand thousand")
Traceback (most recent call last):
    ...
NumberException: magnitude 'thousand' must be preceded by a number

>>> text2num("one thousand two thousand")
Traceback (most recent call last):
    ...
NumberException: magnitude 'thousand' appeared out of order following
'one thousand two'

>>> text2num("one hundred two hundred")
Traceback (most recent call last):
    ...
NumberException: magnitude 'hundred' appeared out of order following
'one hundred two'

>>> text2num("one thousand two million")
Traceback (most recent call last):
    ...
NumberException: magnitude 'million' appeared out of order following
'one thousand two'

>>> text2num("nine one")
Traceback (most recent call last):
    ...
NumberException: 'one' may not proceed 'nine'

>>> text2num("ten two")
Traceback (most recent call last):
    ...
NumberException: 'two' may not proceed 'ten'

>>> text2num("nineteen nine")
Traceback (most recent call last):
    ...
NumberException: 'nine' may not proceed 'nineteen'

>>> text2num("sixty five hundred")
6500

>>> text2num("sixty hundred")
6000

>>> text2num("ten hundred twelve")
1012

>>> text2num("twenty twenty ten")
Traceback (most recent call last):
    ...
NumberException: 'ten' may not proceed 'twenty' following 'twenty'

>>> text2num("three thousand nineteen eighty four")
Traceback (most recent call last):
    ...
NumberException: 'eighty' may not proceed 'nineteen' following
'three thousand'

>>> text2num("three million nineteen eighty four")
Traceback (most recent call last):
    ...
NumberException: 'eighty' may not proceed 'nineteen' following
'three million'

>>> text2num("one million eighty eighty")
Traceback (most recent call last):
    ...
NumberException: 'eighty' may not proceed 'eighty' following 'one million'

>>> text2num("one million eighty one")
1000081

>>> text2num("zero zero")
Traceback (most recent call last):
    ...
NumberException: 'zero' may not appear with other numbers

>>> text2num("one zero")
Traceback (most recent call last):
    ...
NumberException: 'zero' may not appear with other numbers

>>> text2num("zero thousand")
Traceback (most recent call last):
    ...
NumberException: 'zero' may not appear with other numbers

>>> text2num("foo thousand")
Traceback (most recent call last):
    ...
NumberException: unknown number: 'foo'

>>> text2num("one thousand and two")
1002

>>> text2num("ten hundred and twelve")
1012

>>> text2num("nineteen hundred and eighty eight")
1988

>>> text2num("one hundred and ten thousand and one")
110001

>>> text2num("forty and two")
Traceback (most recent call last):
    ...
NumberException: 'and' must be preceeded by a magnitude but got 'forty'

>>> text2num("one and")
Traceback (most recent call last):
    ...
NumberException: 'and' must be preceeded by a magnitude but got 'one'

>>> text2num("and one")
Traceback (most recent call last):
    ...
NumberException: 'and' must be preceeded by a magnitude

>>> text2num("one hundred and")
Traceback (most recent call last):
    ...
NumberException: 'and' must be followed by a number

>>> text2num("nineteen and eighty eight")
Traceback (most recent call last):
    ...
NumberException: 'and' must be preceeded by a magnitude but got 'nineteen'

```
