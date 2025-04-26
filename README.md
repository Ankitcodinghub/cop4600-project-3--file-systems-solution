# cop4600-project-3--file-systems-solution
**TO GET THIS SOLUTION VISIT:** [COP4600 Project 3- File Systems Solution](https://www.ankitcodinghub.com/product/cop4600-p3-file-systems-solution/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;120780&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;COP4600 Project 3- File Systems Solution&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
<span style="font-size: 2.61792em; letter-spacing: -1px;">Overview</span>

Your cover in the Lizard Legion was blown, and you’ve been revealed as a double agent and driven out! It was all very “James Bond”, if you do say so yourself, and what a daring underground helicopter escape it was… but you feel lucky to have escaped with your skin. (Literally… they would have used you to make a “human suit”!) Now that you’re back on the “outside”, you’ve been tasked with creating a scheme to allow remaining resistance fighters still within the Lizard Legion to clandestinely move information back to your organization without raising suspicion. As of late, members of the Lizard Legion have discovered the PC classic “DOOM”, and it has become all the rage to build new mods for it at headquarters, so your team has decided to use mods for this title as a vehicle for exfiltration. By burying encrypted bits within textures and other game data blocks, information can be hidden within innocuous “WAD” (Where’s All the Data) files.

In this project, you will implement a userspace filesystem daemon using the FUSE (Filesystem in UserSpacE) API to access data in WAD format, the standard used in a number of classic PC game titles (including DOOM and Hexen). In this critical early prototype, you have been tasked with implementing read and write access to files and directories within the WAD files as a proof-of-concept. As such, you will need to implement read and write functionality for both files and directories within your FUSE-based program. We, as your comrades-inarms battling the Reptilian invasion, will provide sample WAD files to demonstrate the functionality of your implementation. (The resistance is counting on you!) The resistance uses university courses as cover for standard operations, so you’ll submit the project via Canvas.

<h1>Structure</h1>
The project is broken into three main parts:

<ul>
<li>Develop a library to read from and write to WAD files and create a directory and file structure from them.</li>
<li>Implement a userspace daemon (via FUSE) to access the directory structure once mounted.</li>
<li>Test your implementation by navigating the mounted directory, examining the names and file contents, and adding directories and files of your own.</li>
</ul>
While exact implementation may vary, the daemon’s parameters must match those laid out in this document, and the directory structure, naming, and file contents must be properly presented via the filesystem.

<h2>File Format</h2>
The WAD file format contains information in three sections: the header, which gives basic layout information, the descriptors, which describe elements in the file, and the lumps, which contain the data themselves. NOTE: all numbers are in <u>little-Endian</u> format and, where applicable, are designated in <u>bytes</u>! Since Reptilian stores its variables in memory in little-Endian format as well, it is not necessary to perform any byte-order inversions when reading in or writing data, but this is still important information to know.

<u>File Header</u>

The header contains the file magic, descriptor count, and location (offset) of the descriptors in the file:

The magic for a wad file is usually ASCII and always ends in the suffix “WAD” (e.g., “IWAD” or “PWAD”). It is also important to note that the descriptor list, beginning at the position indicated by the descriptor offset, is always situated at the end of the WAD file.

<u>Descriptors</u>

The file’s descriptors contain information about elements in the WAD file – its file offset, length, and name:

Some elements will have specific naming conventions that will differentiate them from regular content files. These “marker” elements will be interpreted by the daemon as directories and should be displayed accordingly in the filesystem (see below).

<u>Lumps</u>

Elements in the WAD format are stored as “lumps” described by the descriptors. These lumps will be represented in the filesystem by the daemon as individual files that can be opened, read, and closed. You cannot write to existing lumps, but you will be creating empty files whose lumps you will have to write to.

<u>Marker Elements</u>

There are two primary types of marker elements in WAD files, each of which should be interpreted as directories by our daemon. The type includes <u>map markers</u> and <u>namespace markers</u>.

Map marker names are of the format “E#M#”, where # represents a single decimal digit (e.g., “E1M9”). They are followed by ten (10) map element descriptors. The elements for the next 10 descriptors <u>should be</u> <u>placed inside of a directory</u> with the map’s name. Map marker directories cannot have files or directories added to them.

Namespace markers <u>come in pairs</u>. A namespace’s beginning is marked with a descriptor whose name has the suffix “_START” (e.g., “F1_START”), and its ending is marked with a descriptor whose name has the suffix “_END” (e.g., “F1_END”). Any descriptors for elements falling between the beginning and ending markers for a namespace should be placed within a directory with the namespace’s name (e.g., “F1”). The namespace marker’s name, excluding the suffixes, will never exceed two characters. These will be the kind of directories you will be responsible for creating.

As an example, the following descriptors, in order, in the descriptor list, should result in this organization:

<table width="551">
<tbody>
<tr>
<td width="78">Offset</td>
<td width="72">Length</td>
<td width="90">Name</td>
<td rowspan="17" width="88"></td>
<td rowspan="2" width="224">Directory Structure</td>
</tr>
<tr>
<td width="78">0</td>
<td width="72">0</td>
<td width="90">F_START</td>
</tr>
<tr>
<td width="78">0</td>
<td width="72">0</td>
<td width="90">F1_START</td>
<td rowspan="15" width="224"></td>
</tr>
<tr>
<td width="78">67500</td>
<td width="72">0</td>
<td width="90">E1M1</td>
</tr>
<tr>
<td width="78">67500</td>
<td width="72">1380</td>
<td width="90">THINGS</td>
</tr>
<tr>
<td width="78">68880</td>
<td width="72">6650</td>
<td width="90">LINEDEFS</td>
</tr>
<tr>
<td width="78">75532</td>
<td width="72">19440</td>
<td width="90">SIDEDEFS</td>
</tr>
<tr>
<td width="78">94972</td>
<td width="72">1868</td>
<td width="90">VERTEXES</td>
</tr>
<tr>
<td width="78">96840</td>
<td width="72">8784</td>
<td width="90">SEGS</td>
</tr>
<tr>
<td width="78">105624</td>
<td width="72">948</td>
<td width="90">SSECTORS</td>
</tr>
<tr>
<td width="78">106572</td>
<td width="72">6608</td>
<td width="90">NODES</td>
</tr>
<tr>
<td width="78">113180</td>
<td width="72">2210</td>
<td width="90">SECTORS</td>
</tr>
<tr>
<td width="78">115392</td>
<td width="72">904</td>
<td width="90">REJECT</td>
</tr>
<tr>
<td width="78">116296</td>
<td width="72">6922</td>
<td width="90">BLOCKMAP</td>
</tr>
<tr>
<td width="78">42</td>
<td width="72">9001</td>
<td width="90">LOLWUT</td>
</tr>
<tr>
<td width="78">0</td>
<td width="72">0</td>
<td width="90">F1_END</td>
</tr>
<tr>
<td width="78">0</td>
<td width="72">0</td>
<td width="90">F_END</td>
</tr>
</tbody>
</table>
<h2>Library</h2>
Your library will contain a class to represent WAD data as described in this section.

<u>Wad Class</u>

The Wad class is used to represent WAD data and should have the following functions. The root of all paths in the WAD data should be “/”, and each directory should be separated by ‘/’ (e.g., “/F/F1/LOLWUT”).

public static Wad* loadWad(const string &amp;path)

Object allocator; <u>dynamically</u> creates a Wad object and loads the WAD file data from path into memory. <u>Caller</u> must deallocate the memory using the delete keyword.

public string getMagic()

Returns the magic for this WAD data.

public bool isContent(const string &amp;path)

Returns true if path represents content (data), and false otherwise.

public bool isDirectory(const string &amp;path)

Returns true if path represents a directory, and false otherwise.

public int getSize(const string &amp;path)

If path represents content, returns the number of bytes in its data; otherwise, returns -1.

public int getContents(const string &amp;path, char *buffer, int length, int offset = 0)

If path represents content, copies as many bytes as are available, up to length, of content’s data into the preexisting buffer. If offset is provided, data should be copied starting from that byte in the content. Returns number of bytes copied into buffer, or -1 if path does not represent content (e.g., if it represents a directory).

public int getDirectory(const string &amp;path, vector&lt;string&gt; *directory)

If path represents a directory, places entries for immediately contained elements in directory. The elements should be placed in the directory in the same order as they are found in the WAD file. Returns the number of elements in the directory, or -1 if path does not represent a directory (e.g., if it represents content).

public <em>void</em> <strong>createDirectory</strong>(const string &amp;path)

<strong>path</strong> includes the name of the new directory to be created. If given a valid <strong>path</strong>, creates a new directory using namespace markers at <strong>path</strong>. The two new namespace markers will be added just before the “_END” marker of its parent directory. New directories cannot be created inside map markers.

public <em>void</em> <strong>createFile</strong>(const string &amp;path)

<strong>path</strong> includes the name of the new file to be created. If given a valid <strong>path</strong>, creates an empty file at <strong>path</strong>, with an offset and length of 0. The file will be added to the descriptor list just before the “_END” marker of its parent directory. New files cannot be created inside map markers.

public int <strong>writeToFile</strong>(const string &amp;path, const char *buffer, int length, int offset = 0)

If given a valid <strong>path</strong> to an empty file, augments file size and generates a lump offset, then writes <strong>length</strong> amount of bytes from the <strong>buffer</strong> into the file’s lump data. If <strong>offset</strong> is provided, data should be written starting from that byte in the lump content. Returns number of bytes copied from <strong>buffer</strong>, or -1 if <strong>path</strong> does not represent content (e.g., if it represents a directory).

<strong>NOTE:</strong> If a file or directory is created inside the root directory, it will be placed at the very end of the descriptor list, instead of before an “_END” namespace marker.

<h2>Daemon Command &amp; Parameters</h2>
Your daemon should have name wadfs and should accept at a minimum three parameters – the single-threaded flag “-s”, the target WAD file, and the mount directory. For example, this command should mount TINY.WAD in /home/reptilian/mountdir…

$ ./wadfs <strong>-s</strong> TINY.WAD /home/reptilian/mountdir $

…and this should result from executing the ls command to show part of its contents:

$ ls /home/reptilian/mountdir/F/F1 -al total 0 dr<strong>w</strong>xr<strong>w</strong>xr<strong>w</strong>x. 2 root root&nbsp; 0 Jan&nbsp; 1&nbsp; 1970 . dr<strong>w</strong>xr<strong>w</strong>xr<strong>w</strong>x. 2 root root&nbsp; 0 Jan&nbsp; 1&nbsp; 1970 .. dr<strong>w</strong>xr<strong>w</strong>xr<strong>w</strong>x. 2 root root&nbsp; 0 Jan&nbsp; 1&nbsp; 1970 E1M1

-r<strong>wx</strong>r<strong>wx</strong>r<strong>wx</strong>. 2 root root 9001 Jan&nbsp; 1&nbsp; 1970 LOLWUT

We will use the following command below to unmount your filesystem:

$ <strong>fusermount -u /home/reptilian/mountdir</strong>

Your daemon should <u>run in the background</u>. Do not hard-code the debug (-d) or foreground (-<strong>f) </strong>flags!

<h2><strong>Extra Credit</strong></h2>
You may notice when testing with your daemon that there is an upper limit to how large files you create in your filesystem can be. Your task is to configure your library and daemon such that you are able to create large files in your filesystem (using “cp” to copy in a 200KB image file, for example). Running your daemon in debug mode (<strong>-d</strong>) may give you hints as to how certain calls are expected to behave.

<h3>File and Directory Requirements</h3>
Your daemon must implement, at a minimum, the following filesystem functions to provide read and write access:

<ul>
<li>Retrieving file and directory attributes</li>
<li>Reading from existing files, and writing to new ones</li>
<li>Reading from existing directories, and writing to new ones</li>
</ul>
Files and directories should be given full read, write, and execute permissions.

The above requirements will be achieved using, at a minimum, the following six fuse callback functions:

<h4>get_attr, mknod, mkdir, read, write, and readdir</h4>
It is highly recommended to closely follow the linked resources at the bottom of this pdf to assist with your FUSE implementation. All changes to the filesystem, such as directory and file creation, must survive between mounting and unmounting.

<h1>Building with FUSE</h1>
FUSE is a userspace filesystem API that is supported directly by the Linux kernel. It allows userspace programs to provide information to the kernel about filesystems the kernel cannot interpret on its own.

<h2>Installation &amp; Setup</h2>
To use the FUSE library, you will need to install it within Reptilian and change the FUSE permissions:

$ sudo apt install libfuse-dev<strong> fuse</strong>

$ sudo chmod<strong> 666</strong> /dev/fuse

NOTE: if you reboot the virtual machine, you will need to re-add the FUSE permissions, as they will be reset!

<h2>Build Directives</h2>
In order to build programs using the FUSE library system, you will need to specify the file offset bits as 64 and identify the FUSE version. We recommend specifying FUSE version 26 (though this is optional):

$ g++ -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=26 myproggy.cpp -o myproggy -lfuse

<h1>Submissions</h1>
You will submit the following at the end of this project:

 Report (p3.txt) in man page format on Canvas, including link to <u>unlisted</u> screencast video  Compressed tar archive (wad.tar.gz) for libWad library and wadfs daemon on Canvas

<h2>Report</h2>
Your report will explain how you implemented the daemon, including your general architecture / program structure. It must include an explanation of how you represent the WAD file elements as a directory structure in memory, as well as how this structure was utilized in the daemon when running. It will include a description of how testing was performed along with any known bugs. The report should be no more than 600 words, cover all relevant aspects of the project, and be organized and formatted professionally – this is not a memo!

<h2>Screencast</h2>
In addition to the written text report, you should submit a screencast (with audio) walking through your library and the daemon you wrote to provide the filesystem interface, describing your primary functions and structures (~5:30).

<h2>Compressed Archive (wad.tar.gz)</h2>
Your compressed tar file should have the following directory/file structure:

To build the library and daemon, we will execute these commands:

$ tar zxvf wad.tar.gz

$ cd libWad

$ make $ cd ..

$ cd wadfs

$ make

$ cd ..

To run your daemon, we will execute this command:

$ ./wadfs/wadfs <strong>-s </strong>somewadfile.wad /some/mount/directory

To build another program using your library, we will execute this command:

$ c++ -o program_name sourcefile.cpp -L ./libWad -lWad

<h1>Helpful Links</h1>
You may find the following resources helpful when reading about how to implement a FUSE daemon:

<u>https://www.cs.nmsu.edu/~pfeiffer/fuse-tutorial/html/</u> <u>https://engineering.facile.it/blog/eng/write-filesystem-fuse/ https://maastaar.net/fuse/linux/filesystem/c/2019/09/28/writing-less-simple-yet-stupid-filesystem-using-FUSE-in-C/ https://www.cs.hmc.edu/~geoff/classes/hmc.cs137.201601/homework/fuse/fuse_doc.html http://slade.mancubus.net/index.php?page=about</u>
