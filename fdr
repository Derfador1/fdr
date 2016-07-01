#! /usr/bin/env python3

import socket
import os
import threading


class myThread(threading.Thread):
	def __init__(self, host, port):
		threading.Thread.__init__(self)
		self.host = host
		self.port = port
		self.server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM) #move there two lines somewhere else
		self.server_socket.bind((self.host, self.port))
		self.server_socket.setblocking(False)
		self.flag = 1
		
	def quitter(self):
		self.flag = 0
		
	def run(self):
			while(self.flag):
				try:
					self.data, addr = self.server_socket.recvfrom(1024)
					self.data = self.data.decode('utf-8')
					if self.data[0] == 'F':
						answer = fibonacci(int(self.data[1:]))
						answer += '\n\0'
						self.server_socket.sendto(bytes(answer, 'utf-8'), addr)
					elif self.data[0] == 'D':
						answer = hex_to_dec(int(self.data[1:]))
						answer += '\n\0'
						self.server_socket.sendto(bytes(answer, 'utf-8'), addr)
					elif self.data[0] == 'R':
						pass
				except BlockingIOError:
					"""stuff"""	
			self.server_socket.close()
			
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
	uid = os.getuid()

	host = "127.0.0.1"
	port1 = uid
	port2 = uid + 1000
	port3 = uid + 2000
	
	print(port2)
	print(port3)
	
	#sd = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
	#sd.connect(("127.0.0.1", 6667))
	
	#mySocket0.bind((host,port1))
    
	#mySocket1.bind((host, port2))
	
	#mySocket2.bind((host, port3))
	
	myServer1 = myThread(host, port1)
	myServer2 = myThread(host, port2)
	myServer3 = myThread(host, port3)
	
	myServer1.start()
	myServer2.start()
	myServer3.start()
	
	x = input("What would you like to do?")
	if x == 'quit':
		myServer1.quitter()
		myServer2.quitter()
		myServer3.quitter()
		myServer1.join(timeout=1)
		myServer2.join(timeout=1)
		myServer3.join(timeout=1)
		
		
	#myServer2 = myThread(host, port2)
	#myServer3 = myThread(host, port3)

	
	#x = fibonacci(10)
	#print(x)
	
	#b = hex_to_dec(10998723)
	#print(b)
	
	#d = 'MDCDIIII'
	
	#c = roman_to_hex(d)
	#print(c)

if __name__ == '__main__':
	main()
