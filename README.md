Download Link: https://assignmentchef.com/product/solved-cs39006-assignment5-simple-communication-using-datagram-socket-using-posix-c
<br>
The objective of this assignment is to get familiar with datagram sockets using POSIX C programming. The target is to establish a communication between two computers (processes) using a datagram socket. A datagram socket uses a simple communication paradigm to transfer short messages between two computers (processes) without ensuring any reliability.

<strong>Problem Statement: </strong><strong> </strong>

Your task will be to write two programs – one program corresponding to the server process and another program corresponding to the client process. The client process requests for the content of a file (by providing the file name) and the server process sends the contents of that file to the client.

For simplicity, we assume that the file is a simple text file that contains a set of words, with the first word being HELLO and the last word being END. We assume that HELLO and END are two special keywords that do not come anywhere except at the first line (HELLO) and the last line (END). The content of a sample file looks as follows.

HELLO

CAT DOG

TIGER

LION

HORSE ZEBRA COW

END




The transfer of the contents of the file works using a communication protocol as follows.

<ol>

 <li>The client first sends the file name to the server.</li>

 <li>The server looks for the file in the local directory, if the file is not there it sends back with a message FILE_NOT_FOUND. By receiving this message, the client prints an error message “File Not Found” and exits.</li>

 <li>If the file is present, the server reads the first line of the file, which contains HELLO, and sends this message to the client. If the first line of the file is not HELLO, it prints an error “Wrong File Format” and exits after sending a message WRONG_FILE_FORMAT to the client. When the client receives this message, it prints “Wrong File Format” and exits.</li>

 <li>After receiving HELLO, the client creates a local file (a different file name from the requested one) and sends a message WORD_1 to the server. This message indicates that the client is requesting the first word.</li>

 <li>After receiving the message WORD1, the server sends the first word (after HELLO) to the client. The client writes this word to the local file after receiving it and sends the message WORD2 to request the next word. This procedure continues for each word.</li>

 <li>On receiving WORDi, the server sends the i-th word to the client. This process continues until the client receives the keyword END.</li>

 <li>Once the client receives the keyword END, it closes the local file after writing the last word to the file.</li>

</ol>





