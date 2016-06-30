#! /usr/bin/env python3

def fibonacci(n):
	a = 0
	b = 1
	for i in range(0, n):
		temp = a
		a = b
		b = temp + b
	return hex(a)

def hex_to_dec(n):
	return hex(n)

#converting roman numeral to decimal found at
#http://stackoverflow.com/questions/19308177/converting-roman-numerals
#-to-integers-in-python
def roman_to_hex(number):
	numerals = [
		{'letter': 'M', 'value': 1000},
		{'letter': 'D', 'value': 500},
		{'letter': 'C', 'value': 100},
		{'letter': 'L', 'value': 50},
		{'letter': 'X', 'value': 10},
		{'letter': 'V', 'value': 5},
		{'letter': 'I', 'value': 1},
	]
	
	
	index_by_letter = {}
	for index in range(len(numerals)):
		index_by_letter[numerals[index]['letter']] = index

	result = 0
	previous_value = None
	for letter in reversed(number):
		index = index_by_letter[letter]
		value = numerals[index]['value']
		if (previous_value is None) or (previous_value <= value):
			result += value
		else:
			result -= value
		previous_value = value

	return hex(result)
	
def main():
	x = fibonacci(10)
	print(x)
	
	b = hex_to_dec(10998723)
	print(b)
	
	d = 'MDCDIIII'
	
	c = roman_to_hex(d)
	print(c)

if __name__ == '__main__':
	main()
