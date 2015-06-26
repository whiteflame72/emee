How to start
------------

1. Open the following two files and understand the structure of the XML:

application/xml/section.xml
application/xml/content.xml

2. Generate your own data (either dynamically via a web server/application server or just static xml, replacing the above mentioned xml files in the same directory)

3. Replace the following codes accordingly inside ts.lzx:

	<dataset name="ds10" request="true" type="http" src="application/xml/section.xml"/>
	<dataset name="ds30" request="true" type="http" src="application/xml/content.xml"/>

4. Access the Extreme Media Explorer via an URL like
http://localhost:8080/lps-4.9.0/media/ts.lzx?debug=false

Note: The URL is subjective to the version of LZX and the port configured.

5. To implement your application which will extend this framework, add your components by editing the following files:

library/external.lzx

A sample acmeapp.lzx is provided, showing one how to listen to the changes made by EMEE component.

Users of EMEE should not have to modify anything other than the file external.lzx under the library directory and any application specific component(s) under the directory application. EMEE will not be guaranteed to work if its libraries are changed directly by the user and if such a need arise, it is the designer's oversight.
 
Dependencies
------------
Media explorer depends on the following library :

LAVA 3 (for String justification and formatting)
lava3-printf.jar from http://www.sharkysoft.com/software/java/lava3/printf/download/ for String utility class etc.

lava3-core.jar from 
http://www.sharkysoft.com/software/java/lava3/core/download/, it is the lava3-printf.jar dependent jar file.

GROOVY (optional; to demonstrate alternative backend besides JSP)
To sett up groovylets, put the following in your web.xml :

<servlet>
<servlet-name>Groovy</servlet-name>
<servlet-class>groovy.servlet.GroovyServlet</servlet-class>
</servlet>

<servlet-mapping>
<servlet-name>Groovy</servlet-name>
<url-pattern>*.groovy</url-pattern>
</servlet-mapping>

Then all the following jar files -
groovy-1.0.jar
antlr-2.7.5.jar
asm-2.2.jar

into WEB-INF/lib.

Then access it at 
http://localhost:8080/lps-4.9.0/media/application/groovlet/hello.groovy

One should see something like the following :

Hello, 127.0.0.1: 1! Sun Mar 04 11:06:02 EST 2007

And lastly and obviously, OpenLaslo server available at http://www.openlaszlo.org/download.