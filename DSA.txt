/*find the frquency of a letter in a word:*/
int freq[mchar]={0};
for(int i=0;i<l;i++)
{
    freq[str[i] - 'a']++;
}

/*the two string are rotation of each other or not*/
bool isRotation(string str1,string str2)
{

	if(str1.length() != str2.length())
	{
		return false;
	}
	
		string temp=str1+str1;
	return(temp.find(str2)!=string::npos);//this line says that srt2 is found in temp.
	
}


/*Since the question only asks the number of bribes, there's no need to really do a sorting, nor element swapping, nor "bubbling up" an element. All you need to do is to count the number of people who overtake a person.*/

void calc(vector<int> q)
{
    int ans = 0;
    for (int i = q.size() - 1; i >= 0; i--) {
        if (q[i] - (i + 1) > 2) {
            cout << "Too chaotic" << endl;
            return;
        }
        for (int j = max(0, q[i] - 2); j < i; j++)
            if (q[j] > q[i]) ans++;
    }
    cout << ans << endl;
}



/*Sort an array according to absolute difference with given value*/

void rearrange(int arr[],int n,int k)
{
	stable_sort(arr,arr+n,[k](int a,int b)     //here lamda expression is used which return true if the condition is true, lamda expression is a small type of fucntion which can use any variable outside the function, and returns true according to the condition.
	{
	  return abs(k-b)>abs(k-a); 
	});
} 



/*Remove Nth Node From End of List*/
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
          ListNode* current = head;
          int m=0;
          int count;
        while(current!=NULL)
        {
            m++;
            current = current->next;
        }
        count = m-n;
        if(m==1)
        {
            return NULL;
        }
        current = head;
        if(m==n)
        {
            return current->next;
        }
        while(count-- >1)
        {
            current=current->next;
        }
        current->next=current->next->next;
        return head;
            
        
    }
};


// substr function to read the substring of our own choice.

#include <iostream>
#include <string>

int main ()
{
  std::string str="We think in generalities, but we live in details.";
                                           // (quoting Alfred N. Whitehead)

  std::string str2 = str.substr (3,5);     // "think"

  std::size_t pos = str.find("live");      // position of "live" in str

  std::string str3 = str.substr (pos);     // get from "live" to the end

  std::cout << str2 << ' ' << str3 << '\n';

  return 0;
}


// Longest substring which is a palindrom in string s.

  class Solution {
  public:
  bool palin(string s)
  {
      int a = 0;
      int b = s.size()-1;
      while(a<b)
      {
          if(s[a++] != s[b--])
          return false;
      }
      return true;
  }
    string longestPalin (string S) {
        // code here
        if(palin(S)) return S;
        int ma = INT_MIN;
        string ans;
        for(int i = 0;i<S.size();i++)
        {
            for(int j = S.size()-1;j>=i;j--)
            {
                string x = S.substr(i,j-i+1);
                int d = x.length();
                if(palin(x)==true && ma < d)
                {
                    ans = x;
                    ma = d;
                }
            }
        }
        
        return ans;
        
        
    }
  };




// most efficient method to find any power of a number.

const int M = 1e9+7;
int powerrec(int a, int b)
{
	if(!b) return 1;

	int res = powerrec(a,b/2);

	if(b&1)
		return (a * (res * 1LL * res) % M) % M;
	else
		return (res * 1LL * res) % M;
}



// void leftrotate(string &s, int d)          
  {
       reverse(s.begin(), s.begin()+d);
       reverse(s.begin()+d, s.end());
       reverse(s.begin(), s.end());
  }
 
// In-place rotates s towards right by d
   void rightrotate(string &s, int d)
  {
      leftrotate(s, s.length()-d);
  }




// to_string is used to convert the numerical value into string

std::string str = std::to_string(9954);
  
    // Finding 5 in the number
    std::cout << "5 is at position " << str.find('5') + 1;


output: 5 is at position 3

