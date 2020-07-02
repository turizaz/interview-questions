# interview-questions

<ul>
  <li>What is node.js</li>

<li>What principes do you following while writing scripts.
<li>In your opinion which code we can call clean.
<li>What is algorithm complexity, do you know what complexity of search will be in sorted list, unsorted list.
<li>What type of data structure do you know, what type of data structure do you know in js
<li>We have function with callback, how we can rewrite in to promise ?
<li>We have list of urls, how we can fetch all of them simuntaniously.
<li>What pattern of perfomance optimization do you know.
<li>We created social network for 1 million users will be enought 4 sign hash as id for each user to maintain it, (26 letters of english alphabet plus 9 digits) 35 sign ?
<li>How db search works, how to improve perfomance of search.
  </ul>
<pre>
function foo() {
  setTimeout(()=> {
      throw new Error('Err')
  },0)
}

try {
  foo();
} catch (error) {
  console.error('error catch');
}
</pre>

<br/>Not so singlethreaded
<pre>
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
</pre>
