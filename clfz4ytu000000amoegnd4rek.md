---
title: "Cpp Soup"
datePublished: Sun Apr 02 2023 08:24:00 GMT+0000 (Coordinated Universal Time)
cuid: clfz4ytu000000amoegnd4rek
slug: cpp-soup
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/hvSr_CVecVI/upload/21b8a15b9827c7ce36d8db170d164ba0.jpeg
tags: cpp

---

Some old CPP notes were written by me during my freshman years. Hope some of these are still relevant.

1. ### [Two very annoying mistakes](http://cppsoup.blogspot.com/2012/08/two-very-annoying-mistakes.html)
    
    I am very good at doing silly mistakes in c++ syntax. Here are two of the most disturbing mistakes.  
    1\. Forgetting to put; after-class declaration :  
       class mb  
       {  
    int a;  
       }  
      
      Error :  "expected unqualified-id at end of input"  
      
    2\. Forgetting to leave a space after "&gt;" in map declaration.  
      map&lt;string,vector&lt;double&gt;&gt; *a;  
        Error : ‘&gt;&gt;’ should be ‘&gt; &gt;’ within a nested template argument list    Correct syntax : map&lt;string,vector&lt;double&gt; &gt;* a;The second one is more annoying . It made me google many times :)
    
2. ### [Limiting memory use to a % of total memory](http://cppsoup.blogspot.com/2012/08/limiting-memory-use-to-of-total-memory.html)
    
    One of my friends was very annoyed with his application. He thinks one unknown process occasionally eats up the total memory available. So he was asking , if there is some way to limit memory usage to a predefined portion of total available memory. I googled it, and most people say this is indeed a very very bad idea. Applications should not measure ram and occupy. If ten applications are coded, such that they occupy 1/4th of ram and are run together, then a crash is inevitable. In the process, I learnt a way to get memory-related stats on a Unix system. Just parse the file at /proc/meminfo  
      
    
    ![](http://3.bp.blogspot.com/-W4vVMSxD1CI/UCP_WVVR0AI/AAAAAAAAIYs/Jdy0kxebae0/s320/mem.png align="left")
    
    {Used cat to see meminfo}
    
    Otherwise,  a system-wide setting can also be changed using [ulimit](http://www.linuxhowtos.org/Tips%20and%20Tricks/ulimit.htm) .  For more info [read here](http://www.linuxhowtos.org/Tips%20and%20Tricks/ulimit.htm). {Read the warnings at the bottom first.}
    
      
    
3. ### [Funny C++ Declarations](http://cppsoup.blogspot.com/2012/05/funny-c-declarations.html)
    
    I was browsing through the GNU website and found a fun page. Here are some examples from that page...  
      
      
    1\. struct dumb by\[sizeof member\];  
    2\. struct by\_lightning;  
    3\. short circuit;  
    4\. void if\_removed();  
    5\. unsigned check;  
    6\. class dismissed : public annoyance  
    7\. long trousers\_with\_holes;  
      
      
    For more fun head to the source [http://www.gnu.org/fun/jokes/declarations.html](http://www.gnu.org/fun/jokes/declarations.html)
    
4. ### [Why not use void main](http://cppsoup.blogspot.com/2012/05/why-not-to-use-void-main.html)
    
    In college, while using turbo c, we learn to use "void main()". But this is against the c++ standard. This shouldn't compile. The main function must return an int value. The main function should be declared as "Int main()". And at the end "return 0" may be added to indicate that function was executed successfully. It may return 1 to indicate that some error has occurred. This is also referred to as Exit Status. It can be `EXIT_SUCCESS` (traditionally 0) and `EXIT_FAILURE`. If a return is not provided by the programmer, it will return 0 by default.  For other exit statuses you may have a look in stdlib.h(cstdlib).
    
5. ### [QVector Advantages](http://cppsoup.blogspot.com/2012/05/in-our-workplace-use-stl-as-much-as.html)
    
      
    In our lab we use stl as much as possible. Even when coding in qt we are advised to import and use STL containers. I googled this issue to know the justifications behind this favouritism. What I found is STL is a clear winner if speed is the single most important concern. On the other hand, QTL has many advantages of its own. Let me elaborate on these points with an example of the vector. QVector is easier to use than stl::vector. Qvectors are more lightweight. Whenever we copy or pass qvector , only a pointer to the vector is passed. A deep copy is used only when editing data. QVector occupies more memory to prevent the use of memory allocation operations every time expansion is required. It uses realloc() to grow by increments of 4096 bytes. Qvector has lots of interesting functions to make life easier for developers. It has a squeeze option to remove extra spaces allocated. So I believe it’s advisable to use qvector as much as possible. And in case you want to use stl:: vector , you can always convert to stl::vector like this
    
    ```plaintext
     QVector vector;
     vector << 1.2 << 0.5 << 3.14;
     std::vector stdvector = vector.toStdVector();  
    ```
    
    (reference [http://doc.qt.nokia.com/4.7/qvector.html](http://doc.qt.nokia.com/4.7/qvector.html))
    
6. ### [Assignment operator in RVALUE](http://cppsoup.blogspot.com/2012/05/assignment-operator-in-rvalue.html)
    
    I came across a line of code which looked a bit strange to me. It reads like this..  
    `x= m * (n=7);`  
    The above code is equivalent to  
    `n=7   x=m*n`  
    C++ supports using assignments on the right-hand side of the assignments operator. And we are all familiar with that. I bet you must have seen assignments like this…  
    `a=b=c;`  
    This and the previous code follows the same rule.
    
7. ### [Calling constructor from the constructor](http://cppsoup.blogspot.com/2012/05/calling-constructor-from-constructor.html)
    
      
    I was trying a few whiteboard programs, just for fun. In one of them I called a constructor from within another constructor. The code compiled without any fuss, but the code didn’t work the way I was expecting.  I found out that when calling a constructor from within a constructor a temporary unnamed constructor is created. That is the reason why the program is not behaving the way I was expecting. Check out this…  
    `   `*  
    using namespace std;class foo  
    {  
    int x;  
    public:  
    foo()  
    {  
    x=20;  
    }foo(int d)  
    {  
    x=d;  
    foo();//value should be changed to 20, but it won't  
    }  
    void show()  
    {  
    foo a;  
    *[*a.show*](http://a.show)*();// will print 20  
    foo b(10);  
    *[*b.show*](http://b.show)*();// will print 10. I was expecting it to print 20  
    return 0;  
    }*
    
8. ### [Constant functions and Mutable](http://cppsoup.blogspot.com/2012/05/constant-functions-and-mutable.html)
    
    For a c++ rookie, this syntax may look interesting ..  
      
    *void myFunc() const;*  
      
    Normally we love to see const at the beginning of a line . like "const int i = 10;". Actually above line is perfect. It tells that the function can't modify its calling object. It is referred to as a read-only function in some textbooks. It can call some more constant functions from the inside. But it can't call any normal function.  This type of function can be called from any ordinary function as well as constant functions.  
      
    Suppose you want to declare a constant function, but at the same time, you want it to modify some particular data. In that case, you need to use a mutable keyword while declaring your variables.  
      
     *mutable int x;*