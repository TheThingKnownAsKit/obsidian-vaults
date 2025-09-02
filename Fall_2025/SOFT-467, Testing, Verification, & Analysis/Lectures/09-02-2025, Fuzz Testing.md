![[soft467-3-testing-review.pdf]]

<mark style="background: #ADCCFFA6;">Unit tests</mark> are for single piece of code (like a method). Does it pass/fail under different conditions? Assertion based. Small and fast and easy to isolate errors. Hard to test UIs. Might require changes to code to enable testing. Lots of code per line being tested
```Python
import unittest

class Test (unittest.TestCase):
	def test_something(self):
		oooo code goes here
		self.assertEqual(result, expected)
	
	def test_error(self):
		with self.assertRaises(AssertionError):
			ooooo code

if __name__ == '__main__':
	unittest.main()
```

<mark style="background: #ADCCFFA6;">Integration Tests</mark> is testing many units working together. Can they communicate and work together and still function as expected?
<mark style="background: #ADCCFFA6;">Regression Tests</mark> are testing after something changes. If you fix one bug, add a test that checks to see if that one bug still happens. Run this test every time something is changed to see if the bug stayed fixed
<mark style="background: #ADCCFFA6;">Acceptance Tests</mark> is asking if the functionality meets the business requirements? Mostly meetings

<mark style="background: #ADCCFFA6;">Test-Driven Development (TDD)</mark> is encoding requirements as a unit test to make sure test fails. Design and implement API(s) as needed to make sure requirements stay encoded

<mark style="background: #ADCCFFA6;">Fuzzing</mark> is the practice of creating random inputs and seeing if they break things. Generate random noise and see how robust the error handling is. Below is a fuzz generator
```Python
import random

def fuzzer(max_length: int = 100, char_start: int = 32, char_range: int = 32) -> str:
    """A string of up to `max_length` characters
       in the range [`char_start`, `char_start` + `char_range`)"""
    string_length = random.randrange(0, max_length + 1)
    out = ""
    for i in range(0, string_length):
        out += chr(random.randrange(char_start, char_start + char_range))
    return out
```

