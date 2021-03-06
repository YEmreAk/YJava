---
description: JavaFX ile javada görsel arayüze sahip uygulama yapımı
---

# 🌃 GUI Tasarımı \| JavaFX

## 📢 Önemli Bilgi

* JavaFX artık JDK 12'nın bir parçası değildir, [buradan](https://stackoverflow.com/a/53463455/9770490) gerekli bilgilere erişebilirsin.
* Java SDK 8 ile depoy edebilmektesin
  * Deploy etme hususunda bilgi almak için [buraya](https://www.youtube.com/watch?v=iR85RRep-Po&t=299s) bakabilirsin

## 👷‍♂️ IntelliJ için JavaFx Kurulumu

JavaFX ve JFhoenix Material UI'ı kurulumunu anlatan videom için [buraya](https://www.youtube.com/watch?v=1uDuWfPPL6s) bakabilrisin 💁‍♂️

* İlk olarak [IntelliJ](https://www.jetbrains.com/idea/download/#section=windows)'yi indirin
* Resmi sitesinden [JavaFX SDK](https://gluonhq.com/products/javafx/)'sını indirin
* İndirdiğiniz arşivdeki çıkartın
* Arşivdeki `javafx-sdk-12.0.1` dosyasını `C:\Program Files\Java` dizinine taşıyın
* GUI düzenleme aracı olan [Scene Builder](https://gluonhq.com/products/scene-builder/)'ı indirin
* IntelliJ üzerinden `File` - `Settings` - `Languages & Frameworks` - `JavaFx` kısmına [Scene Builder](https://gluonhq.com/products/scene-builder/)'ın yolunu yazın.
  * Örn: _C:\Program Files\SceneBuilder\SceneBuilder.exe_
* IntelliJ üzerinden `File` - `New` - `Project` - `JavaFX` - `Next` - `Finish` ile projenizi oluşturun
* Son olarak `File` - `Project Structure` - `Modules`
* Açılan ekranda `+` - `Library` - `Java`
* Çıkan ekran ile `C:\Program Files\Java\javafx-sdk-12.0.1\lib` kütüphanesini ekleyin
* `Run` - `Edit Configurations`
* Çıkan ekranda `VM Opitons` alanına alttaki metni kopyalayın:
  * `--module-path "C:\Program Files\Java\javafx-sdk-12.0.1\lib" --add-modules=javafx.controls,javafx.fxml`
* Artık `.fxml` uzantılı dosyalarda ekranın sol alt köşesinden `Scene Builder`'a tıklayarak GUI programlamaya başlayabilirsiniz ✨

> Not sizin sürümünüz ve yolunuz farklı ise ona göre ayalayın `<yol>\javafx-sdk-<version>\lib`

### 🍱 Maven ile Modüler JavaFX Kurulumu

Anlatıcı video için [buraya](https://www.youtube.com/watch?v=Ri6No63fl-A) bakabilrisin

### 📃 pom.xml içeriği

Maven xml verilerini, `pom.xml` dosyasında geösterilen alana yapıştırın.

* **TODO** alanlarını düzenlemeyi unutmayın

```markup
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.yemreak</groupId> <!-- TODO: Kodların bulunduğu ana package ismi-->
    <artifactId>ytoolsfx</artifactId> <!-- TODO: Modül ismi -->
    <version>1.0.0</version>  <!-- TODO: Sürüm numarası -->

   <!-- Buraya yapıştırılacak -->

</project>
```

```markup
<properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>12</maven.compiler.source>
    <maven.compiler.target>12</maven.compiler.target>
</properties>
<dependencies>
    <dependency>
        <groupId>org.openjfx</groupId>
        <artifactId>javafx-controls</artifactId>
        <version>12</version>
    </dependency>
    <dependency>
        <groupId>org.openjfx</groupId>
        <artifactId>javafx-fxml</artifactId>
        <version>12</version>
    </dependency>
</dependencies>
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.8.0</version>
            <configuration>
                <release>12</release>
                <source>8</source>
                <target>8</target>
            </configuration>
        </plugin>
        <plugin>
            <groupId>org.openjfx</groupId>
            <artifactId>javafx-maven-plugin</artifactId>
            <version>0.0.2</version>
            <configuration>
                <release>12</release>
                <jlinkImageName>ytoolsfx</jlinkImageName> <!-- TODO: Modül ismi -->
                <launcher>launcher</launcher>
                <mainClass>ytoolsfx/com.yedhrab.applications.MainApp</mainClass> <!-- TODO: Main classının yolu -->
            </configuration>
        </plugin>
    </plugins>
</build>
```

### 🎈 Maven ile Başlangıç Yapılandırması

⇧ Shift + F10 ile projeyi çalıştırmanızı sağlar

* Edit Configuration + + + maven
* **Command Line** alanına `javafx:run` yazın
* **Before launch: Activate Tool Windov** alanınındaki + butonuna tıklayın
* Run maven goal'ı seçin
* `javafx:compile` yazıp kaydedin

> Ana kaynak [JavaFX and IntelliJ Moduler with Maven](https://openjfx.io/openjfx-docs/#IDE-Intellij) yazısıdır.

* Project Structures - **Libraries** kısmında + butona basın
* Çıkan ekranda **From Maven** yazısına tıklayın ve `org.openjfx:javafx-maven-plugin:0.0.2` yazıp indirin.

## 🧱 JavaFX Scene Builder

* `View` - `Show Sample Controller Skeleton` ile Controller'a yazılacak kodu görebiliriz
* Sol alttaki alandan `Controller` içerisinde
  * `Controller Class` alanına `<package>.Controller` yazarak Controller class'ını görmesini sağlıyoruz
* Sol alttaki `code` alanındakiler Controller'a aktarılacaktır
* Her importta `javafx.scene` olması lazımdır
  * Image vs..
* Sağ taraftaki `code` alanındaki `fx:id` kısmında ismi yazacak \(Controller'dan erişmek için\)

### 🔨 Scene Builder Yapılandırması

\[JFoenix\] framework'ü kullanıldığından [Scene Builder](https://gluonhq.com/products/scene-builder/)'ın library'lerine dahil edilmesi lazımdır.

* Sol üst kısımda **Library** sekmesinin en sağındaki ⚙ tıklayın
* JAR/FXML Management - Add Library/FXML from file system linkine tıklayın
* İndirdiğiniz \[JFoenix\] dosyasının `jar`'ını bulup, seçin.
* Check All ve Built in ayarları ile dahil edin.

> FXML dosyası ile Controller vs Resimlerin aynı package içerisinde olmaması durumunda **Scene Builder** öneri yapamaz 😢

## 💿 JavaFX RunTime Images

```text
export PATH_TO_FX_MODS=path/to/javafx-jmods-12.0.1
$JAVA_HOME/bin/jlink --module-path $PATH_TO_FX_MODS:mods/production --add-modules hellofx --output jre
jre/bin/java -m hellofx/org.openjfx.MainApp
```

## 🐛 Hata Notları

### 📌 class com.sun.javafx.fxml.FXMLLoaderHelper \(in unnamed module @0x24782c87\) cannot access class com.sun.javafx.util.Utils \(in module javafx.graphics\) because module javafx.graphics:

* Çıkan ekranda `VM Opitons` alanına alttaki metni kopyalayın:
  * `--module-path "C:\Program Files\Java\javafx-sdk-12.0.1\lib" --add-modules=javafx.controls,javafx.fxml`

### 📍 Error: Java FX Packager: Can not build artifact - fx: deploy is not available in this JDK

* **IntelliJ** üzerinde java ile gelen `fx:deploy` özelliği kaldırılmıştır \(java 11+\)
* Bu yüzden [buradan](https://openjfx.io/openjfx-docs/#modular) veya [jpackage](http://jdk.java.net/jpackage/) üzerinden kurulumlara bakabilirsin

### 📌 Error:Kotlin: The Kotlin standard library is not found in the module graph. Please ensure you have the 'requires kotlin.stdlib' clause in your module definition

Projeyi **Build** sekmesinden `Rebuild Edin` tekrar deneyin.

### 📍 \*\* has been compiled by a more recent version of Java Runtime\(class file version 56.0\), this version of Java Runtime only recognizes class file versions up to 52.0

* Jar dosyalarını Java 12 JVM ile çalıştırmamanızdan kaynaklanır
* Java 12 derleyicisi `target 12`, `bytecode 56` değerlerine sahiptir
* Java 8 `bytecode 52` değerine sahiptir
* Bir yerde kalmış olan Java 8 JVM'ine sahip olabilirsiniz

That's because you're not running the jars on a Java 12 JVM. You built them with a Java 12 compiler and targeted release 12. Java 12 is bytecode version 56. 52 is Java 8. You have an old Java 8 JVM somewhere and that's what you're running.

Either run with the Java 12 java or recompile using javac --release 8 ...

\(And that's not a JNI error\)

> [Kaynak](https://github.com/openjfx/openjfx-docs/issues/90#issuecomment-477743330)

## 🔗 Faydalı Bağlantılar

* [Drag Drop](https://www.youtube.com/watch?v=f7KGXUrAH0g)
* [Java Settings UI Design](https://www.youtube.com/watch?v=gJYXctDSIl8&list=PLniX3R2-dwS90WpmHq-hD7g_3xnkTwB6w&index=3)
* [Exe'ye çevirme](https://www.youtube.com/watch?v=iR85RRep-Po)

