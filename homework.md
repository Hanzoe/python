def __odd__iter():
	n = 1
	while True:
		n = n + 2
		yield n#创建一个3为首的奇数序列
	
def __not__divisible(n):
	return lambda x: x % n>0#定义一个筛选函数，运用lambda函数
	
def primes():
	yield 2 #首先返回一个素数2
	it = __odd__iter()#引用奇数序列
	while True:
		n = next(it)#从第一个数3开始逐步带入
		yield n#逐个返回
		it = filter(__not__divisible(n), it)#调用筛选函数，其中的x为序列，n为迭代的值，逐步筛选
	
for n in primes():#设置结束点
	if n < 100:
		print(n)
	else:
		break