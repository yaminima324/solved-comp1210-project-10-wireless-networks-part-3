Download Link: https://assignmentchef.com/product/solved-comp1210-project-10-wireless-networks-part-3
<br>
<strong>Files to submit to Web-CAT</strong>:

<u>From Wireless Networks – Part 1</u> •        WirelessNetwork.java

<ul>

 <li>java, WiFiTest.java</li>

 <li>java, CellularTest.java</li>

 <li>java, LTETest.java</li>

 <li>java, FiveGTest.java</li>

</ul>




<u>From Wireless Networks – Part 2</u>

<ul>

 <li>java, BandwidthComparatorTest.java</li>

 <li>java, MonthlyCostComparatorTest.java</li>

 <li>java (<u>add exception handling</u>),</li>

</ul>

WirelessNetworkListTest.java




<u>New in Wireless Networks – Part 3</u>

<ul>

 <li>java (<u>with exception handling</u>), WirelessNetworksPart3Test.java</li>

 <li>InvalidCategoryException</li>

</ul>




<h1>Recommendations</h1>

You should create new folder for Part 3 and copy your relevant Part 2 source and test files to it. You should create a jGRASP project and add the new source and test files as they are created. <strong> </strong>




<strong>Specifications – </strong><strong>Use arrays in this project; ArrayLists are not allowed! </strong><strong> </strong>

<strong> Overview: </strong> Wireless Networks – Part 3 is the third of a three-part software project that involves the monthly cost and reporting for wireless networks.  The completed class hierarchy is shown in the UML class diagram above.  Part 3 of the project focuses on handling exceptions that are thrown as a result of erroneous input from the command line or the data file.  The main method in the WirelessNetworksPart3 class, which reads in the file name from the command line, will need to handle a FileNotFoundException that may result from attempting to open the file (e.g., if the file does not exist).  Also, the readFile method in WirelessNetworkList will need to handle exceptions that occur while processing the data file, including a new exception called InvalidCategoryException.

<strong> </strong>

<strong>WiFi, Cellular, LTE, and FiveG,</strong><strong> BandwidthComparator, and MonthlyCostComparator</strong>

<strong> </strong>

<strong>Requirements and Design:</strong>  There are no changes to these classes from Part 2.

<strong> </strong>

<h2>WirelessNetworkList.java</h2>

<strong> </strong>

<strong>Requirements: </strong>The WirelessNetworkList class provides methods for reading in the data file and generating the reports.  The readFile method should redesigned to handle exceptions in the data.  Reading a “good” line of data results in a new element added the WirelessNetwork array, and reading a “bad” line of data results in the line + an exception message being added the to the invalid records String array.  A new report method produces the Invalid Records Report.




<strong>Design: </strong>The readFile method from Part 2 should be redesigned to handle exceptions. The WirelessNetworkList class has fields, a constructor, and methods as outlined below.

<ul>

 <li><strong>Fields:</strong> no change from Part 2.</li>

 <li><strong>Constructor: </strong>no change from Part 2.</li>

 <li><strong>Methods:</strong> The readFile method needs to be reworked and the generateInvalidRecordsReport method needs to be added. <u>See Part 2 for the full description of other methods in this class</u>. o readFile has no return value, accepts the data file name as a String, and throws FileNotFoundException.  If a FileNotFoundException occurs when attempting to open the data file, it should be ignored in this method so that it can be handled in the calling method (i.e., main).  If a line from the file is processed successfully, a WirelessNetwork object of the appropriate category (subclass) is added to the WirelessNetwork array in the class.  However, when an exception occurs as a result from erroneous data in a line read from the file, it should be caught and handled as follows.  The line should be concatenated with a newline and the exception message and then the resulting String should be added to the invalid records String array in the class.  The three exceptions that should be caught in this method are (1) InvalidCategoryException (described below), (2) NumberFormatException, and (3) NoSuchElementException.   Note that the InvalidCategoryException must be explicitly thrown by your code if the category is not W, C, L, or F.  The NumberFormatException will be thrown automatically if the item scanned in the line from the file is not a double when Double.parseDouble expects it to be a double. The NoSuchElementException will be thrown automatically if the item scanned does not exist (i.e., data is missing).  For examples, see the output below for the Invalid Records Report.</li>

</ul>




o generateInvalidRecordsReport processes the invalid records array to produce the Invalid Records Report and then returns the report as String.  See the example result near the end of the output for WirelessNetworksPart3 that begins on page 4 and ends on page 6.

