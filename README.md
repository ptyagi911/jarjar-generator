jarjar-generator
================

Generating custom jar to support using Hex.encodeHexString method from commons-codec-1.6.jar in Android

Step-1: Create a build.xml like follows:
<project name="generate-jarjar">
    <property name="jarjarfile" value="commons-codec-1.6-jarjar.jar"/>
    <path id="classpath">
      <pathelement location="jarjar-1.4.jar"/>
      <pathelement location="asm-2.2.3.jar"/>
    </path>
    <taskdef name="jarjar" classname="com.tonicsystems.jarjar.JarJarTask"   classpathref="classpath"/>
    <delete file="${jarjarfile}"/>
    <jarjar destfile="${jarjarfile}">
    <zipfileset src="commons-codec-1.6.jar"/>
    <rule pattern="org.apache.**" result="org.jarjar.apache.@1"/>
    </jarjar>
</project>
Step-2: Run command "ant" from command line. This build script will generate a new jar  commons-codec-1.6-jarjar.jar, which you can add in your build path and use this new jar to import from.

You can download all the files mentioned in above script and build.xml from here.
