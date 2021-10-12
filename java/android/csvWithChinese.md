# CSV with Chinese

> **Lien Chen** *2021-10-12*

* When we write file with utf-8 charset, the chinese words will be garbled. It seems that excel default to use BIG5 read file.
* Here is easy code to write file with charset BIG5

```java=
StringBuilder output = new StringBuilder();
Files.write(tempFile, new String(output.toString().getBytes(StandardCharsets.UTF_8)).getBytes(Charset.forName("big5")));
```

First we need to set the string charset to utf-8, then youcan change its to big5.