<strong>Code and Test:  </strong>See examples of exception handling in the text and the class notes.  In the catch blocks for the NumberFormatException and NoSuchElementException, the invalid line should be concatenated with a newline and the exception message, and the resulting String should be added to the invalidRecords String array. Note that for the NoSuchElementException, “: For missing input data” will need to be concatenated to the end of the toString value of the NoSuchElementException to form the complete message.




Download wireless_network_data2_exceptions.csv from the assignment page in

Canvas to test your program. Your JUnit test methods should force the exceptions described above to thrown and caught.  Since the readFile method will propagate the FileNotFoundException if the file is <u>not</u> found when the Scanner is created to read the file, test method could catch this exception to check that it was thrown.  Any other test method involving the readFile method must have the throws FileNotFoundException clause.

<strong> </strong>

<h2>InvalidCategoryException.java</h2>

<strong> </strong>

<strong>Requirements and Design: </strong>The InvalidCategoryException class defines a new subclass of the Exception class.  The constructor accepts a String categoryIn representing the invalid category, then invokes the super constructor with the message:

“For category: ” + categoryIn

See <strong>examples</strong> of creating user defined exceptions in text and class notes.




<h2>WirelessNetworksPart3.java</h2>

<strong> </strong>

<strong>Requirements: </strong>The WirelessNetworksPart3 class contains the main method for running the program. In addition to the specifications in Part 2, the main method should be modified as indicated below.




<strong>Design: </strong>The WirelessNetworksPart3 class is the driver class and has a main method described below.




o main accepts a file name as a command line argument, then within a try block, creates a WirelessNetworkList object, and then invokes its methods to (1) read the file and process the wireless network records and (2) to generate and print the <u>five reports</u> as shown in the third run in example output beginning on page 4.  If no command line argument is provided, the program should indicate this and end as shown in the first run in the example output on page 4.  If an FileNotFoundException is thrown in the readFile method in the WirelessNetworkList class, it should be caught in the catch block of the try statement in main.  The catch block should print a message (“*** Attempted to read file: ” along with the exception’s message).  For example, if the user entered “nofile.csv” as the command line argument and this file does not exit, then the Run I/O in jGRASP would look like the second run in the example output beginning on page 4).  Note that since the main method is catching FileNotFoundException, it no longer needs the throws clause in its declaration.







<strong>Code and Test:  </strong>See examples of exception handling in the text and the class notes.  Download wireless_network_data2_exceptions.csv from the assignment page in Canvas to test your program.  One of your JUnit test methods should call your main method with no argument (i.e., an empty String array). Another should call your main method with an argument this is <u>not</u> a valid file name to ensure that your catch block is covered.  Finally, a third should call your main method with an argument that is the file name above. See “Code and Test” for WirelessNetworksPart2 in Part 2 to see how to invoke your main method.

<strong> </strong>

<h1>Example Output</h1>




Three separate runs are shown below: (1) one with no command line argument, (2) one with an invalid file name as command line argument, and (3) one with valid file name as command line argument.

<strong> </strong>

<table width="639">

 <tbody>

  <tr>

   <td width="639">MMMMMM«M —-jGRASP exec: java WirelessNetworksPart3 MM§MFile name expected as command line argument. MM§MProgram ending. MM§M MM©M —-jGRASP: operation complete.MMMMMM«M —-jGRASP exec: java WirelessNetworksPart3 nofile.csvMM§M *** Attempted to read file: nofile.csv (No such file or directory)MM§M MM©M —-jGRASP: operation complete.MMMMMM«M —-jGRASP exec: java WirelessNetworksPart3 wireless_network_data2.exceptions.csvMM§M——————————-MM§MMonthly Wireless Network ReportMM§M——————————-MM§MMy Wifi (class WiFi) Cost: $45.00MM§MBandwidth: 450.0 MbpsMM§MMM§MMy Note (class Cellular) Cost: $20.00MM§MBandwidth: 5.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 1.0 GBMM§MData Used: 0.75 GBMM§MMM§MMy iPad (class LTE) Cost: $38.00MM§MBandwidth: 20.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 2.0 GB MM§MData Used: 3.0 GBMM§MMM§MMy Phone (class FiveG) Cost: $80.00MM§MBandwidth: 80.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 10.0 GB MM§MData Used: 12.0 GBMM§M</td>

  </tr>

 </tbody>

</table>




