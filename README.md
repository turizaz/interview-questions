# interview-questions

<ul>
<li>What is node.js
<li>How node js works
<li>How block thread in Node.js
<li>What mechanisms on scalability do you know, what mechanisms of scalability node.js offer ?
<li>When allowed use sync methods like readFileSync ?
<li>What is pure functions, what advanages of pure functions
<li>What principes do you following while writing scripts.
<li>What is js context
<li>How clone object
<li>In your opinion which code we can call clean.
<li>What is algorithm complexity, do you know. What complexity of search will be in sorted list, unsorted list.
<li>What type of data structure do you know, what type of data structure do you know in js
<li>What pattern of perfomance optimization do you know.
<li>We created social network for 1 million users will be enought 4 sign hash as id for each user to maintain it, (26 letters of english alphabet plus 9 digits) 35 sign ?
<li>How db search works, how to improve perfomance of search.
<li>What mehanizm authentiacation do you know
  <li>Why do we need tests, what type of tesing do you know. What is unit testing. What pattern of writting code helps us in testing and what makes testing mode difficult
  <li>
    Rewrite to promise
    <pre>
    const http = require('https');
    const options = {
      host: 'www.random.org',
      path: '/integers/?num=1&min=1&max=10&col=1&base=10&format=plain&rnd=new'
    };
    http.request(options, function(response) {
      let str = '';
      response.on('data', function (chunk) {
        str += chunk;
      });
      response.on('end', function () {
       console.log(str);
      });
    }).end();
    </pre>
  </li>
  <li>
    <pre>
  realization of rewrite to promise
  function httpViaPromise(options) {
      return new Promise((res, rej) => {
        http.request(options, (response) => {
            let str = '';
            response.on('data', (chunk) => {
              str += chunk;
            });
            response.on('error',  (err) => {
              return rej(err);
            });
            response.on('end', () => {
              return res(str);
            });
          }).end();
      })
    }
    </pre>
  </li>
  <li>
    Call multiple http at once
    <pre>
    const list = [
      {
        host: 'www.random.org',
        path: '/integers/?num=1&min=1&max=10&col=1&base=10&format=plain&rnd=new'
      },
      {
        host: 'www.3random.org',
        path: '/integers/?num=1&min=1&max=10&col=1&base=10&format=plain&rnd=new'
      }
    ];
     Promise.all(list.map(it => {
      return httpViaPromise(it);
    })).then(console.log);
    </pre>
  </li>
  <li>
    <pre>
    const base = 8;
    const arr = [7,4,8,4,5]; => [[0,4],[1,2],[2,3]]
    </pre>
    find  indexes wich in sum will give 12
  <li>
    What will be first ?
    <pre>
    setTimeout(()=> {console.log('timeout'), 0})
    console.log('logging')
    </pre>
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