// to convert string character number to integer.
   
   str = "478932";
   cout<<str[2] ; -> this will give 8 as output but is it of char type.
   cout<<str[2] - '0'; -> this will give 8 as output and it is of int type.


//is used to find the first element in str1 which not present in  str2

str1.find_first_not_of(str2);



//Bit-manupulation to check even and odd numbers


int countSetBits(int n)                         // -> this funtion will count the number of setbits ie. no. of 1's in the number.
{
    // base case
    if (n == 0)
        return 0;
    else
        return 1 + countSetBits(n & (n - 1));
}


  
  if (a & 1 == 0)
  {
    cout<<a <<"is even";
  }
   else if(a & 1 == 1)
        {
           cout<<a <<"is odd";
        }


//Bit-manupulation to multipy and divide by 2

 for(int i=0 ; i < n*2 ; i++)  => can be Written as => for(int i=0 ; i < n<<1 ; i++)

 for(int i=0 ; i < n/2 ; i++)  => can be Written as => for(int i=0 ; i < n>>1 ; i++)

   // The left-shift of 1 by i is equivalent to 2 raised to power i. 
      As mentioned in point 1, it works only if numbers are positive. 
       
      1 << i  here let i = 3 then value of 1 << i = 2^3 = 8


// Bit-manupulation to swap two numbers faster

  int a = 5;
  int b = 7;

  a = a ^ b; // here a becomes 2;
  b = a ^ b; // here b becomes 5;
  a = a ^ b; // here a becomes 7;
  
  cout<<a<<" "<<b;  // 7 5


//To find how many bits are there in the binary representation of number n.

no. of bits = log n(base 2) + 1

//To find how many bits are there in the decimal representation of number n.

no. of bits = log n(base 10) + 1

// __builtin_popcount(n); -> this will give total number of set bits in number n. and set bits means no. of 1's in the binary expention of n.

// char temp = 'C';
   char temp1 = temp | ' '; -> this will convert capital C to small c.

// char temp = 'c';
   char temp1 = temp & '_'; -> this will convert small c to capital C.

// string s;  string b;  regex c(b);

   regex_match(s,c); --> this will give the regex match of s in b;


// float value = (int)(var * 100 + .5);
    return (float)value / 100;
  
   { 37.66666 * 100 =3766.66
   { 3766.66 + .5 =3767.16    for rounding off value }
    then type cast to int so value is 3767
    then divided by 100 so the value converted into 37.67 }



//Commit Branch

// bool res = binary_search(arr,arr+n,val); -> this will do binary search for element val in an array arr.

// int index = lower_bound(arr,arr+n,val)-a; -> this will give the index of element val of an array arr. if the element is not present then it will give the index of imdidiate greater value elements of val. if the element is not present and non of the element is greater than val then it will return n+1 to the index. 

// To append integer number in string as a string.

  int x = 5;
  string y = "abc";
  y = y + to_string(x);
  cout<<y;  -> y == abc5


// Stack:
      
     stack emplace():
        Difference between stack::emplace() and stack::push() function.
        While push() function inserts a copy of the value or the parameter 
        passed to the function into the container at the top, the emplace() 
        function constructs a new element as the value of the parameter and 
        then adds it to the top of the container.


     stack swap():
                 mystack1.swap(mystack2);
     



// stringstream s(str);
    // breaking input into word using string stream Used for breaking words

    clear() — to clear the stream
    str() — to get and set string object whose content is present in stream.
    operator << — add a string to the stringstream object.
    operator >> — read something from the stringstream object,

                {vector<string> ops[i];
                 vector<int> v;
                 stringstream ss(ops[i]);   // this will change the string_vector element ops[i] to auto(numeric,float,char,string) value.
                int x;
                ss >> x;                    // this will assign numeric(converted from string by stringstream) value of string_vector ss to x.
            
                v.push_back(x);}   //now it can push back vector_string elememt to vector_int elements.
     






// accumulate(a.begin(), a.end(), 0); // this function will sum all the integer values of vector.(here a is the vector and 0 is the initial value of sum.).