<table width="639">

 <tbody>

  <tr>

   <td width="639">MM§M—————————————–MM§MMonthly Wireless Network Report (by Name)MM§M—————————————–MM§MMy iPad (class LTE) Cost: $38.00MM§MBandwidth: 20.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 2.0 GB MM§MData Used: 3.0 GBMM§MMM§MMy Note (class Cellular) Cost: $20.00MM§MBandwidth: 5.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 1.0 GBMM§MData Used: 0.75 GBMM§MMM§MMy Phone (class FiveG) Cost: $80.00MM§MBandwidth: 80.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 10.0 GB MM§MData Used: 12.0 GBMM§MMM§MMy Wifi (class WiFi) Cost: $45.00MM§MBandwidth: 450.0 MbpsMM§MMM§M———————————————-MM§MMonthly Wireless Network Report (by Bandwidth)MM§M———————————————-MM§MMy Note (class Cellular) Cost: $20.00MM§MBandwidth: 5.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 1.0 GBMM§MData Used: 0.75 GBMM§MMM§MMy iPad (class LTE) Cost: $38.00MM§MBandwidth: 20.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 2.0 GB MM§MData Used: 3.0 GBMM§MMM§MMy Phone (class FiveG) Cost: $80.00MM§MBandwidth: 80.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 10.0 GB MM§MData Used: 12.0 GBMM§MMM§MMy Wifi (class WiFi) Cost: $45.00MM§MBandwidth: 450.0 MbpsMM§MMM§M————————————————-MM§MMonthly Wireless Network Report (by Monthly Cost)MM§M————————————————-MM§MMy Phone (class FiveG) Cost: $80.00MM§MBandwidth: 80.0 MbpsMM§MTime: 1200.0 seconds</td>

  </tr>

  <tr>

   <td width="639">MM§MData Limit: 10.0 GB MM§MData Used: 12.0 GBMM§MMM§MMy Wifi (class WiFi) Cost: $45.00MM§MBandwidth: 450.0 MbpsMM§MMM§MMy iPad (class LTE) Cost: $38.00MM§MBandwidth: 20.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 2.0 GB MM§MData Used: 3.0 GBMM§MMM§MMy Note (class Cellular) Cost: $20.00MM§MBandwidth: 5.0 MbpsMM§MTime: 1200.0 secondsMM§MData Limit: 1.0 GBMM§MData Used: 0.75 GB MM§MMM§M———————-MM§MInvalid Records ReportMM§M———————-MM§MX,Bad Data,0,0,0,0,0,0,0MM§MInvalidCategoryException: For category: XMM§MMM§MW,My Other Wifi,450,40.0a,5.00MM§Mjava.lang.NumberFormatException: For input string: “40.0a”MM§MMM§MC,My Other Note,5.0,20.00,1200MM§Mjava.util.NoSuchElementException: For missing input data MM§MMM§MMM§M MM©M —-jGRASP: operation complete.¼¼MM</td>

  </tr>

 </tbody>

</table>










<h1>Notes</h1>

<ol>

 <li>This project assumes that you are reading each double value as a String using next() and then parsing it into a double with Double.parseDouble(…) as shown in the following example.     . . . Double.parseDouble(myInput.next());</li>

</ol>

This form of input will throw a <u>java.lang.NumberFormatException</u> if the value is not a double.




If you are reading in each double value as a double using nextDouble(), for example

. . . myInput.nextDouble(); then a <u>java.util.InputMismatchException</u> will be thrown if the value read in is not a double.




For this assignment, you should change your input to use Double.parseDouble(…) rather than nextDouble(), since Web-CAT is looking for <u>NumberFormatException</u> rather than  <u>java.util.InputMismatchException</u>.




<ol start="2">

 <li>If you are using the JUnit Assert.assertArrayEquals method to check two WirelessNetwork arrays for equality, then the equals and hashCode methods must be implemented in your WirelessNetwork class; that is, Assert.assertArrayEquals calls equals(Object obj) on each object in the array, so WirelessNetwork must have an equals method that overrides the one inherited from the Object class. If the WirelessNetwork class does not override equals(Object obj), then the JUnit Assert.assertArrayEquals method will use the inherited equals(Object obj) method which means two WirelessNetwork arrays will be equal only if they are the same object (i.e., aliases).</li>

</ol>




Below is a simplified equals method and hashCode method you are free to use.




public boolean equals(Object obj) {          if (!(obj instanceof WirelessNetwork)) {          return false;

}       else {

WirelessNetwork c = (WirelessNetwork) obj;                 return (name.equalsIgnoreCase(c.getName()));

}

}

public int hashCode() {       return 0;

}


