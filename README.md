Download Link: https://assignmentchef.com/product/solved-cs220-lab7-assembler
<br>
Convert the following assembly code into “symbol less” code by replacing each symbol (variable or label) with its corresponding value (number).  Also, please label the ROM address (line number) for each real instruction.

<h1>1.       Sum.asm</h1>




<table width="653">

 <tbody>

  <tr>

   <td width="247"><strong>Assembly Code</strong><strong>(raw with symbols)</strong></td>

   <td width="84"><strong>ROM Address</strong><strong>(line number)</strong></td>

   <td width="322"><strong>Assembly Code</strong><strong>(cleaned and without symbols)</strong></td>

  </tr>

  <tr>

   <td width="247">// Computes sum = R2 + R3// (R2 refers to RAM[2]) @R2D=M@R3D=D+M   // Add R2 + R3 @sumM=D     // sum = R2 + R3 </td>

   <td width="84"> </td>

   <td width="322"> </td>

  </tr>

 </tbody>

</table>




<h1>2.       Max.asm</h1>




<table width="653">

 <tbody>

  <tr>

   <td width="247"><strong>Assembly Code</strong><strong>(raw with symbols)</strong></td>

   <td width="84"><strong>ROM Address</strong><strong>(line number)</strong></td>

   <td width="322"><strong>Assembly Code</strong><strong>(cleaned and without symbols)</strong></td>

  </tr>

  <tr>

   <td width="247">// Computes R2=max(R0, R1)// (R0,R1,R2 refer to// RAM[0],RAM[1],RAM[2]) @R0D=M@R1D=D-M@OUTPUT_FIRSTD;JGT@R1D=M@OUTPUT_D0;JMP(OUTPUT_FIRST)@R0D=M(OUTPUT_D)@R2M=D(INFINITE_LOOP)@INFINITE_LOOP0;JMP</td>

   <td width="84"> </td>

   <td width="322"> </td>

  </tr>

 </tbody>

</table>

<h1></h1>

<h1>3.       Rect.asm</h1>




<table width="653">

 <tbody>

  <tr>

   <td width="247"><strong>Assembly Code</strong><strong>(raw with symbols)</strong></td>

   <td width="84"><strong>ROM Address</strong><strong>(line number)</strong></td>

   <td width="322"><strong>Assembly Code</strong><strong>(cleaned and without symbols)</strong></td>

  </tr>

  <tr>

   <td width="247">// Draws a rectangle at// the top-left corner of // the screen.// The rectangle is 16// pixels wide and R0// pixels high. @R0D=M@INFINITE_LOOPD;JLE@counterM=D@SCREEND=A@addressM=D(LOOP)@addressA=MM=-1@addressD=M@32D=D+A@addressM=D@counterMD=M-1@LOOPD;JGT(INFINITE_LOOP)@INFINITE_LOOP0;JMP</td>

   <td width="84"> </td>

   <td width="322"> </td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong>UML Diagram of Entire Assembler Program</strong>




<strong>A brief Java refresher:</strong>

<table>

 <tbody>

  <tr>

   <td width="367"><strong>Write Java code to implement the following enum:</strong></td>

   <td width="286"><strong> </strong></td>

  </tr>

  <tr>

   <td width="367"><strong>What does the following code display?</strong><strong> </strong>String code = “t0;JMP  //unconditional jump  “;System.<strong><em>out</em></strong>.println(code.trim());</td>

   <td width="286"><strong> </strong></td>

  </tr>

  <tr>

   <td colspan="2" width="653"><strong>How would you extract the </strong>JMP<strong> from the </strong>code<strong> string above?  Write the Java code to do so.</strong></td>

  </tr>

  <tr>

   <td width="367"><strong>What is assigned to the variable </strong>dest<strong> ?</strong><strong> </strong>String code = “D=M;JGT”;<strong>int</strong> index = code.indexOf(‘=’);String dest = (index != -1) ?code.substring(0, index) : <strong>null</strong>;</td>

   <td width="286"><strong> </strong></td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<h1>Write pseudocode for the following helper methods:</h1>

<h2>❑  <u>String cleanLine(String rawLine)</u></h2>













<ul>

 <li><u>Command parseCommandType(String cleanLine)</u></li>

</ul>




<ul>

 <li><u>boolean isValidName(String symbol)</u></li>

</ul>







<ul>

 <li><u>String decimalToBinary(int number)</u></li>

</ul>







