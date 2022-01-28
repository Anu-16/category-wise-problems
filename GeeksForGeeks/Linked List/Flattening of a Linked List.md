[flattening of a Linked List](https://practice.geeksforgeeks.org/problems/flattening-a-linked-list/1#)

- merge sort approach
- we will initially take root and its next node and using merge function we'll try to flatten them first
- we recursively merge() the current list with the already flattened list

<details>
<summary> Code </summary>

```cpp

struct Node{
	int data;
	struct Node * next;
	struct Node * bottom;
	
	Node(int x){
	    data = x;
	    next = NULL;
	    bottom = NULL;
	}
	
};

// Function which returns the  root of the flattened linked list.
    
Node* merge(Node* root1 , Node* root2)
{
    if(!root2)
      return root1 ;
    if(!root1)
      return root2 ;
    
    Node* root3 ;
    
    if(root1->data <= root2->data)
     {
         root3 = root1 ;
         root3->bottom = merge(root1->bottom , root2) ;
     }
     else
     {
         root3 = root2 ;
         root3->bottom = merge(root1 , root2->bottom) ;
     }
    
    return root3 ;
}

Node *flatten(Node *root)
{

    Node* r1 = root ;
    Node* r2 = root->next ;
    while(r2)
    {
        r1 = merge(r1,r2) ;
        r2 = r2->next ;
    }
    
    return r1 ;
       
   
}      

```
</details>