// char intToAlphabet( int i )              // -> this will return the alphabet to which number it corresponds, example-> 1->A, 2->B, 26->Z.
  {
   return static_cast<char>('A' - 1 + i);
  }



//  getline(cin, S);
 
    stringstream X(S);

   while (getline(X, T, ' ')) {   // it will split the the string sentance whenever te space comes.
        cout << T << endl;
    }
  
  string str = {"ayush","ujjwal","abhishek"}

   string s = "";
  for(int i=v.size();i>=0;i--)
     { s+=v[i];
      s+=" ";  }
     return s;

//  vector<int> v(n); -> this is the vector of size n.
    vector<int> v(n,2); -> this means vector of n size where every n elements of vector is intilized with 2.
    vector<int> v(arr,arr+n). -> this means coverting array arr to vector v.
    vector<int> v1(v.begin(),v.end()); -> this means making another vector v1 with all the elements of v.
    vector<vector<int>> v(n,vector<int>(m)); -> this will initialize a 2D vector of size n x m.
    vector.insert(pos,val);
    vector.insert(pos,noofelements,val);
    vector1.insert( vector1.end(), vector2.begin(), vector2.end() );  -> this will insert the elements of vector2 in the end of vector1.
    vector.erase(pos);  -> this will erase the elements at position pos.
    vector.erase(pos,pos+n);
    vector.swap(v2);  -> swap v2 with vector;
    vector.front(); -> to read the front element.
    vector.back(); -> to read the last element.
    *max_element(a.begin(), a.end()); // -> this will give the maximum element of the vector.
    int arr[5] = {[0 ... 4] = 1};  // -> this will initalize all array elements to value 1. Its similar to -> int arr[5] = {1,1,1,1,1};


// sets -> only unique elements are allowed. so sets.count(2) count of elements is either 0 or 1.
    
   set<int> s;
   set<int> s(vector.begin(),vector.end());  -> this will make a set with the elements of vector, so the freqency of all elements of the vector become 1 or 0 in set and the elements will get sorted automatically in set.

  

//       string str = "23"

         stringstream ss(str);
                ss >> x;       ->here integer value is stored in x form stringstream ss
                s1.push_back(x);


// storage classes -> https://www.geeksforgeeks.org/storage-classes-in-c-with-examples/

   auto     //used for any data types
   register //used 
   extern   //tells that tha variable is decleared somewhere globally.
   static   //the value of the variabls of a function get retained and the changed value is used in the next function call.
   mutable //the intialized values of data members of a class can be modified in the main function.


// function to return the unique elements of array arr.

void printDistinct(int arr[],int n)
{
    // Creates an empty hashset
    unordered_set<int> s;
 
    // Traverse the input array
    for (int i=0; i<n; i++)
    {
        // If not present, then put it in
        // hashtable and print it
        if (s.find(arr[i])==s.end())  // -> this means if arr[i] is not present in set s then insert it into set. 
        {
            s.insert(arr[i]);
            cout << arr[i] << " ";
        }
    }
}





//Queue 

  enqueue(value);
  dequeue();
  front();
  rear();
                                     //  In a circular queue, the new element is always inserted at Rear position. 
                                     //  In a circular queue, the element is always deleted from front position. 

    Applications:
       a) Semaphores
       b) FCFS ( first come first serve) scheduling, example: FIFO queue
       c) Spooling in printers
       d) Buffer for devices like keyboard


// priority_queue<int> pq;
  
  empty();
  size();
  pop();
  push();
  top();
  insert(item, priority): Inserts an item with given priority.

    Applications: 
             Dijkstra’s Shortest Path Algorithm using priority queue: When the graph is stored in the form of adjacency list or matrix, priority queue can be used to extract minimum efficiently when implementing Dijkstra’s algorithm.
             Prim’s algorithm: It is used to implement Prim’s Algorithm to store keys of nodes and extract minimum key node at every step.
             Data compression : It is used in Huffman codes which is used to compresses data.
   
   priority_queue<int> pq(vector.begin(),vector.end());
   pq.top(); -> this will return maximum element of vector;
   
