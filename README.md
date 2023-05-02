Download Link: https://assignmentchef.com/product/solved-cop3275-programming-assignment-6
<br>
<ul>

 <li>You have to upload your codes in both Canvas and the Judge system at <a href="https://cop3275.cise.ufl.edu/">https://cop3275.cise.ufl.edu</a></li>

 <li>For guide on how to access the Judge, visit Judge Access Page under Pages section in Canvas.</li>

 <li>The judge will run test cases against your code and assign it a grade. You can have multiple submission for the same problem but you have to choose which one is the final (we will consider your final submission for grading). Canvas is only used for record keeping.</li>

 <li>When upload on canvas, zip your programs in a zipfile with your ufid as name (nothing more, just 8 digit ufid, for instance 12345678.zip). Name your files (inside the zipped archive) p1.c, p2.c, and so on.</li>

 <li>For all the problems input is read from standard input (i.e. read using scanf) and must be written to standard output (i.e. printf).</li>

 <li><strong>Don’t print extra stuff. Since the assignments are automatically graded, if the output doesn’t match the expected output, you will not get the points. For instance: </strong></li>

</ul>

<strong>If the problem is to read a number and return its square, the expected output is a number (i.e. “printf(“%d”,i*i)”). If you print using something like “printf(“square is %d”,i*i);” you will not receive any points.</strong>

<ul>

 <li>The assignment is due on 11:59 pm Sunday April 28<sup>th</sup>  There is a 20% penalty for late submission of one day. No submission is accepted beyond that time.</li>

</ul>




<strong>Problem 1:  Sparse! (4 pts.) </strong>

You are again given two vectors as input and you have to compute and print the elementwise multiplication and determine whether they are perpendicular or not (Similar to Dense! Problem). The difference is this time you are given the input in sparse representation and you have to print the computed elementwise multiplication <strong>in sorted order of indices</strong>. Also note that the input is given, in a <strong>random</strong> order (it is not sorted) so you must sort them yourself.

Sparse representation of vectors is useful when a lot of elements in the vector are zero and hence, it is wasteful to represent them using regular arrays (in terms of memory and in many cases, computation). In this format, the index and the value of each <strong>non zero </strong>element is given correspondingly. For instance:

V<sub>dense</sub> = [1,0,0,6,0]  -&gt; V<sub>sparse </sub>= [(0,1),(3,6)]

First, N the number of non zero elements of first vector is given in the first and line and then N elements are given (each in a separate line) as index&lt;whitespace&gt;value (e.g. “1 3”). The M (= number of nonzero elements of the second vector) and its M elements in a similar format.




<table width="623">

 <tbody>

  <tr>

   <td width="312">Sample input (same vectors as Problem 1):52 200 54 -303 105  566  200 82 -11 23 25 1</td>

   <td width="312">Sample output:0 402                     -203                     20 5 5not perpendicular </td>

  </tr>

 </tbody>

</table>







Suggestions:

<ul>

 <li>Have a struct that represents an element (let’s tag it v_element) of the vector (with two integer members: index and value). Represent each vector as an array of v_element s. Sizes of the arrays are the N and M given in the input.</li>

 <li>Iterate over both arrays in a way that you find elements with the same index and compute the multiplication of their value. Store it in a new array.</li>

 <li>Use the qsort function to sort the resulting array. For that you need to write a comparator function that tells which one of the given elements is less than the other one (compare v_element indices).</li>

 <li>If all the elements of the results are zero, print an empty newline followed by perpendicular.</li>

</ul>




<strong>Problem 4: IP address (3 pts.)</strong>

In today’s world, we are all connected through our devices. Internet Protocol (IP) is at the heart of Internet where it specifies an address for every device that is connected to the network. In general, Internet is a big network of connected subnetworks (subnets) and the addresses follow a hierarchy based on the subnets. In this problem you are given two <em>IP addresses</em> and a <em>Network Mask</em> and you have to determine whether those two IP addresses belong to the same subnet or not.

An IP address is written as four numbers between 0 and 255 separated by a dot character. For instance: 192.168.1.1 or 254.178.3.51 are valid IP addresses but 284.120.12.230 (284 is greater than 255) or 123.123..1 (third number is not given) are not. Each number can be represented with 8 bits and hence a byte (unsigned). So, we can put these 4 bytes together and store them in an integer variable that has 4 bytes (one byte per number that is separated by a dot). For instance, 254.23.10.1 can be broken down into:

254 =&gt; 11111110

23 =&gt; 00010111

10 =&gt; 00001010

1 =&gt;  00000001

So, the corresponding 32 bit integer is 11111110000101110000101000000001 which when seen as an unsigned integer in decimal (base 10) is 4,262,922,753.

A network mask is a number that is used to mask the exact address of the device and instead show the subnet address. Typically, because of the Internet’s hierarchy, this number when represented in binary, has its N most significant bits set to 1. For instance, 11111111100000000000000000000000 (or in decimal 4,286,578,688) is a valid subnet mask (note that because of equivalence of IP address in their dot notation to integer numbers we can also write a subnet mask in the IP format. For instance, the subnet mask above can be written as 255.128.0.0 – but you don’t need this conversion for this problem).

When you <strong><em>bitwise and</em></strong> the IP address and the subnet mask, it extracts the most significant bits of the given IP address. It is usually known as the subnet address. Two IPs belong to the same subnet if they have the same subnet address.

In this problem, you are given two IP addresses in dot notation and a number N corresponding to the number of bits that are set to 1 in the subnet mask. Print 1 if they belong to the same subnet and 0 otherwise.

<table width="623">

 <tbody>

  <tr>

   <td width="312"><strong>Sample input: </strong></td>

   <td width="312"><strong>Sample output: </strong></td>

  </tr>

  <tr>

   <td width="312">192.168.1.10192.172.23.14413</td>

   <td width="312">1</td>

  </tr>

  <tr>

   <td width="312">10.10.20.20 11.10.20.207</td>

   <td width="312">1</td>

  </tr>

  <tr>

   <td width="312">10.10.20.20 11.10.20.208</td>

   <td width="312">0</td>

  </tr>

 </tbody>

</table>


