# pythoncodes
#python programs
class BST:
    def __init__(self,d):
        self.l=None
        self.r=None
        self.d=d
    def insert(self,k):
        if self.d is None:
            self.d=k
            return
        if k<self.d:
            if self.l:
                self.l.insert(k)
            else:
                self.l=BST(k)
        else:
            if self.r:
                self.r.insert(k)
            else:
                self.r=BST(k)
    def delete(self,v,r):
        if self.d is None:
            print('empty')
            return
        if v<self.d:
            if self.l:
                self.l=self.l.delete(v,r)
            else:
                print('not fund')
        elif v>self.d:
            if self.r:
                self.r=self.r.delete(v,r)
            else:
                print('not found')
        else:
            if self.l is None:
                t=self.r
                if v==r:
                    self.d=t.d
                    self.l=t.l
                    self.r=t.r
                    t=None
                    return
                self=None
                return t
            if self.r is None:
                t=self.l
                if v==r:
                    self.d=t.d
                    self.l=t.l
                    self.r=t.r
                    t=None
                    return
                self=None
                return t
            m=self.l
            while m.r:
                m=m.r
            self.d=m.d
            self.l=self.l.delete(m.d)
        return self
         
    def inorder(self):
        if self.d is None:
            print('empty')
            return
        if self.l:
            self.l.inorder()
        print(self.d,end=' ')
        if self.r:
            self.r.inorder()
def count(node):
    if node is None:
        return 0
    return 1+count(node.l)+count(node.r)
ra=BST(None)
for i in [10,40,30,20]:
    ra.insert(i)
ra.inorder()
print()
if count(ra)>1:
    ra.delete(10,ra.d)
else:
    print('can not perform delete operation')
ra.inorder()

        
#Python Codes on Data structures