// to find ceiling value of any number n divided by 2 -> (n-n/2);

//   str.erase(remove(str.begin(), str.end(), ' '), str.end());
    This will remove all the strings from a given string.


//    vectorname.erase(position)
      vectorname.erase(startingposition, endingposition)    //here positions acn be written as v.begin()+n;
  
        These will remove the element or the range of elements from the given positions in vector.

//  count the frequency of an element of vector or array.
     count(arr, arr + n, 3);               // 3 is the element in the arr array.
     count(vect.begin(), vect.end(), 3);   // 3 is the element in the vect vector.


//  Lists in c++ (https://www.geeksforgeeks.org/list-in-c-set-2-some-useful-functions/)

//  return all_of(begin(cnt), end(cnt), [&](int c) { return c % words.size() == 0; })  // https://www.geeksforgeeks.org/stdall_of-in-cpp/

//  strlen(str);
    strcmp(str1,str2);
    strrev(str);
            
//  string r = s1.substr(1, 3);   -> this "substr" function will return substring of s1 given string from 1 to 3 index.

//  s.erase( 4, 1 )  // this will remove the char at position 4 of string s and 1 is the number of char we want to remove from that position.

//  vector is a class not a pointer and while passing vector to a void function always to use reference vector as parameter.
     -> https://www.geeksforgeeks.org/passing-vector-function-cpp/  

// Binary Tree:

   max no. of nodes at level i is 2^i.
   max no. of nodes in tree with height h is (2^n)-1.

   in array representation of tree. let i be the index of a node.
                                           then poition of its left child is i*2.
                                           and position of the right child is i*2+1. 


   Traversal in tree: 
       In order traversal LNR(Left->Node->Right).
       Pre-order traversal NLR(Node->Left->Right).
       Post-order traversal LRN(Left->Right->Node).


  // A Binary Heap is a Complete Binary Tree. A binary heap is typically represented as an array.
          -> The root element will be at Arr[0].
          -> Below table shows indexes of other nodes for the ith node, i.e., Arr[i]:
                    Arr[(i-1)/2]   Returns the parent node
                    Arr[(2*i)+1]   Returns the left child node
                    Arr[(2*i)+2]   Returns the right child node

  //  BFS -> wide traversal (level order)
          -> if the searching is element is near to the root node in accordance with height
          -> queue is used to visit all the element.
          -> for finding the shortest path.


      DFS -> deep traversal (inorder,preorder,postorder)
          -> if the searching is element is far from the root node in accordance with height
          -> use stack to get the visited element.
          -> in backtraking and puzzles problems.
  

  // if the graph is sparsly connected then it is good the use list as it then edges can be ignored and TC is O(n+e)->O(n).
     * if the graph is densly connected then we can use list and matrix both as that time both have TC = O(n2). 
           


// Binary Search Tree:

    -> All nodes of left subtree is lesser than the root.
    -> All nodes of right subtree is greater than the root.
    -> left and right subtrees are also BST.
    -> There are no duplicate nodes.
    -> Inorder Traversal of a BST gives an ascending sorted array.



// Heap:

   It is basically used to implement complete binary tree.
   Heap is a complete binary tree(complete binary tree means -> A tree in which there need not to have both childrens of a node, but there must be a left node before the right node of any binary tree or we have to fill all the nodes with null before the alone rightmost node).
    
   MIN_heap -> the key of root node should be smaller than all its child nodes.
   MAX_heap -> the key of root node should be greater than all its child nodes.






// Graph :


#include"stdafx.h"
#include<iostream>
#include<map>
#include<list>
#include<queue>
#include<set>
using namespace std;
template<typename T>
class graph {
public:
	map<T, list<pair<T,int> > > adjlist;

	void addEdge(T u, T v, int dist,bool bidirec = 1)
	{
		 
		adjlist[u].push_back(make_pair(v, dist));
		
		if (bidirec)
			adjlist[v].push_back(make_pair(u, dist));
	}

