- This is a so-called eager algorithm for solving connectivity problem.
- The data structure that we r going to use to support the algorithm is simply an integer array indexed by object
![[quick find data structure.png]]


 ```python
class QuickFindUF:
	def __init__(self, n):
		self.id = []
		for i in range(n):
			self.id.append(i)

	def connected(self,p,q):
		return self.id[p] == self.id [q]

	def union(self,p,q):
		pid = self.id[p]
		qid = self.id[q]
		if pid == qid:
			return
		for i in range(len(self.id)):
			if self.id[i] == pid:
				self.id[i] = qid

 ```



the key：Quick-Find union is a single global update, not an iterative process！

Why `id[p] = id[q]` Is Incorrect？？？
- A component may contain **many elements**
    
- Updating only `id[p]`:
    
    - Breaks component consistency
        
    - Leaves other members unchanged
        
    - Produces incorrect `connected` results


Quick-Find is  too slow cuz its representation requires global updates.
The performance problem is **not implementation**
It is a **data-structure design limitation**

the key idea ：Store the **final answer directly** in the array.



use the array！