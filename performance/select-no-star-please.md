# SELECT - Do not use '*' whenever possible 

## Why ? 

  * You are adding .. to he server: 
    * I/O
    * memory
    * CPU
  * You are preventing covering indexes   

## Ref:

  * https://www.oreilly.com/library/view/high-performance-mysql/9780596101718/ch04.html
