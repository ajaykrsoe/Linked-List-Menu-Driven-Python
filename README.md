# Linked-List-Menu-Driven-Python
class node :
    def __init__(self,data)  :
        self.data=data
        self.next=None
class linkedList  :
    def __init__(self)   :
        self.head=None
        self.size=0
def traverse(List) :
    if(List.head) :
        temp=List.head
        while(temp) :
            print(temp.data,end=" ")
            temp=temp.next

    else :
        print("List Is Empty")
        

def insertAtFirst(List) :
     List.size+=1
     tempData=int(input("Enter Data"))
     newNode=node(tempData)
     if(List.head) :
         temp=List.head
         List.head=newNode
         newNode.next=temp
     else :
         List.head=newNode
         
def insertAtLast(List) :
    List.size+=1
    tempData=int(input("Enter Data"))
    newNode=node(tempData)
    if(List.head)  :
        temp=List.head
        while(temp.next)  :
            temp=temp.next
        temp.next=newNode
    else :
        List.head=newNode
def insertAtPosition(List) :
    pos=int(input("Enter Position"))
    size=List.size
    if(pos==1) :
        insertAtFirst(List)
    elif(pos<=size+1  and pos>0)  :
           tempData=int(input("Enter Data"))
           newNode=node(tempData)
           temp=List.head
           for e in range(pos-2) :
               temp=temp.next
           temp2=temp.next
           temp.next=newNode
           newNode.next=temp2
           List.size+=1
               
    else :
        print("Invalid Position ")
        

def deleteFirst(List) :
    if(not List.head) :
        print("List Is Empty")
    else :
        List.head=List.head.next
        List.size-=1
        


def deleteLast(List) :
    if(List.size==0) :
        print("List Is Empty")
        return 
    if(List.size==1) :
        List.head=None
    else :
        temp=List.head
        while(temp.next.next) :
            temp=temp.next
        temp.next=None
    List.size-=1
        

def deletePosition(List) :
    size=List.size
    if(size==0)  :
        print("List Is Empty")
        return 
    pos=int(input("Enter position"))
    if(pos==1) :
        deleteFirst(List)
    elif(pos<=size) :
        temp=List.head
        for e in range(pos-2) :
            temp=temp.next
        temp.next=temp.next.next
        List.size-=1
        
    else :
       print("Invalid Position ")

def    traverseReverseHelper(node)    :
    if(node)   :
            traverseReverseHelper(node.next )
            print(node.data,end=" ")      
def traverseReverse(List) :
    if(not List.head)  :
        print("List Is Empty ")
    else :
        traverseReverseHelper(List.head)

def reverseIterative(List)  :
    if(List.head)  :
        array=[]
        temp=List.head
        while(temp)  :
            array.append(temp.data)
            temp=temp.next
        array.reverse()
        temp=List.head
        for e in array :
            temp.data=e
            temp=temp.next
    print("Reversed SucessFullly ")
            
def  reverseHelper(prev,curr) :
     if(curr) :
         temp=curr.next
         curr.next=prev
         return reverseHelper(curr,temp)
     else :
        return prev
def reverseRecursive(List)  :
    List.head=reverseHelper(None,List.head)
    print("Reversed Successfully ")



    
def  currentSize(List)  :
    print("Current Size Is",List.size)


def idPrint(List) :
    print("ID of head object",id(List))
    if(List.head) :
        print("ID's of node object")
        temp=List.head
        while(temp) :
            print(id(temp),end=" ")
            temp=temp.next
def out(List) :
    input("Enter any key to exit")
    exit(0)

print("MENU")
print("1.Traverse")
print("2.Insert At First")
print("3.Insert At Last")
print("4.Insert At Position")
print("5.Delete From First")
print("6.Delete From Last")
print("7.Delete From Position")
print("8.Traverse In Reverse Order")
print("9.Reverse Iterative")
print("10.Reverse Recursively")
print("11.Current Size")
print("12.Print ID of each node")
print("13.Exit")

functionHashing={1:traverse,2:insertAtFirst ,3:insertAtLast,4:insertAtPosition,5:deleteFirst,
                 6:deleteLast,  7:deletePosition ,8:traverseReverse ,9:reverseIterative,10:reverseRecursive,11:currentSize,12:idPrint,13:out}


List=linkedList()
while(True)  :
    try :
      choice=int(input("Enter Choice "))
      if(choice  not in range(1,14,1)) :
          print("Enter valid Choice")
          continue
          
    except :
        print("Enter Valid Choice")
        continue
    functionHashing[choice](List)
