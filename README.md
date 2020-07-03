# interview-questions

<ul>
<li>What is node.js
<li>How node js works
<li>How block thread in Node.js
<li>What mechanisms on scalability do you know, what mechanisms on scalability node.js offer ?
<li>When allowed use sync methods like readFileSync ?
<li>What is pure functions, what advanages of pure functions
<li>What principes do you following while writing scripts.
<li>In your opinion which code we can call clean.
<li>What is algorithm complexity, do you know what complexity of search will be in sorted list, unsorted list.
<li>What type of data structure do you know, what type of data structure do you know in js
<li>We have function with callback, how we can rewrite in to promise ?
<li>We have list of urls, how we can fetch all of them simuntaniously.
<li>What pattern of perfomance optimization do you know.
<li>We created social network for 1 million users will be enought 4 sign hash as id for each user to maintain it, (26 letters of english alphabet plus 9 digits) 35 sign ?
<li>How db search works, how to improve perfomance of search.
<li>What mehanizm authentiacation do you know
  <li>
<pre>
function foo() {
  setTimeout(()=> {
      throw new Error('Err')
  },0)
}

try {
  foo();
} catch (error) {
  console.error('will it be fired');
}
</pre>
  <li>
On this example we can see that node.js not so singlethreaded. Operations with fs and crypto are multithreaded
<pre><code>
// process.env.UV_THREADPOOL_SIZE=8
const crypto = require('crypto');
const util = require('util');
const start = process.hrtime();

for (let i = 0; i<8; i++ ) {
  crypto.pbkdf2('secret', 'salt', 100000, 512, 'sha512', (err)=> {
    if(err) return err;
      const end = process.hrtime(start);
      console.log(util.format('crypto %d start %d end %d execute %d', 
      i, end[0], end[1], end[0]+end[1]/1e9
    ))
  })
}
</code></pre>
  <li>
Fibonacci - on this example we can discuss on recursion downsides and how it can be circumvented via memorization
1,1,2,3,5,8,13
<pre>
function fibOptimized(index) {
  const memoriationArray = [];
  function fib(index) {
    if(index < 3) {
      return 1;
    }
    if(memoriationArray[index]) {
      return memoriationArray[index];
    }
    memoriationArray[index] = fib(index - 1) + fib(index - 2);
    return memoriationArray[index]
  }
  return fib(index)
}
</pre>
 </ul>
