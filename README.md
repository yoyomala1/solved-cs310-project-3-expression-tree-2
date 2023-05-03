Download Link: https://assignmentchef.com/product/solved-cs310-project-3-expression-tree-2
<br>
<strong><u>Topics Covered</u></strong>

Trees, Recursion, Stacks, and Queues

<strong>         </strong><strong> </strong>Overview

In this project, you will be working with expression trees represented in First-Child-Next-Sibling format. Basic features of the tree include:

<ul>

 <li>As an expression tree, every node represents either an operator or an operand. We restrict our operands to be integers only. For operators, we only consider the ones included in the table below. Refer Weiss 11.2.4 (pp. 468) for more details.</li>

 <li>As a First-Child-Next-Sibling tree, each node keeps two links, one to its left child (if it is not a leaf) and one to its right sibling (if it is not the rightmost sibling) in the normal binary expression tree. Refer Weiss 18.1.2 (pp. 653) for more details.</li>

</ul>




<table width="553">

 <tbody>

  <tr>

   <td width="99">Operator</td>

   <td width="151">Definition</td>

   <td width="151">Example</td>

   <td width="151">Example Evaluation</td>

  </tr>

  <tr>

   <td width="99">+</td>

   <td width="151">Addition</td>

   <td width="151">5 + 3</td>

   <td width="151">8</td>

  </tr>

  <tr>

   <td width="99">–</td>

   <td width="151">Subtraction</td>

   <td width="151">5  – 3</td>

   <td width="151">2</td>

  </tr>

  <tr>

   <td width="99">*</td>

   <td width="151">Multiplication</td>

   <td width="151">5  * 3</td>

   <td width="151">15</td>

  </tr>

  <tr>

   <td width="99">/</td>

   <td width="151">(integer) Division</td>

   <td width="151">5  / 3</td>

   <td width="151">1</td>

  </tr>

  <tr>

   <td width="99">%</td>

   <td width="151">Remainder</td>

   <td width="151">5 % 3</td>

   <td width="151">2</td>

  </tr>

  <tr>

   <td width="99">~</td>

   <td width="151">Negation</td>

   <td width="151">~ 5</td>

   <td width="151">-5</td>

  </tr>

 </tbody>

</table>




Examples: Representations of the expression <strong>(5+3)*((5*10)/2)</strong> is shown below.




<em><u>Figure 1</u></em><em>: Binary Tree Representation</em><em><sub>                           </sub></em><em><u>Figure 2</u></em><em>: First-Child-Next-Sibling Tree Representation </em>







A tree node in both representations, maintain three fields: value and links to its two children. A binary tree maintains <strong>left </strong>and <strong>right</strong> children while a FCNS tree maintain <strong>firstChild</strong> and <strong>nextSibling</strong> children. Thus, in a binary tree representation <strong>+.left</strong> is <strong>5</strong> and <strong>+.right</strong> is <strong>3</strong> while in the FCNS representation <strong>+.firstChild</strong> is <strong>5</strong> and <strong>+.nextSibling</strong> is <strong>/</strong>. Note that the root nodes in both representations are the same.

<h1>Classes Overview</h1>

<strong>ExpressionBinaryTree</strong> and <strong>BinaryTreeNode</strong> <strong>(ExpressionBinaryTree.java)</strong>:  These two classes are used to represent expressions as binary trees.  They are already implemented and provided to you.  Do not make any modification to them.

<strong>Stack</strong> <strong>(Stack.java)</strong> and <strong>Queue</strong> <strong>(Queue.java)</strong>:  These two are generic implementation of stack and queue data structures respectively.  You will find them useful in

<table width="566">

 <tbody>

  <tr>

   <td width="418">multiple tasks you need to implement in this project.<strong> </strong></td>

   <td width="148"><em><u>Figure 3</u></em><em>: FCNS Tree reorganized</em></td>

  </tr>

 </tbody>

</table>

<h2>ExpressionFCNSTree and FCNSTreeNode</h2>

