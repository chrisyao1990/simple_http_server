simple_http_server
==================
<pre>
This is an team course project in course CS631 Advanced Programming in the UNIX Environment

We using the git tools in our linux lab for collaborate developing.

The Project requirment is as follow: (You can also found it in http://www.cs.stevens.edu/~jschauma/631A/f13-final-project.html)

Summary

The objective of this assignment is for you to write a simple web server that speaks a limited version of HTTP/1.0 as defined in RFC1945. This gives you occasion to understand the process of reading an RFC and implementing a well-known protocol.

You will implement the sws(1) command as described in the manual page provided to you here.

NAME
  sws —asimple web server
SYNOPSIS
  sws [ −dh] [ −c dir] [ −i address] [ −l file] [ −p port] dir
DESCRIPTION
  sws is a very simple web server. It behaves quite like you would expect from any regular web server, in that it 
  binds to a given port on the given address and waits for incoming HTTP/1.0 requests. It serves content from the 
  given directory.That is, any requests for documents is resolved relative to this directory (the document root).

OPTIONS
  The following options are supported by sws:
    −c dir Allow execution of CGIs from the given directory. See CGIs for details.
    −d Enter debugging mode. That is, do not daemonize, only accept one connection at a time and enable logging 
      to stdout.
    −h Print a short usage summary and exit.
    −i address Bind to the given IPv4 or IPv6 address. If not provided, sws will listen on all IPv4 and IPv6 
      addresses on this host.
    −l file Log all requests to the given ﬁle. See LOGGING for details.
    −p port Listen on the given port. If not provided, sws will listen on port 8080.
DETAILS
    sws speaks a crippled dialect of HTTP/1.0: it responds to GET and HEAD requests according to RFC1945,
    but may not support POST requests and only supports the If-Modiﬁed-Since Request-Header.
    When a connection is made, sws will respond with the appropriate HTTP/1.0 status code and the following
    headers:
        Date The current timestamp in GMT.
        Server A string identifying this server and version.
        Last-Modiﬁed The timestamp in GMT of the ﬁle’s last modiﬁcation date.
        Content-Type text/html or, optionally, the correct content-type for the ﬁle in question as 
            determined via magic(5) patterns
        Content-Length The size in bytes of the data returned.
        If the request type was a GET, then it will subsequently return the data of the requested ﬁle. After serving
        the request, the connection is terminated.
FEATURES
    sws supports a number of interesting features:
    CGIs                  Execution of CGIs as described in CGIs.
    Directory Indexing    If the request was for a directory and the directory does not contain a ﬁle named
                          "index.html", then sws will generate a directory index, listing the contents of the 
                          directory in alphanumeric order. Files starting with a "." are ignored.
    User Directories      If the request begins with a "˜", then the following string up to the ﬁrst slash 
                          is translated into that user’s sws directory (ie /home/<user>/sws/)
CGIs
    If a URI begins with the string "/cgi-bin", and the −c ﬂag was speciﬁed, then the remainder of the resource
    path will be resolved relative to the directory speciﬁed using this ﬂag. The resulting ﬁle will then be
    executed and any output generated is returned instead. Execution of CGIs follows the speciﬁcation in
    RFC3875.

LOGGING
    Per default, sws does not do any logging. If explicitly enabled via the −l ﬂag, sws will log every request
    in a slight variation of Apache’s so-called "common" format: ’%a %t "%r" %>s %b’. That is, it will log:
    %a  The remote IP address.
    %t  The time the request was received (in GMT).
    %r  The (quoted) ﬁrst line of the request.
    %>s The status of the request.
    %b  Size of the response in bytes. Ie, "Content-Length".
    All lines will be appended to the given ﬁle unless −d was giv en, in which case all lines will be printed 
      to stdout.
EXIT STATUS
    The sws utility exits 0 on success, and >0 if an error occurs.
SEE ALSO
    RFC1945
HISTORY
    A simple http server has been a frequent ﬁnal project assignment for the class Advanced Programming
    in the UNIX Environment at Stevens Institute of Technology. This variation was ﬁrst assigned in the
    Fall 2008 by Jan Schaumann.

</pre>
  