<table>

 <tbody>

  <tr>

   <td width="376">CInstructionMapper</td>

  </tr>

  <tr>

   <td width="376">–    compCodes : HashMap&lt;String, String&gt;–    destCodes : HashMap&lt;String, String&gt;–    jumpCodes : HashMap&lt;String, String&gt;</td>

  </tr>

  <tr>

   <td width="376">+  CInstructionMapper()+  comp(mnemonic : String) : String+  dest(mnemonic : String) : String+  jump(mnemonic : String) : String </td>

  </tr>

 </tbody>

</table>




<strong>Write pseudocode for the following Code methods:</strong>

<strong> </strong>

<ul>

 <li>Code()</li>

</ul>




<ul>

 <li>String comp(String mnemonic)</li>

</ul>







<ul>

 <li>String dest(String mnemonic)</li>

</ul>




<ul>

 <li>String jump(String mnemonic)</li>

</ul>







<strong>Write pseudocode for the following SymbolTable methods:</strong>

<strong> </strong>

<table>

 <tbody>

  <tr>

   <td width="500">SymbolTable</td>

  </tr>

  <tr>

   <td width="500">–    <u>INITIAL_VALID_CHARS : Strin</u>g–    <u>ALL_VALID_CHARS : String</u>–    symbolTable : HashMap&lt;String, Integer&gt;</td>

  </tr>

  <tr>

   <td width="500">+  SymbolTable()+  addEntry(symbol : String, address : int) : boolean+  contains(symbol : String) : boolean+  getAddress(symbol : String) : int–  <u>isValidName(symbol : String) : boolea</u>n</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>SymbolTable()</li>

 <li>boolean addEntry(String symbol, int address)</li>

 <li>boolean contains(String symbol)</li>

 <li>int getAddress(String symbol)</li>

 <li><u>boolean isValidName(String symbol )</u> //same as earlier but rewrite using constants</li>

</ul>







<table>

 <tbody>

  <tr>

   <td width="544">Parser</td>

  </tr>

  <tr>

   <td width="544">+  <u>NO_COMMAND : char</u> // ‘N’           //constants+  <u>A_COMMAND : char</u> // ‘A’+  <u>C_COMMAND : char</u> // ‘C’+  <u>L_COMMAND : char</u> // ‘L’ –   inputFile : Scanner                //file stuff + debugging–   lineNumber : int–   rawLine : String –   cleanLine : String            //parsed command parts–   commandType : char–   symbol : String–    destMnemonic : String–   compMnemonic : String–   jumpMnemonic : String</td>

  </tr>

  <tr>

   <td width="544">+  Parser(inFileName : String)        //drivers+  hasMoreCommands() : boolean+  advance() : void –    cleanLine() : void                 //parsing helpers–    parseCommandType() : void–    parse() : void–    parseSymbol() : void–    parseDest() : void–    parseComp() : void–    parseJump() : void +  getCommandType() : char            //useful getters+  getSymbol() : String+  getDest() : String+  getComp() : String+  getJump() : String +  getRawLine() : String              //debugging getters+  getCleanLine() : String+  getLineNumber() : int</td>

  </tr>

 </tbody>

</table>




<ul>

 <li>cleanLine() : void //same as part 1 but rewrite using instance variables</li>

 <li>parseCommandType() : void //same as part 1 but rewrite using instance variables</li>

</ul>




<strong>Write pseudocode for the following Parser methods:</strong>

<ul>

 <li>Parser(String fileName)</li>

</ul>




<ul>

 <li>boolean hasMoreCommands()</li>

</ul>




<ul>

 <li>void advance()</li>

</ul>




<ul>

 <li>void parseSymbol()</li>

</ul>




<ul>

 <li>void parseDest()</li>

</ul>




<ul>

 <li>void parseComp()</li>

</ul>




<ul>

 <li>void parseJump()</li>

</ul>







<ul>

 <li>void parse()</li>

</ul>




<ul>

 <li>Command getCommandType()</li>

</ul>




<ul>

 <li>String getSymbol()</li>

</ul>




<ul>

 <li>String getDestMnemonic()</li>

</ul>




<ul>

 <li>String getCompMnemonic()</li>

</ul>










<ul>

 <li>String getJumpMnemonic()</li>

</ul>




<ul>

 <li>String getRawLine()</li>

</ul>




<ul>

 <li>String getCleanLine()</li>

</ul>




<ul>

 <li>int getLineNumber()</li>

</ul>