Google RPC Compatibility checker
--------------------------

jar for https://github.com/googleapis/google-cloud-java/tree/master/google-cloud-util/google-cloud-compat-checker

create artifact
--

```bash
mvn clean compile assembly:single
```

run compatibility checker
----

```
$ java -jar target/google-cloud-compat-checker-0.79.1-alpha-SNAPSHOT-jar-with-dependencies.jar 
============================================
OS details:
  os.detected.name: osx
  os.detected.arch: x86_64
  os.detected.classifier: osx-x86_64
  os.detected.release: null
  os.detected.release.version: null
JVM details:
  Java version: 1.8.0_151
  Java specification version: 1.8
  JVM bit mode: 64
OpenSSL details:
  open ssl is available: false
  ALPN is supported: false
============================================
Checking compatibility...
  [PASS] This OS + architecture is supported.
  [PASS] 64-bit JVM is supported.
  [FAIL] Open SSL is NOT available
         Open SSL Unavailability cause:
java.lang.IllegalArgumentException: Failed to load any of the given libraries: [netty-tcnative-osx-x86_64, netty-tcnative]
	at io.netty.util.internal.NativeLibraryLoader.loadFirstAvailable(NativeLibraryLoader.java:178)
	at io.netty.handler.ssl.OpenSsl.loadTcNative(OpenSsl.java:403)
	at io.netty.handler.ssl.OpenSsl.<clinit>(OpenSsl.java:85)
	at com.google.cloud.compatchecker.GoogleCloudCompatChecker.check(GoogleCloudCompatChecker.java:58)
	at com.google.cloud.compatchecker.Application.main(Application.java:6)
  [FAIL] Open SSL ALPN is NOT supported
Result: FAIL
  Your environment is not supported by Forked Tomcat Native.
  See http://netty.io/wiki/forked-tomcat-native.html for details.
  This means that you won't be able to use grpc-based APIs, but
  http1-based APIs should still work.
```