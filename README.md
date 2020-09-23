<div align="center">

## WNetEnumResource


</div>

### Description

This API function can enumerate all network resources, including servers, workstations, printers, shares, remote directories etc. Unlike NetServerEnum function, this will enumerate DOS, Win3.1, Windows 95 and above, as well as NT 3.51 and higher, Win2k amd XP workstations.

The function is recursive, it works from top down. You can use this code in any way you like, hust keep the credit.

Tested on XP and NT 4.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Eugene Zhukovsky](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/eugene-zhukovsky.md)
**Level**          |Advanced
**User Rating**    |4.8 (24 globes from 5 users)
**Compatibility**  |C\#
**Category**       |[System Services/ Functions](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/system-services-functions__10-23.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/eugene-zhukovsky-wnetenumresource__10-741/archive/master.zip)





### Source Code

<HTML>
<HEAD>
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=windows-1252">
<META NAME="Generator" CONTENT="Microsoft Word 97">
<TITLE>//declare the DLL import functions [DllImport("netapi32</title>
</head>
<BODY>
<FONT FACE="Lucida Console" COLOR="#008000"><P>//Coded by Eugene E. Zhukovsky, 8.21.2002</p>
<P>//declare the DLL import functions</font><FONT FACE="Lucida Console"> </p>
<P>[DllImport("mpr.dll", CharSet=CharSet.Auto)]</p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff"><P>public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">static</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">extern</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">int</font><FONT FACE="Lucida Console"> WNetEnumResource(</p>
<P>IntPtr hEnum, </p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff"><P>ref</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">int</font><FONT FACE="Lucida Console"> lpcCount,</p>
<P>	IntPtr lpBuffer, </p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff"><P>ref</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">int</font><FONT FACE="Lucida Console"> lpBufferSize );</p>
<P>[DllImport("mpr.dll", CharSet=CharSet.Auto)]</p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff"><P>public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">static</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">extern</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">int</font><FONT FACE="Lucida Console"> WNetOpenEnum(</p>
<P>RESOURCE_SCOPE dwScope, </p>
<P>	RESOURCE_TYPE dwType,</p>
<P>	RESOURCE_USAGE dwUsage, </p>
<P>	[MarshalAs(UnmanagedType.AsAny)][In] Object lpNetResource, </p>
<P>	</font><FONT FACE="Lucida Console" COLOR="#0000ff">out</font><FONT FACE="Lucida Console"> IntPtr lphEnum);</p>
</font><FONT SIZE=2><P> </p>
</font><FONT FACE="Lucida Console"><P>[DllImport("mpr.dll", CharSet=CharSet.Auto)]</p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff"><P>public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">static</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">extern</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">int</font><FONT FACE="Lucida Console"> WNetCloseEnum( IntPtr hEnum );</p>
</font><FONT SIZE=2>
</font><FONT FACE="Lucida Console" COLOR="#008000"><P>//declare the structures to hold info</p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff">
<P>public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">enum</font><FONT FACE="Lucida Console"> RESOURCE_SCOPE</p>
<P>{</p>
<P>	RESOURCE_CONNECTED = 0x00000001,</p>
<P>	RESOURCE_GLOBALNET = 0x00000002,</p>
<P>	RESOURCE_REMEMBERED = 0x00000003,</p>
<P>	RESOURCE_RECENT  = 0x00000004,</p>
<P>	RESOURCE_CONTEXT  = 0x00000005</p>
<P>}</p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff"><P>public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">enum</font><FONT FACE="Lucida Console"> RESOURCE_TYPE</p>
<P>{</p>
<P>	RESOURCETYPE_ANY  = 0x00000000,</p>
<P>	RESOURCETYPE_DISK  = 0x00000001,</p>
<P>	RESOURCETYPE_PRINT = 0x00000002,</p>
<P>	RESOURCETYPE_RESERVED = 0x00000008,</p>
<P>}</p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff"><P>public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">enum</font><FONT FACE="Lucida Console"> RESOURCE_USAGE</p>
<P>{</p>
<P>	RESOURCEUSAGE_CONNECTABLE =0x00000001,</p>
<P>	RESOURCEUSAGE_CONTAINER  =0x00000002,</p>
<P>	RESOURCEUSAGE_NOLOCALDEVICE =0x00000004,</p>
<P>	RESOURCEUSAGE_SIBLING  =0x00000008,</p>
<P>	RESOURCEUSAGE_ATTACHED  =0x00000010,</p><DIR>
<DIR>
<P>	RESOURCEUSAGE_ALL   =(RESOURCEUSAGE_CONNECTABLE | RESOURCEUSAGE_CONTAINER | RESOURCEUSAGE_ATTACHED),</p></dir>
</dir>
<P>}</p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff"><P>public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">enum</font><FONT FACE="Lucida Console"> RESOURCE_DISPLAYTYPE</p>
<P>{</p>
<P>	RESOURCEDISPLAYTYPE_GENERIC  = 0x00000000,</p>
<P>	RESOURCEDISPLAYTYPE_DOMAIN  = 0x00000001,</p>
<P>	RESOURCEDISPLAYTYPE_SERVER  = 0x00000002,</p>
<P>	RESOURCEDISPLAYTYPE_SHARE  = 0x00000003,</p>
<P>	RESOURCEDISPLAYTYPE_FILE   = 0x00000004,</p>
<P>	RESOURCEDISPLAYTYPE_GROUP  = 0x00000005,</p>
<P>	RESOURCEDISPLAYTYPE_NETWORK  = 0x00000006,</p>
<P>	RESOURCEDISPLAYTYPE_ROOT   = 0x00000007,</p>
<P>	RESOURCEDISPLAYTYPE_SHAREADMIN = 0x00000008,</p>
<P>	RESOURCEDISPLAYTYPE_DIRECTORY = 0x00000009,</p>
<P>	RESOURCEDISPLAYTYPE_TREE   = 0x0000000A,</p>
<P>	RESOURCEDISPLAYTYPE_NDSCONTAINER = 0x0000000B</p>
<P>}</p>
</font><FONT SIZE=2>
</font><FONT FACE="Lucida Console" COLOR="#0000ff"><P>public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">struct</font><FONT FACE="Lucida Console"> NETRESOURCE</p>
<P>{</p>
<P>	</font><FONT FACE="Lucida Console" COLOR="#0000ff">public</font><FONT FACE="Lucida Console"> RESOURCE_SCOPE		dwScope;</p>
<P>	</font><FONT FACE="Lucida Console" COLOR="#0000ff">public</font><FONT FACE="Lucida Console"> RESOURCE_TYPE		dwType;</p>
<P>	</font><FONT FACE="Lucida Console" COLOR="#0000ff">public</font><FONT FACE="Lucida Console"> RESOURCE_DISPLAYTYPE	dwDisplayType;</p>
<P>	</font><FONT FACE="Lucida Console" COLOR="#0000ff">public</font><FONT FACE="Lucida Console"> RESOURCE_USAGE		dwUsage;</p>
<P>	[MarshalAs(System.Runtime.InteropServices.UnmanagedType.LPTStr)]	</font><FONT FACE="Lucida Console" COLOR="#0000ff">public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">string</font><FONT FACE="Lucida Console"> lpLocalName;</p>
<P>	[MarshalAs(System.Runtime.InteropServices.UnmanagedType.LPTStr)]	</font><FONT FACE="Lucida Console" COLOR="#0000ff">public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">string</font><FONT FACE="Lucida Console"> lpRemoteName;</p>
<P>	[MarshalAs(System.Runtime.InteropServices.UnmanagedType.LPTStr)]	</font><FONT FACE="Lucida Console" COLOR="#0000ff">public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">string</font><FONT FACE="Lucida Console"> lpComment;</p>
<P>	[MarshalAs(System.Runtime.InteropServices.UnmanagedType.LPTStr)]	</font><FONT FACE="Lucida Console" COLOR="#0000ff">public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">string</font><FONT FACE="Lucida Console"> lpProvider;</p>
<P>}</p>
</font><FONT SIZE=2>
</font><FONT FACE="Lucida Console" COLOR="#008000"><P>//the function we'll be calling</p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff"><P>public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">static</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">void</font><FONT FACE="Lucida Console"> WNETOE(Object o)</p>
<P>{</p>
<P>	</font><FONT FACE="Lucida Console" COLOR="#0000ff">int</font><FONT FACE="Lucida Console"> iRet;</p>
<P>	IntPtr ptrHandle = </font><FONT FACE="Lucida Console" COLOR="#0000ff">new</font><FONT FACE="Lucida Console"> IntPtr();</p>
<P>	</font><FONT FACE="Lucida Console" COLOR="#0000ff">try</p>
</font><FONT FACE="Lucida Console"><P>	{</p>
<P>				</p>
<P>		iRet =WNetOpenEnum( </p>
<P>			RESOURCE_SCOPE.RESOURCE_GLOBALNET, </p>
<P>			RESOURCE_TYPE.RESOURCETYPE_ANY,</p>
<P>			RESOURCE_USAGE.RESOURCEUSAGE_ALL, </p>
<P>			o, </p>
<P>			</font><FONT FACE="Lucida Console" COLOR="#0000ff">out</font><FONT FACE="Lucida Console"> ptrHandle );</p>
<P>		</font><FONT FACE="Lucida Console" COLOR="#0000ff">if</font><FONT FACE="Lucida Console">( iRet != 0 )</p>
<P>		{ </p>
<P>			</font><FONT FACE="Lucida Console" COLOR="#0000ff">return</font><FONT FACE="Lucida Console">; </p>
<P>		}</p>
<P>		</font><FONT FACE="Lucida Console" COLOR="#0000ff">int</font><FONT FACE="Lucida Console"> entries;</p>
<P>		</font><FONT FACE="Lucida Console" COLOR="#0000ff">int</font><FONT FACE="Lucida Console"> buffer = 16384;</p>
<P>		IntPtr ptrBuffer = Marshal.AllocHGlobal( buffer );</p>
<P>		NETRESOURCE nr;</p>
<P>		</font><FONT FACE="Lucida Console" COLOR="#0000ff">for</font><FONT FACE="Lucida Console">(;;)</p>
<P>		{</p>
<P>			entries = -1;</p>
<P>			buffer = 16384;</p>
<P>			iRet =WNetEnumResource( ptrHandle, </font><FONT FACE="Lucida Console" COLOR="#0000ff">ref</font><FONT FACE="Lucida Console"> entries, ptrBuffer, </font><FONT FACE="Lucida Console" COLOR="#0000ff">ref</font><FONT FACE="Lucida Console"> buffer );</p>
<P>			</font><FONT FACE="Lucida Console" COLOR="#0000ff">if</font><FONT FACE="Lucida Console">( (iRet != 0) || (entries < 1) )</p>
<P>			{</p>
<P>				</font><FONT FACE="Lucida Console" COLOR="#0000ff">break</font><FONT FACE="Lucida Console">;</p>
<P>			}</p>
<P>			Int32 ptr = ptrBuffer.ToInt32();</p>
<P>			</font><FONT FACE="Lucida Console" COLOR="#0000ff">for</font><FONT FACE="Lucida Console">( </font><FONT FACE="Lucida Console" COLOR="#0000ff">int</font><FONT FACE="Lucida Console"> i = 0; i < entries; i++ )</p>
<P>			{</p>
<P>				nr = (NETRESOURCE)Marshal.PtrToStructure( </font><FONT FACE="Lucida Console" COLOR="#0000ff">new</font><FONT FACE="Lucida Console"> IntPtr(ptr), </font><FONT FACE="Lucida Console" COLOR="#0000ff">typeof</font><FONT FACE="Lucida Console">(NETRESOURCE) );</p>
<P>											</font><FONT FACE="Lucida Console" COLOR="#0000ff">if</font><FONT FACE="Lucida Console">(RESOURCE_USAGE.RESOURCEUSAGE_CONTAINER == (nr.dwUsage</p>
<P>							& RESOURCE_USAGE.RESOURCEUSAGE_CONTAINER))</p>
<P>			{</p>
</font><FONT FACE="Lucida Console" COLOR="#008000"><P>//call recursively to get all entries in a container</p>
</font><FONT FACE="Lucida Console"><P>				WNETOE(nr);</p>
<P>			}</p>
<P>				ptr += Marshal.SizeOf( nr );</p>
<P>Console.WriteLine( " {0} : LocalName='{1}' RemoteName='{2}'",</p>
<P>nr.dwDisplayType.ToString(), nr.lpLocalName, nr.lpRemoteName );</p>
<P>				}</p>
<P>		}</p>
<P>		Marshal.FreeHGlobal( ptrBuffer );</p>
<P>		iRet =WNetCloseEnum( ptrHandle );</p>
<P>	}</p>
<P>	</font><FONT FACE="Lucida Console" COLOR="#0000ff">catch</font><FONT FACE="Lucida Console">(Exception e)</p>
<P>	{</p>
<P>	}</p>
<P>}</p>
</font><FONT FACE="Lucida Console" COLOR="#008000">
<P>//now call the function passing a null</p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff">
</font><FONT FACE="Lucida Console"><P>WNETOE(null);</p>
</font><FONT SIZE=2>
</font><FONT FACE="Lucida Console" COLOR="#008000"><P>//here's some possible error codes</p>
</font><FONT FACE="Lucida Console" COLOR="#0000ff">
<P>public</font><FONT FACE="Lucida Console"> </font><FONT FACE="Lucida Console" COLOR="#0000ff">enum</font><FONT FACE="Lucida Console"> NERR</p>
<P>{</p>
<P>	NERR_Success	= 0,  </font><FONT FACE="Lucida Console" COLOR="#008000">/* Success */</p>
</font><FONT FACE="Lucida Console"><P>	ERROR_MORE_DATA = 234, </font><FONT FACE="Lucida Console" COLOR="#008000">// dderror</p>
</font><FONT FACE="Lucida Console"><P>	ERROR_NO_BROWSER_SERVERS_FOUND = 6118,</p>
<P>	ERROR_INVALID_LEVEL	= 124,</p>
<P>	ERROR_ACCESS_DENIED	= 5,</p>
<P>	ERROR_INVALID_PARAMETER	= 87,</p>
<P>	ERROR_NOT_ENOUGH_MEMORY	= 8,</p>
<P>	ERROR_NETWORK_BUSY	= 54,</p>
<P>	ERROR_BAD_NETPATH	= 53,</p>
<P>	ERROR_NO_NETWORK = 1222,</p>
<P>	ERROR_INVALID_HANDLE_STATE = 1609,</p>
<P>	ERROR_EXTENDED_ERROR  = 1208</p>
<P>}</p></font></body>
</html>

