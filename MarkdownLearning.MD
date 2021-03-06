# **1. TEXT OF MARKDOWN**<br>
It is very easy to make some words **bold** and other words *italic* with markdown. You can even link to [**Google**](www.google.com).
<br>
<br>

# **2. LISTS OF MARKDOWN**<br>
Sample 1 : Numbered Lists<br>
1. ONE<br>
2. TWO<br>
3. THREE<br>

Sample 2 : Bullet Points Lists<br>
* sin<br>
* kin<br>
* ben<br>

Sample 3 : Dashes Lists<br>
- ONE
  - 1.1
  - 1.2
- TWO<br>
  - 2.1
  - 2.2
<br>

# **3. IMAGES OF MARKDOWN**<br>
Insert a image here:<br>
![La La Land](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/psb.jpg?raw=true)
<br>

# 4. About Heading 
Sometimes it is useful to ave different levels of heading to structure your documents. Start lines with a '#' to create headings. Mutiple '##' in a row denote smaller heading sizes.
## Second Level heading
### Third Level heading
#### Fourth Level heading
##### Fifth Level heading
###### Sixth Level heading

# 5. About quote
Use the '>' character.
> All men are created equal.
> -Thomas Jefferson

# **6. INSERT CODE**
* Sample 1
```
#include<stdio.h>
int main()
{
	int a=1,b=2;
	a=a^b;
	b=a^b;
	a=a^b;
	printf("%d %d\n",a,b);
}
```
* Sample 2
```C
#include<stdio.h>
int main()
{
	int a=1,b=2;
	a=a^b;
	b=a^b;
	a=a^b;
	printf("%d %d\n",a,b);
}
```

# **7. Syntax Guide**
Here is an overview of Markdown syntax that you can use anywhere on GitHub or in your own Markdown editor.  
### 7.1 Headers
> \# This is an \<h1> tag  
> \## This is an \<h2> tag  
> \###### This is an \<h6> tag  

### 7.2 Emphasis
```
*This text will be italic*  
_This will also be italic_  

**This text will be bold**  
__This will also be bold__  

_You **can** combine them_

```  
Here are the effects.  
> *This text will be italic*  
> _This will also be italic_  
> **This text will be bold**  
> __This will also be bold__  
> _You **can** combine them_  

# 8.GitHub Flavored Markdown   
### 8.1 Task Lists
 - [x] item1  
 - [x] item2  
 - [ ] item3  
 - [ ] item4  

### 8.2 Tables  
CELL-1-1	|CELL-1-2	|CELL-1-3	|  
----------------|---------------|---------------|  
Cell-2-1	|Cell-2-2	|Cell-2-3	|   
Cell-3-1	|Cell-3-2	|Cell-3-3	|  

### 8.3 Strikethrough
~~This is a sentence which I want to cross out.~~