	void print_adj()
	{
		for (auto n : adjlist)
		{
			cout << n.first<<" : ";
				for (auto a : n.second )
			{
				cout <<"( "<<a.first<<" , "<<a.second<<" ) " ;
			}
				cout << endl;
		}
	}

	void bfs(T u)
	{
		map< T, bool> visited;
		queue<T> q;
		q.push(u);
		while (!q.empty())
		{
			T front_element = q.front();
			q.pop();
			if (!visited[front_element]) {
				cout << front_element << " -> ";
				visited[front_element] = true;
			}
			for (auto a : (adjlist[front_element]))
			{
				if(!visited[a.first])
				q.push(a.first);
				
			}
		}
	}

	void dfs_helper(T src,map<T,bool> &visited)
	{
		visited[src] = true;
		cout << src << " -> ";

		for (auto a : adjlist[src])
		{
			if (!visited[a.first])
			{
				dfs_helper(a.first, visited);
			}
		}
	}	
 
	void dfs_utility(T src) //calling function of dfs helper
	{
		map < T, bool> visited;
		dfs_helper(src, visited);
	}

	void bfs_sssp(T src)
	{

		map<T, int> distance;
		map<T, T> parent;
		for (auto i : adjlist)
		{
			distance[i.first] = INT_MAX;
		}
		queue<T> q;
		q.push(src);
		distance[src] = 0;
		parent[src]=src;
		while (!q.empty())
		{
			T front_element = q.front();
			q.pop();

			for (auto neighbours : (adjlist[front_element]))
			{
				if (distance[neighbours.first] == INT_MAX)
				{
					q.push(neighbours.first);
					distance[neighbours.first] = distance[front_element] + 1;
					parent[neighbours.first] = front_element;
				}
			}
		}

		for (auto i : adjlist)
		{
			cout << "distance to " << i.first << " from  " << src << " is " << distance[i.first] << endl;
		}

		//suppose u want to know the hortest path beeen 2 nodes.
		//let destion be == g
		T temp = 'g';
		while (parent[temp] != temp)
		{

			cout << temp << "<--";
			temp = parent[temp];
		}cout << src << endl;

	}


	void dijkstra(T src)
	{
		map<T, int> dist;
		for (auto i : adjlist)
		{
			dist[i.first] = INT_MAX;
		}
		set<pair<int, T> > s;
		s.insert(make_pair(0, src));
		dist[src] = 0;
		while (!s.empty())
		{
			auto p = *(s.begin());
			int nodedist = p.first;// sorce node ka distance
			T temp = p.second;
			s.erase(s.begin());

			for (auto neigh : adjlist[temp])
			{
				if (nodedist + neigh.second < dist[neigh.first])//neigh.second distance h adjlist me
				{

					//purane wale ko delete karo and naye wale ko dalo
					auto f = s.find(make_pair(dist[neigh.first], neigh.first));
					if (f != s.end())
					{
						s.erase(f);
					}

					dist[neigh.first] = nodedist + neigh.second;
					s.insert(make_pair(dist[neigh.first], neigh.first));
				}
			}
		}
		for (auto d : dist) 
			cout << d.first << " and " << d.second << endl;
		
	}
};

int main()
{
	graph<char> g;
	g.addEdge('0', '1',4, 0);
	g.addEdge('0', '7',8, 0);
	g.addEdge('1', '7',11, 0);
	g.addEdge('1', '2',8, 0);
	g.addEdge('7', '8',7, 0);
	g.addEdge('2', '8',2, 0);
	g.addEdge('8', '6',6, 0);
	g.addEdge('2', '5',4, 0);
	g.addEdge('6', '5',2, 0);
	g.addEdge('2', '3',7, 0);
	g.addEdge('3', '3',14, 0);
	g.addEdge('3', '4',9, 0);
	g.addEdge('5', '4',10, 0);
	g.addEdge('7', '6',1, 0);
	g.print_adj();
	
	return 0;
}