<strong>(ExpressionFCNSTree.java)</strong>:  These two classes are used to represent expressions as FCNS-format trees.  FCNSTreeNode is already implemented and provided to you.  You should use it without making any modification. <strong>ExpressionFCNSTree</strong> is the main class that you will need to implement.  We have provided the signature and description of all required methods in the template Java file. Below is the list of main tasks.

<strong> </strong>

<strong><u>Task 1: </u></strong><u>Reporting tree properties</u>, including the size, height, and the number of tree nodes with certain features.




<strong><u>Task 2: </u></strong><u>Generating string representation</u> of the tree.  You will need to generate a string representing pre-order, post-order, and level-order (breadth-first) tree traversal of the FCNS tree respectively.  Check the template file for format requirements and examples. For example, based on the FCNS tree in Figure 4, we should have the following string representations:

<ul>

 <li>Prefix: “+ % 5 3 10 “</li>

 <li>Postfix: “3 5 10 % + “</li>

 <li>Level-order: “+ % 5 10 3 “</li>

</ul>




<strong><u>Task 3:</u></strong><u> Construct a FCNS tree</u> from an expression in prefix notation using method buildTree().  This method should accept a String parameter filename, open the file and construct a FCNS expression tree based on the file contents.  Each input file contains a numeric expression in prefix notation. For example, <strong>* + 5 3 / * 5 10 2</strong> represents <strong>(5+3)*((5*10)/2)</strong> and

corresponds to a FCNS tree shown in Figure 2.  You can assume that the input file is error-free and that operators/operands are separated by a space.  More examples are included in Figure 3 and 4.




<em>Figure 3: FCNS for </em><strong><em>* ~ 5 10</em></strong><em>            </em><sup> </sup><sub>                      </sub><em>Figure 4: FCNS for </em><strong><em>+ % 5 3 10</em></strong>

<strong>Allowed Operators</strong>: add(+), subtract(-), multiply(*), divide(/), mod(%), negate(~).  See the previous table for definitions and examples. Note that the tree supports unary operator ~ which can complicate your code.




<strong>Allowed Operands:</strong>  integers (positive, negative, zero).

<strong> </strong>

<strong><u>Task 4:</u></strong><u> Construct a binary tree from the FCNS tree</u> using buildBinaryTree(). You will need to create the corresponding binary tree from the FCNS tree.  For example, given the FCNS tree in Figure 2, a binary tree as in Figure 1 should be constructed and the root should be returned.




<strong><u>Task 5:</u></strong><u> Simulate in-order binary tree traversal with the FCNS tree</u> using toStringPrettyInFix(). You will need to generate an infix notation of the expression.  This is essentially simulating the in-order traversal of the corresponding binary expression tree.  Note that you are NOT allowed to first construct the binary tree and then perform an in-order traversal to generate the string.  The infix notation must be generated from the FCNS tree directly without building a binary tree.  Parentheses need to be inserted to make the expression correct and human-readable.  For example, the string generated from Figure 2 should be <strong>(5+3)*((5*10)/2)</strong>.

<strong> </strong>

<strong><u>Task 6: </u></strong><u>Evaluate the expression to an integer from FCNS tree</u>, both recursively and iteratively. In this task, you will compute the result of the expression using the FCNS tree.<strong>  </strong>




<strong><u>Task 6.1: Recursive Implementation.</u></strong> Implement method evaluate() for this task. The method walks through the tree and update two attributes for individual nodes: an integer <strong>value</strong> and a boolean flag <strong>nan</strong> to indicate whether the expression is not-a-number.  Normally, the value of an operand node is the integer value of that operand; the value of an operator is the integer value associated with sub-expression rooted at that node.  For example, the value of each tree node in Figure 4 after we perform evaluate() is given in the following table:

