# ShellShock

<!-- wp:paragraph -->
<p><strong>ShellShock </strong>es una vulnerabilidad salida a la luz el año 2004, reconocida mediante el identificador <strong>CVE-2014-6271</strong>. El error se produce en bash, a la hora de crear funciones, y guardarlas en variables de entornos. </p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>La forma de explotarlo reside en poner caracteres antes de la lectura de la variable, bash lo interpretará como un comando, por lo que podremos ejecutar de forma remota los comandos (<strong>RCE</strong>).</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Si encontramos en alguna CTF el directorio <strong><em>cgi-bin</em></strong>, sería un gran indicio de que almacenamos scripts vulnerables a este método de explotación.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Código de ejemplo: </p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code -->
<pre class="wp-block-syntaxhighlighter-code">curl -H "user-agent: () { :; }; echo; echo; /bin/bash -c 'cat /etc/passwd'" \
http:&#47;&#47;localhost:8080/cgi-bin/vulnerable</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>La linea vendría a significar que usaremos el encabezado del navegador como variable de entorno, tras esto haríamos un <strong>cat </strong>a<strong> /etc/passwd </strong>(En este punto, es donde podríamos colocar el comando a desear, desde un simple id a una reverse shell) y el host atacado.  </p>
<!-- /wp:paragraph -->
