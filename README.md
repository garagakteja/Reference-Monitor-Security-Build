# Implement a Defensive Security System



Creation of a reference monitor(Security Mechanisms) using the security layer functionality in Repy V2. A reference monitor is an access control concept that refers to an abstract machine that mediates all access to objects by subjects. This can be used to allow, deny, or change the behavior of any set of calls. 


Building a security layer which keeps a backup copy of a file in case it is written incorrectly. In this project, a valid file will start with the character 'S' and end with the character 'E'. If any other characters (including lowercase 's', 'e', etc.) are the first or last characters, then the file is considered invalid.

Applications use ABopenfile() to create or open a file. Files are created by setting create=True when calling ABopenfile(), the reference monitor will create a new file 'SE' in filename.a and an empty file called filename.b. When close() is called on the file, if a file is not valid, it is discarded. If both files are valid, the older one is discarded.


The Reference Monitor does:

Not modify or disable any functionality of any RepyV2 API calls, such as:
Creating new files
Opening an existing file
Reading valid file using readat()
Writing to file using writeat(). This includes invalid writes, because 'S' and 'E' may later be written to the begining and end of the file respectively.
Check if the file starts with 'S' and ends with 'E', only when close() is called.
Normal operations will not be blocked or produce any output
Invalid operations will not produce any output to the user

The Reference Monitor would also:

Store two copies of the same file (filename.a and filename.b)
One is a valid backup, and the other is written to
When an app calls ABopenfile(), the method opens the A/B files, which you should name filename.a and filename.b.
When the app calls readat(), all reads must be performed on the valid file
When the app calls writeat(), all writes must be performed on the invalid file.