<table width="547">

 <tbody>

  <tr>

   <td width="97">Node symbol</td>

   <td width="63">5</td>

   <td width="72">3</td>

   <td width="72">%</td>

   <td width="87">10</td>

   <td width="156">+</td>

  </tr>

  <tr>

   <td width="97">Node.value</td>

   <td width="63">5</td>

   <td width="72">3</td>

   <td width="72">2</td>

   <td width="87">10</td>

   <td width="156">12</td>

  </tr>

  <tr>

   <td width="97">Reason</td>

   <td width="63">operand</td>

   <td width="72">operand</td>

   <td width="72">5 % 3</td>

   <td width="87">operand</td>

   <td width="156">(5%3)+ 10 = 2+10</td>

  </tr>

 </tbody>

</table>




The special situation not-a-number is triggered when a division has a zero divisor.  Then the not-anumber flag needs to be propagated following this rule: any operation applying on a not-a-number yields a not-a-number result. When a node is marked as not-a-number, its value should be null.




<u>Task 6.2:<strong> Iterative Implementation. </strong></u>Implement method evaluateNonRec() for this task. This method returns an integer value without changing any tree node attributes.  For this task, you can assume all expressions are valid and there is no division-by-zero.




Sample inputs and results:

<table width="587">

 <tbody>

  <tr>

   <td width="197"><strong>Input (prefix notation) </strong></td>

   <td width="200"><strong>Pretty-Infix notation </strong><strong>(or Binary Tree Infix </strong><strong>Traversal with parenthesis) </strong></td>

   <td width="190"><strong>FCNS Infix notation </strong><strong>(</strong>implementation not required<strong>) </strong></td>

  </tr>

  <tr>

   <td width="197">* + 5 3 / * 5 10 2</td>

   <td width="200">((5+3)*((5*10)/2))</td>

   <td width="190">5 3 + 5 10 * 2 / *</td>

  </tr>

  <tr>

   <td width="197">* ~ 5 10</td>

   <td width="200">((-5) * 10)</td>

   <td width="190">5 ~ 10 *</td>

  </tr>

  <tr>

   <td width="197">+ % 5 3 10</td>

   <td width="200">((5 % 3) + 10)</td>

   <td width="190">5 3 % 10 +</td>

  </tr>

  <tr>

   <td width="197">/ 10 ~ * 5 2</td>

   <td width="200">(10 / -(5 * 2))</td>

   <td width="190">10 5 2 * ~ /</td>

  </tr>

 </tbody>

</table>

Table continued…




<table width="510">

 <tbody>

  <tr>

   <td width="198"><strong>FCNS Postfix notation </strong></td>

   <td width="192"><strong>FCNS Level Order  </strong></td>

   <td width="120"><strong>Result </strong></td>

  </tr>

  <tr>

   <td width="198">3 5 10 5 2 * / + *</td>

   <td width="192">* + 5 / 3 * 5 2 10</td>

   <td width="120">200</td>

  </tr>

  <tr>

   <td width="198">5 10 ~ *</td>

   <td width="192">* ~ 5 10</td>

   <td width="120">-50</td>

  </tr>

  <tr>

   <td width="198">3 5 10 % +</td>

   <td width="192">+ % 5 10 3</td>

   <td width="120">12</td>

  </tr>

  <tr>

   <td width="198">2 5 * ~ 10 /</td>

   <td width="192">/ 10 ~ * 5 2</td>

   <td width="120">-1</td>

  </tr>

 </tbody>

</table>







<h1>Big-O</h1>




Template given to you in the starter package contains instructions on the REQUIRED Big-O runtime for a subset of methods. For those methods, your implementation should not have a higher Big-O and you will be graded on this.




<h1>Testing</h1>




Test cases will not be provided for this project. However, feel free to create test cases by yourselves. In addition, the main methods provided along with the template classes contain useful code to test your code. You can use command like “java ExpressionFCNSTree” to run the testing defined in main( ).  You could also edit main( ) to perform additional testing.  As always, a part of your grade will be based on automatic grading using test cases that are not provided to you.  A set of expression files are provided to you for testing purpose.





