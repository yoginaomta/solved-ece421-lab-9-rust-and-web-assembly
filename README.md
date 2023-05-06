Download Link: https://assignmentchef.com/product/solved-ece421-lab-9-rust-and-web-assembly
<br>
<h1>Part 1: Starting Web Assembly</h1>

Rust gives programmers low-level control and reliable performance. It is free from the non-deterministic garbage collection pauses that plague JavaScript. Programmers have control over indirection, monomorphization, and memory layout.

WebAssembly in action

As of now, you might have imagined what WebAssembly can do. Now let me show you some great examples that can motivate you further. The developers at wasm have developed a demo game using unity, which has been exported to the web using web assembly. Go ahead, try it.

Tanks Demo: (https://wasm.bootcss.com/demo/)

WebAssembly (wasm)

WebAssembly (wasm) is a simple machine model and executable format with an <a href="https://webassembly.github.io/spec/">extensive specification.</a> It is designed to be portable, compact, and execute at or near-native speeds.

As a programming language, WebAssembly is comprised of two formats that represent the same structures, albeit in different ways:

<ul>

 <li>The .wat text format (called wat for “<strong>W</strong>eb<strong>A</strong>ssembly <strong>T</strong>ext”) uses <a href="https://en.wikipedia.org/wiki/S-expression">S</a><a href="https://en.wikipedia.org/wiki/S-expression">–</a><a href="https://en.wikipedia.org/wiki/S-expression">expressions</a><a href="https://en.wikipedia.org/wiki/S-expression">.</a></li>

 <li>The .wasm binary format is lower-level and intended for consumption directly by wasm virtual machines.</li>

</ul>

For reference, here is a factorial function in wat:

<table width="603">

 <tbody>

  <tr>

   <td width="65"> (module</td>

   <td colspan="8" width="538"> </td>

  </tr>

  <tr>

   <td colspan="8" width="297">  (func $fac (param f64) (result f64)</td>

   <td rowspan="12" width="306"> </td>

  </tr>

  <tr>

   <td colspan="4" width="121">    get_local 0     f64.const 1</td>

   <td colspan="4" rowspan="2" width="176">  </td>

  </tr>

  <tr>

   <td colspan="2" width="81">    f64.lt</td>

   <td colspan="2" width="40"> </td>

  </tr>

  <tr>

   <td colspan="6" width="153">    if (result f64)</td>

   <td colspan="2" rowspan="8" width="144"> </td>

  </tr>

  <tr>

   <td colspan="5" width="137">      f64.const 1</td>

   <td rowspan="7" width="16">    </td>

  </tr>

  <tr>

   <td width="65">    else</td>

   <td colspan="4" width="72"> </td>

  </tr>

  <tr>

   <td colspan="5" width="137">      get_local 0       get_local 0       f64.const 1</td>

  </tr>

  <tr>

   <td colspan="3" width="105">      f64.sub</td>

   <td colspan="2" width="32"> </td>

  </tr>

  <tr>

   <td colspan="4" width="121">      call $fac</td>

   <td rowspan="3" width="16"> </td>

  </tr>

  <tr>

   <td colspan="3" width="105">      f64.mul</td>

   <td rowspan="2" width="16"> </td>

  </tr>

  <tr>

   <td width="65">    end)</td>

   <td colspan="2" width="40"> </td>

  </tr>

  <tr>

   <td colspan="7" width="233">  (export “fac” (func $fac)))</td>

   <td width="64"> </td>

  </tr>

  <tr>

   <td width="65"></td>

   <td width="16"></td>

   <td width="24"></td>

   <td width="16"></td>

   <td width="16"></td>

   <td width="16"></td>

   <td width="80"></td>

   <td width="64"></td>

   <td width="306"></td>

  </tr>

 </tbody>

</table>

For more information about the webAssembly syntax and text format, please refer to : <a href="https://developer.mozilla.org/en-US/docs/WebAssembly/Understanding_the_text_format">https://developer.mozilla.org/en</a><a href="https://developer.mozilla.org/en-US/docs/WebAssembly/Understanding_the_text_format">–</a><a href="https://developer.mozilla.org/en-US/docs/WebAssembly/Understanding_the_text_format">US/docs/WebAssembly/Understanding_the_text_format</a>

To      transform     the     above      wat      code     to     wasm,     you      can     use     the       wat2wasm

<a href="https://webassembly.github.io/wabt/demo/wat2wasm/">(</a><a href="https://webassembly.github.io/wabt/demo/wat2wasm/">https://webassembly.github.io/wabt/demo/wat2wasm/)</a> demo with the above code.<strong> Question 1: Change the above code as follows: </strong>

<ul>

 <li>Change the function name into <strong><em>RecursiveCount</em></strong></li>

 <li>Change the function argument and return type to i32</li>

 <li>Change the logic of the function, so tween 1 and 9) and the number 10.</li>

</ul>

For example      RecursiveCount(9)=9+10 =19




RecursiveCount(7)= 7+8+9+10=34

Transform the code after these changes to <em>.wasm</em> and <strong>DEMO this deliverable to the lab instructor. (Hint: all you need to write is already in the program)</strong>

<strong>Part 2: Hello, World!</strong>instead of returning the factorial of a number, it returns the sum of all the integers in a range between any number (be

To set up the toolchain for compiling Rust programs to WebAssembly and integrate them into JavaScript, you have to follow the following steps:

<ul>

 <li>You need the rust toolchain (rustup, rustc, and cargo), you should already have it installed in your machine. For more information, review Lab 1.</li>

 <li>You need wasm-pack, which is your one-stop-shop for building, testing, and publishing Rustgenerated WebAssembly. Get it from here: <a href="https://rustwasm.github.io/wasm-pack/installer/">https://rustwasm.github.io/wasm</a><a href="https://rustwasm.github.io/wasm-pack/installer/">–</a><a href="https://rustwasm.github.io/wasm-pack/installer/">pack/installer/</a></li>

 <li>You need cargo-generate to helps you get up and running quickly with a new Rust project by leveraging a pre-existing git repository as a template. To install cargo-generate run the following command:</li>

</ul>

cargo install cargo-generate

<ul>

 <li>Finally, you need npm, which is a package manager for JavaScript. We will use it to install and run a JavaScript bundler and development server. To install npm, follow the instruction from here: <a href="https://www.npmjs.com/get-npm">https://www.npmjs.com/get</a><a href="https://www.npmjs.com/get-npm">–</a><a href="https://www.npmjs.com/get-npm">npm</a></li>

</ul>

Now, let’s create our first WebAssembly project, a web page that alerts “Hello World!”.

<ul>

 <li>To start the project, you can clone a project template which comes pre-configured with sane defaults, so you can quickly build, integrate, and package your code for the web. To clone the project template, use the following command:</li>

</ul>

cargo generate –git https://github.com/rustwasm/wasm-pack-template

<ul>

 <li>Running the command should prompt you for the new project’s name. Name your project “wasmis-prime”</li>

 <li>Then take a look at the project contents:</li>

 <li>Let’s take a look at a /src/lib.rs</li>

</ul>

The src/lib.rs file is the root of the Rust crate that we are compiling to WebAssembly. It uses wasmbindgen to interface with JavaScript. It imports the window.alert JavaScript function, and exports the greet Rust function, which alerts a greeting message.

<ul>

 <li>Ensure that we have Rust 1.30 or newer and the wasm32-unknown-unknown target installed via rustup,</li>

 <li>Compile our Rust sources into a WebAssembly .wasm binary via cargo,</li>

 <li>Use wasm-bindgen to generate the JavaScript API for using our Rust-generated WebAssembly. To do all of that, run this command inside the project directory:</li>

</ul>

<table width="603">

 <tbody>

  <tr>

   <td width="38"> </td>

   <td width="565">wasm-pack build</td>

  </tr>

  <tr>

   <td colspan="2" width="603">6- When the build has completed, we can find its artifacts in the pkg directory, and it should have</td>

  </tr>

 </tbody>

</table>

these contents:

running the following command within the project directory:

<table width="603">

 <tbody>

  <tr>

   <td width="38"> </td>

   <td width="565">npm init wasm-app www</td>

  </tr>

 </tbody>

</table>

Here’s what our new wasm-is-prime/www subdirectory contains:

<ul>

 <li>To ensure that the local development server and its dependencies are installed, run npm install within the wasm-is-prime/www subdirectory:</li>

</ul>

<table width="603">

 <tbody>

  <tr>

   <td width="38"> </td>

   <td width="565">npm install</td>

  </tr>

 </tbody>

</table>

Note that this command only needs to be run once, and will install the webpack JavaScript bundler and its development server.

<ul>

 <li>To incrementally develop our project, we need to specify the dependencies to include wasm-isprime</li>

</ul>

Do that by opening up wasm-is-prime/www/package.json and editing the “dependencies” to add a “wasm-is-prime “: “file:../pkg” entry:

<table width="603">

 <tbody>

  <tr>

   <td colspan="2" width="603">import * as wasm from “wasm-is-prime”; wasm.greet();</td>

  </tr>

  <tr>

   <td colspan="2" width="603">11- Since we declared a new dependency, we need to install it:</td>

  </tr>

  <tr>

   <td width="38"> </td>

   <td width="565">npm install</td>

  </tr>

  <tr>

   <td colspan="2" width="603">12- Finally, open a new terminal for the development server. Running the server in a new terminal lets</td>

  </tr>

 </tbody>

</table>

us leave it running in the background, and doesn’t block us from running other commands in the meantime. In the new terminal, run this command from within the wasm-is-prime/www directory:

<table width="603">

 <tbody>

  <tr>

   <td width="142">     npm run start</td>

   <td width="461"> </td>

  </tr>

  <tr>

   <td colspan="2" width="603">Navigate your Web browser to <a href="http://localhost:8080/">http://localhost:8080/</a><a href="http://localhost:8080/">,</a> and you should be greeted with an alert message:</td>

  </tr>

 </tbody>

</table>




Anytime you make changes and want them reflected on <a href="http://localhost:8080/">http://localhost:8080/,</a> just re-run the wasmpack build command within the wasm-is-prime directory.

For more tutorials refer to the online book: <a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">https://rustwasm.github.io/book/game</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">–</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">of</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">life/introduction.html#tutorial</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">–</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">conways</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">–</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">game</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">–</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">of</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">–</a><a href="https://rustwasm.github.io/book/game-of-life/introduction.html#tutorial-conways-game-of-life">life</a> • <strong>DEMO this deliverable to the lab instructor.</strong>

<h1>Part 3: Implementing is-prime app</h1>

is-prime app is a small application that takes input from the user (the input must be an integer). Then, it checks if this input is prime and alerts the user with the results of the check. For example, if the user inputs a prime number, the application should show an alert message that says, “your input is a prime number.” Otherwise, the app should display a message that says, “your input is NOT a prime number.”

1- In the last part, we cloned an initial project template. We will modify that project template now. Let’s begin by modifying the wasm-is-prime/src/lib.rs by adding the following two functions as follows:

<table width="603">

 <tbody>

  <tr>

   <td width="121">#[wasm_bindgen]</td>

   <td colspan="4" width="482"> </td>

  </tr>

  <tr>

   <td colspan="3" width="257">pub fn CheckPrime(s: &amp;JsValue) {</td>

   <td colspan="2" width="346"> </td>

  </tr>

  <tr>

   <td colspan="4" width="414">     let mut input: String = s.as_string().unwrap();</td>

   <td rowspan="2" width="189"> </td>

  </tr>

  <tr>

   <td colspan="2" width="198">     if(is_prime(input)){</td>

   <td colspan="2" width="216"> </td>

  </tr>

  <tr>

   <td width="121"></td>

   <td width="77"></td>

   <td width="59"></td>

   <td width="157"></td>

   <td width="189"></td>

  </tr>

 </tbody>

</table>

npm run start

<strong>5- </strong>The app should be up and running now. However, it does not apply a primality test. Instead, it returns true regardless of the value of the input. Therefore, you need to add the code in lib.rs that checks if the user input is prime or not. <strong>(Hint: you can use any crate that performs primality tests which you may have used in Lab1).</strong>