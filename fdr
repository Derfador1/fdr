#! /usr/bin/env python3

import socket

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
	"""
	host = "127.0.0.1"
	port1 = 1000 #uid 
	port2 = 2000 #uid + 1000
	port3 = 3000 #uid + 2000
	
	mySocket0 = socket.socket()
	mySocket0.bind((host,port1))
    
	mySocket1 = socket.socket()
	mySocket1.bind((host, port2))
	
	mySocket2 = socket.socket()
	mySocket2.bind((host, port3))
	"""
	
	#sd = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	#sd.connect(("127.0.0.1", 6667))
	
	x = fibonacci(10)
	print(x)
	
	b = hex_to_dec(10998723)
	print(b)
	
	d = 'MDCDIIII'
	
	c = roman_to_hex(d)
	print(c)

if __name__ == '__main__':
	main()
