# zmiiaby.v2.1_UAS_Pemograman-Mobile
# SerendipityApps - UAS_PEMROGMOBILE


Nama    : Mohammad Azmi Abdusssyukur

NIM     : 312210109

Kelas   : TI.22.A1

Mata Kuliah : Pemrograman Mobile 1

Dosen Pengampu   : Donny Maulana, S.Kom., M.M.S.I.


<img width="371" alt="logo" src="https://github.com/MohAzmii04/zmiiaby.v2.1_UAS_Pemograman-Mobile/assets/115864496/d8fa2bc2-7696-4ba2-918c-7395f2cab804">


## Tugas 1 
```
Buatkanlah :

1. Launcher Splash logo masing-masing Individu 

2. Buatkanlah untuk menampilkan semua project sebelum UTS dengan metode Ekplisit Intent dan

     Implisit Intent:

    a. Project Hallo

    b. Project Count

    c. Project Sianida

    d. Project TwoActivity

    e. Project Set Alarm

 
Untuk tampilan Layout Bebas, terima kasih.
```

> **Pada tugas 3 saya juga akan menambahkan video trailer di setiap film**

## Penjelasan & Hasil Program Tugas 1
1. Launcher Splash Logo
Pertama, yaitu membuat Launcher Splash Logo atau menampilkan logo / icon saat kita pertama kali membuka aplikasi.
Caranya adalah :

- Persiapkan gambar terlebih dahulu
- Selanjutnya kita klik `app`, lalu klik `res` dan setelahnya kita pilih dan klik `mipmap`
- Setelah itu klik kanan pada bagian `mipmap` , lalu pilih `new`
- Lalu pilih dan klik `Image Asset`
- Lalu ketika sudah terbuka, kita klik bagian `Icon Type` lalu pilih yang `Launcher Icons (Adaptive and Legacy)`
- Lalu pada bagian `Path` kita klik logo file lalu kita pilih dan klik file gambar yang telah disiapkan sebelumnya dan klik `OK`
- Lalu untuk ukuran logo / ikon bisa kita atur pada bagian `Resize`, Jika sudah kita klik `Next`
- Setelah itu kita klik `Finish`, Maka logo / ikon aplikasi kita akan berubah sesuai gambar yang kita inginkan

Untuk menambahkan file gambar seperti untuk SplashScreen, Background di setiap project kita bisa klik bagian `Resource Manager` lalu kita klik tanda `+`. Setelah itu kita pilih dan klik `Import Drawables`, setelah itu kita pilih dan klik file gambar yang sudah kita siapkan lalu klik `OK`. Maka gambar akan tersedia di `res` pada `drawable`.

- Lalu buka `backgroundlauncher.xml` dan masukkan code ini :
```
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@color/birumuda"/>
    <item>
        <bitmap
            android:src="@drawable/logo"
            android:gravity="center" />
    </item>
</layer-list>
```

> Untuk Warna bisa kita sesuaikan dengan Logo yang telah kita tambahkan sebelumnya

- Lalu, buka `themes.xml` yang letaknya ada di *res/values/themes*, dan tambahkan code ini didalam resourcesnya :
```
<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="SplashScreen" parent="Theme.MaterialComponents.DayNight.NoActionBar">
        <item name="android:windowBackground">@drawable/bg2</item>
        <item name="android:statusBarColor">?attr/colorOnPrimary</item>
    </style>
</resources>
```

- Selanjutnya kita buat java class nya agar SplashScreen bisa berjalan, lalu pada `SplashScreen.java` kita masukkan code dibawah ini :
```
package com.tgs9;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;

import androidx.appcompat.app.AppCompatActivity;

public class SplashScreen extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                startActivity(new Intent(SplashScreen.this, MainActivity.class));
                finish();
            }
        }, 2500);
    }
}
```

> Code di atas digukankan untuk menampilkan SplashScreen, ketika SplashScreen selesai dalam 2.5 detik maka akan langsung berpindah pada tampilan `MainActivity.java`.

- Buka `AndroidManifest.xml`, dan tambahkan code berikut didalam *application* :
```
<activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
</activity>
```
Selesai sudah kita membuat perintah Launcher Splash Logo, Selanjutnya kita akan ke tahap berikutnya yaitu membuat menu untuk menampilkan semua project yang sudah dibuat pada pertemuan sebelumnya.


## 2. Menu Utama 
Yang kedua, disini kita akan membuat menu utamanya yang akan berjalan setelah SplashScreen Logo.
Caranya adalah:

Jika awal pembuatan project kita memilih template Empty Views Activity, maka pada layout otomatis terbuat file `activity_main.xml` dan pada java akan ada `MainActivity.java`.
Maka langsung saja kita buka `activity_main.xml`, dan buat code seperti berikut ini:
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bg1"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"/>

    <TextView
        android:id="@+id/txtJudul"
        android:layout_width="match_parent"
        android:layout_height="68dp"
        android:layout_alignParentTop="true"
        android:layout_alignParentBottom="true"
        android:layout_marginTop="46dp"
        android:layout_marginBottom="569dp"
        android:gravity="center"
        android:scaleType="centerCrop"
        android:text="Please select and click on the project below"
        android:textColor="@color/black"
        android:textSize="25dp"
        android:textStyle="bold" />

    <Button
        android:id="@+id/btnHelloWorld"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="100dp"
        android:layout_marginTop="200dp"
        android:layout_marginEnd="100dp"
        android:onClick="btnHelloWorld"
        android:background="@color/hijaumuda"
        android:text="Hello World!!!"
        tools:ignore="UsingOnClickInXml"
        android:scaleType="centerCrop"/>

    <Button
        android:id="@+id/btnProjectCount"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_below="@+id/btnHelloWorld"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="100dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="100dp"
        android:onClick="btnCount"
        android:background="@color/cream"
        android:text="Count"
        tools:ignore="UsingOnClickInXml"
        android:scaleType="centerCrop"/>

    <Button
        android:id="@+id/btnProjectSianida"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_below="@+id/btnProjectCount"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="100dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="100dp"
        android:onClick="btnSianida"
        android:background="@color/birumuda"
        android:scaleType="centerCrop"
        android:text="Scroll Movie"
        tools:ignore="UsingOnClickInXml" />

    <Button
        android:id="@+id/btnTwoActivity"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_below="@+id/btnProjectSianida"
        android:layout_alignParentEnd="true"
        android:layout_alignParentStart="true"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="100dp"
        android:layout_marginStart="100dp"
        android:onClick="btnTwoActivity"
        android:background="@color/pink"
        android:text="Two Activity"
        tools:ignore="UsingOnClickInXml"
        android:scaleType="centerCrop"/>

    <Button
        android:id="@+id/btnSetAlarm"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_below="@+id/btnTwoActivity"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="100dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="100dp"
        android:onClick="btnSetAlarm"
        android:background="@color/purple"
        android:text="Set Alarm"
        tools:ignore="UsingOnClickInXml"
        android:scaleType="centerCrop"/>

</RelativeLayout>
```
- Setelah itu kita buka `MainActivity.java` untuk menambahkan code intent untuk masing-masing tombol :
```
package com.tgs9;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.btnSetAlarm).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Panggil metode untuk mengatur alarm
                setAlarm();
            }
        });
    }
    private void setAlarm() {
        Intent alarm = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        startActivity(alarm);
    }

    public void btnHelloWorld(View view) {
        Intent helloworld = new Intent(MainActivity.this, HelloActivity.class);
        startActivity(helloworld);
    }

    public void btnCount(View view) {
        Intent count = new Intent(MainActivity.this, CountActivity.class);
        startActivity(count);
    }

    public void btnSianida(View view) {
        Intent sianida = new Intent(MainActivity.this, SianidaActivity.class);
        startActivity(sianida);
    }

    public void btnTwoActivity(View view) {
        Intent twoact = new Intent(MainActivity.this, TwoActivity.class);
        startActivity(twoact);
    }
}
```
> Button *HelloWorld, Count, Sianida dan TwoActivity* menggunakan Explicit Intent, dan project *SetAlarm* menggunakan Implicit Intent.

> Menu halaman utama dan tombol-tombol aplikasi sudah berhasil dibuat. Maka selanjutnya yang kita lakukan adalah menambahkan coding pada `AndroidManifest.xml` agar aplikasi dapat berjalan.

## 3. AndroidManifest.xml
Didalam `AndroidManifest.xml` kita tambahkan semua java class dari semua project kita sebelumnya. Berikut nama java class dari berbagai project yang telah saya buat:

a. Project Hello World = HelloActivity.java

b. Project Count = CountActivity.java

c. Project Scroll Movie = SianidaActivity.java

d. Project TwoActivity = TwoActivity.java dan Two2Activity.java

e. Project Set Alarm = MainActivity.java (karena merupakan Implicit Intent, jadi code untuk set alarm langsung dibuat disini)

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-permission
        android:name="com.android.alarm.permission.SET_ALARM" />
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Design.Light"
        tools:targetApi="31">

        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.SET_ALARM" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>

        <activity
            android:name=".HelloActivity"
            android:exported="true" />

        <activity
            android:name=".TwoActivity"
            android:exported="true" />

        <activity
            android:name=".Two2Activity"
            android:exported="true" />

        <activity
            android:name=".CountActivity"
            android:exported="true" />

        <activity
            android:name=".SianidaActivity"
            android:exported="true" />

        <activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

## 4. Code All Projects (Strings, Colors dan Dimens)
> `Strings.xml`
```
<resources>
    <string name="app_name">TGS9INTENT</string>
    <string name="Hello_World">Hello World!!</string>

    <string name="button_main">Send</string>
    <string name="editText_main">Enter Your Message Here</string>
    <string name="text_header">Message Received</string>
    <string name="buttton_second">Reply</string>
    <string name="editText_second">Enter Your Reply Here</string>
    <string name="text_header_reply">Reply Received</string>

    <string name="button_label_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">1</string>
    <string name="toast_massage">Hello Toast!</string>
    <string name="button_label_restart">Restart</string>
    <string name="enter_fibonacci_limit">Masukkan Angka Limit</string>

    <string name="article_title"> Kasus Sianida</string>
    <string name="article_subtitle">ICE COLD!</string>

    <string name="article_text"> Film dokumenter Ice Cold: Murder, Coffee and Jessica Wongso memaparkan pertanyaan tak terjawab tentang persidangan yang dilalui Jessica Wongso. Dengan menyajikan perspektif baru, film ini hadir bertahun-tahun setelah kematian sahabat Jessica, Wayan Mirna Salihin.


Film ini menggambarkan bagaimana Jessica yang mengajak teman-temannya, termasuk Mirna, untuk bertemu setelah sekian lama tak berjumpa. Pertemuan di salah satu kafe di mal ibu kota tersebut pun berlangsung lancar, sebelum akhirnya Mirna pingsan sesaat setelah meminum kopi yang sebelumnya dipesan Jessica.Dokumenter ini turut menyajikan rekaman CCTV pada waktu kejadian, berbagai footage berita saat persidangan berlangsung, hingga wawancara eksklusif dengan beberapa sumber, termasuk Jessica Wongso.


Persidangan atas dugaan pembunuhan Mirna Salihin digelar lima bulan setelah kematiannya. Sidang tersebut melalui 32 kali persidangan dengan menghadirkan puluhan saksi di pengadilan. Hasilnya, Jessica Wongso divonis bersalah atas kematian Mirna dan dijatuhi hukuman 20 tahun penjara.
Kasus yang berjalan cukup lama tersebut menyita banyak perhatian dari masyarakat Indonesia. Musababnya, banyak misteri tak terjawab selama rangkaian persidangan yang panjang tersebut. Salah satunya adalah mengenai akses untuk mendapatkan bubuk sianida yang tidak bisa didapatkan oleh orang sembarangan. Selain itu, motif Jessica di balik pembunuhan tersebut pun belum menemukan jawabannya.

        
Film dokumenter buatan Netflix ini menyoroti rangkaian persidangan yang saat itu menjadi sidang pertama yang disiarkan secara langsung di berbagai stasiun televisi Indonesia. Selain itu, kasus ini juga diliput secara intens oleh media massa, baik nasional maupun internasional.Tak hanya itu, pihak rumah produksi Beach House Pictures juga berhasil mendapatkan akses untuk mewawancarai Jessica Wongso secara langsung dari balik tahanan. Dalam video trailer yang diluncurkannya, ditampilkan juga sejumlah wawancara eksklusif yang dilakukan dengan beberapa narasumber. Mulai dari ayah dan saudara kembar  Mirna Salihin, pengacara Jessica Wongso, jurnalis yang mendalami kasus tersebut, hingga bagaimana saat itu kasus ini begitu ramai diberitakan oleh media massa Indonesia dan internasional.</string>
    
</resources>
```

> `Colors.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="birumuda">#ABCBFA</color>
    <color name ="purple">#E3A2ED</color>
    <color name="hijau">#92A676</color>
    <color name="biru">#8FC2EA</color>
    <color name="hijaumuda">#C2E69C</color>
    <color name="cream">#E6C18A</color>
</resources>
```

> `Dimens.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <dimen name="padding_regular">10dp</dimen>
    <dimen name="line_spacing">5sp</dimen>
</resources>
```

## A. Code Project Hello World 
> `activity_hello.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".HelloActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bg3"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"/>

    <TextView
        android:id="@+id/txthello"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="Hello World!!"
        android:textColor="@color/hijau"
        android:textSize="20pt"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.503"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.413"
        tools:ignore="TextSizeCheck" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

> `HelloActivity.java`
```
package com.tgs9;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

public class HelloActivity extends AppCompatActivity{
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_hello);
    }
}
```

## B. Code Project Count
> `activity_count.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:ignore="ExtraText"
    tools:context=".CountActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bg4"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop" />


    <Button
        android:id="@+id/button_limit"
        android:layout_width="354dp"
        android:layout_height="76dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="8dp"
        android:background="@color/cream"
        android:onClick="setLimit"
        android:text="Masukkan Angka Limit"
        android:textColor="@android:color/black"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.507"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />

    <Button
        android:id="@+id/button_count"
        android:layout_width="173dp"
        android:layout_height="70dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="24dp"
        android:background="@color/cream"
        android:onClick="countUp"
        android:text="Count"
        android:textColor="@android:color/black"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.039"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />

    <Button
        android:id="@+id/button_restart"
        android:layout_width="173dp"
        android:layout_height="72dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="24dp"
        android:background="@color/cream"
        android:onClick="back1"
        android:text="Restart"
        android:textColor="@android:color/black"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.965"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <TextView
        android:id="@+id/show_count"
        android:layout_width="305dp"
        android:layout_height="442dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:gravity="center_vertical"
        android:text="1"
        android:textAlignment="center"
        android:textColor="@color/colorAccent"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.505"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_limit"
        app:layout_constraintVertical_bias="0.51"
        tools:ignore="RtlCompat" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

> `CountActivity.java`
```
package com.tgs9;

import android.app.AlertDialog;
import android.content.DialogInterface;
import android.graphics.Color;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;


public class CountActivity extends AppCompatActivity {
    private TextView show_count;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 1;
    private int limit = -1; // Inisialisasi limit dengan nilai default

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_count);

        show_count = findViewById(R.id.show_count);
    }

    public void countUp(View view) {
        if (count == 0) {
            show_count.setText("0");
        }
        else if (count == 1) {
            show_count.setText("1");
        }
        else {
            if (limit != -1 && count > limit) {
                // Jika count melebihi limit, atur ulang perhitungan
                count = 0;
                fibNMinus1 = 1;
                fibNMinus2 = 0;
                show_count.setText(getString(R.string.count_initial_value));
            }
            else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;

                //Mengatur warna teks berdasarkan angka Fibonacci
                int colorResId = R.color.colorAccent; // Warna Default
                switch (count % 11) {
                    case 1:
                        colorResId = R.color.colorAccent; // Warna Pink Tua
                        break;
                    case 2:
                        colorResId = R.color.hijaumuda; // Warna Hijau Muda
                        break;
                    case 3:
                        colorResId = R.color.purple; // Warna Ungu
                        break;
                    case 4:
                        colorResId = R.color.salem; // Warna Salem
                        break;
                    case 5:
                        colorResId = R.color.birumuda; // Warna Biru Muda
                        break;
                    case 6 :
                        colorResId = R.color.kuning; // Warna Kuning
                        break;
                    case 7:
                        colorResId = R.color.hijau; // Warna Hijau
                        break;
                    case 8:
                        colorResId = R.color.cream; // Warna Cream
                        break;
                    case 9:
                        colorResId = R.color.pink; // Warna Pink
                        break;
                    case 10:
                        colorResId = R.color.biru; // Warna Biru
                        break;
                    case 11:
                        colorResId = R.color.orange; // Warna Orange
                        break;
                }
                show_count.setTextColor(getResources().getColor(colorResId));
                show_count.setText(String.valueOf(fibCurrent));
            }
        }

        count++;
    }

    public void back1(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        show_count.setText(getString(R.string.count_initial_value));
    }

    public void setLimit(View view) {
        // Create and display a dialog to set the limit
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set Limit");

        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);

        builder.setPositiveButton("OK", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                // Get the limit from the input and set it for calculations
                String limitStr = input.getText().toString();
                limit = Integer.parseInt(limitStr);
            }
        });

        builder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                dialog.cancel();
            }
        });

        builder.show();
    }
}
```

## C. Code Project Scroll Movie
> `activity_scrollmovie.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    tools:context=".SianidaActivity">

    <TextView
        android:id="@+id/article_heading"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/biru"
        android:padding="@dimen/padding_regular"
        android:text="@string/article_title"
        android:textAppearance="@android:style/TextAppearance.DeviceDefault.Large"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    <ScrollView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/article_heading">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">

            <TextView
                android:id="@+id/article_subheading"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:padding="@dimen/padding_regular"
                android:text="@string/article_subtitle"
                android:textAlignment="center"
                android:textAppearance="@android:style/TextAppearance.DeviceDefault"
                android:textColor="#1AA0C1" />

            <TextView
                android:id="@+id/article"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:autoLink="web"
                android:lineSpacingExtra="@dimen/line_spacing"
                android:padding="@dimen/padding_regular"
                android:text="@string/article_text"
                tools:ignore="VisualLintLongText" />
        </LinearLayout>
    </ScrollView>
</RelativeLayout>
```

> `SianidaActivity.java`
```
package com.tgs9;

import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;

public class SianidaActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_scrollmovie);
    }
}
```


## D. Code Project Two Activity
> `activity_twoactivity.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".TwoActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bg5" />

    <TextView
        android:id="@+id/text_header_reply"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="@string/text_header_reply"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textStyle="bold"
        android:visibility="invisible"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>

    <TextView
        android:id="@+id/text_message_reply"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        android:visibility="invisible"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text_header_reply" />

    <Button
        android:id="@+id/button_main"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:layout_marginRight="16dp"
        android:text="@string/button_main"
        android:background="@color/pink"
        android:onClick="LaunchSecondActivity"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        tools:ignore="UsingOnClickInXml"/>

    <EditText
        android:id="@+id/editText_main"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="@string/editText_main"
        android:inputType="textLongMessage"
        android:minHeight="48dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button_main"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `activity_twoact2.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".Two2Activity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bg5" />

    <TextView
        android:id="@+id/text_header"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="@string/text_header"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textStyle="bold"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/text_message"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text_header" />

    <Button
        android:id="@+id/button_second"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:layout_marginRight="16dp"
        android:text="@string/buttton_second"
        android:onClick="returnReply"
        android:background="@color/pink"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <EditText
        android:id="@+id/editText_second"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="@string/editText_second"
        android:inputType="textLongMessage"
        android:minHeight="48dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button_second"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `TwoActivity.java`
```
package com.tgs9;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

public class TwoActivity extends AppCompatActivity {

    private static final String LOG_TAG = TwoActivity.class.getSimpleName();

    public static final String EXTRA_MESSAGE = "com.example.android.Two2Activity.extra.MESSAGE";

    public static final int TEXT_REQUEST = 1;

    private EditText mMessageEditText;

    private TextView mReplyHeadTextView;

    private TextView mReplyTextView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_twoactivity);

        mMessageEditText = findViewById(R.id.editText_main);
        mReplyHeadTextView = findViewById(R.id.text_header_reply);
        mReplyTextView = findViewById(R.id.text_message_reply);
    }

    public void LaunchSecondActivity(View view) {
        Log.d(LOG_TAG, "Button clicked!");
        Intent intent = new Intent(this, Two2Activity.class);
        String message = mMessageEditText.getText().toString();
        intent.putExtra(EXTRA_MESSAGE, message);
        startActivityForResult(intent, TEXT_REQUEST);
    }

    @Override
    public void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);

        if (requestCode == TEXT_REQUEST) {
            if (resultCode == RESULT_OK) {
                String reply = data.getStringExtra(Two2Activity.EXTRA_REPLY);

                mReplyHeadTextView.setVisibility(View.VISIBLE);
                mReplyTextView.setText(reply);
                mReplyTextView.setVisibility(View.VISIBLE);
            }
        }
    }
}
```

> `Two2Activity.java`
```
package com.tgs9;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class Two2Activity extends AppCompatActivity {

    public static final String EXTRA_REPLY ="com.example.android.Two2Activity.extra.REPLY";
    public static final String EXTRA_MESSAGE ="com.example.android.Two2Activity.extra.MESSAGE";
    private EditText mReply;

    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_twoact2);

        mReply = findViewById(R.id.editText_second);

        Intent intent = getIntent();
        String message = intent.getStringExtra(Two2Activity.EXTRA_MESSAGE);

        TextView textView = findViewById(R.id.text_message);
        textView.setText(message);
    }
    public void returnReply(View view){
        String reply = mReply.getText().toString();
        Intent replyIntent = new Intent();
        setResult(RESULT_OK, replyIntent);
        finish();
    }
}
```

## E. Code Project Set Alarm
> Pertama, buatlah button terlebih dahulu pada `activity_main.xml`, bersama dengan button aplikasi lainnya :
```
<Button
        android:id="@+id/btnSetAlarm"
        android:layout_width="150dp"
        android:layout_height="60dp"
        android:layout_below="@+id/btnTwoActivity"
        android:layout_alignParentStart="true"
        android:layout_alignParentEnd="true"
        android:layout_marginStart="100dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="100dp"
        android:onClick="btnSetAlarm"
        android:background="@color/purple"
        android:text="Set Alarm"
        tools:ignore="UsingOnClickInXml"
        android:scaleType="centerCrop"/>
```

> Lalu tambahkan code Implicit Intent pada `MainActivity,java` :
```
findViewById(R.id.btnSetAlarm).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Panggil metode untuk mengatur alarm
                setAlarm();
            }
        });
    }
    private void setAlarm() {
        Intent alarm = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        startActivity(alarm);
    }
```

> - Selanjutnya buka `AndroidManifest.xml` dan tambahkan code untuk izin membuka Alarm :
```
<uses-permission android:name="com.android.alarm.permission.SET_ALARM" />
```

- Tambahkan code berikut pada bagian *application* agar set alarm dapat berjalan :
```
<activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.SET_ALARM" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
</activity>
```


## Penjelasan & Hasil Program Tugas 2

1. Menu Utama 
Pertama yang harus kita lakukan adalah mengganti tampilan menu utamanya dengan code yang baru agar ikon tombol berubah menjadi gambar, caranya adalah :

Jika awal pembuatan project kita memilih template Empty Views Activity, maka pada layout otomatis terbuat file `activity_main.xml` dan pada java akan ada `MainActivity.java`. Maka langsung saja kita buka `activity_main.xml`, dan buat code seperti berikut ini:

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">


    <RelativeLayout
        android:layout_width="500dp"
        android:layout_height="match_parent"
        android:background="@drawable/bg6">

    </RelativeLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_marginLeft="16dp"
        android:layout_marginTop="100dp"
        android:layout_marginRight="16dp"
        android:orientation="vertical">

        <TextView
            android:id="@+id/textView"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:fontFamily="serif"
            android:text="Menu Program"
            android:textAlignment="center"
            android:textColor="@color/black"
            android:textSize="34sp"
            android:textStyle="bold" />

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="150dp"
            android:layout_margin="5dp"
            android:orientation="horizontal">

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu1"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">

                    <ImageView
                        android:id="@+id/imageView0"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/worldwide" />

                    <TextView
                        android:id="@+id/textView0"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Hello World"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu2"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">

                    <ImageView
                        android:id="@+id/imageView1"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/mathematics_symbols" />

                    <TextView
                        android:id="@+id/textView1"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Fibonacci"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="150dp"
            android:layout_margin="5dp"
            android:orientation="horizontal">

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu3"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">

                    <ImageView
                        android:id="@+id/imageView2"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/clapperboard" />

                    <TextView
                        android:id="@+id/textView2"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Scroll Movie"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu4"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">

                    <ImageView
                        android:id="@+id/imageView3"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/alarm__1_" />

                    <TextView
                        android:id="@+id/textView3"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Alarm"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>
        </LinearLayout>

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="150dp"
            android:layout_margin="5dp"
            android:orientation="horizontal">

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu5"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">

                    <ImageView
                        android:id="@+id/imageView4"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/messaging" />

                    <TextView
                        android:id="@+id/textView4"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Two Activity"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu6"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">

                    <ImageView
                        android:id="@+id/imageView5"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/gps" />

                    <TextView
                        android:id="@+id/textView5"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Maps"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

        </LinearLayout>
    </LinearLayout>

</RelativeLayout>
```

> - Setelah itu kita buka `MainActivity.java` untuk menambahkan code intent untuk masing-masing tombol :
```
package com.cipaapps;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.cdMenu4).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                setAlarm();
            }
        });

        findViewById(R.id.cdMenu1).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolSatu ditekan, pindah ke HelloActivity
                Intent helloworld = new Intent(MainActivity.this, HelloActivity.class);
                startActivity(helloworld);
            }
        });

        findViewById(R.id.cdMenu2).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolDua ditekan, lakukan aksi yang diinginkan
                // Misalnya, pindah ke aktivitas lain atau jalankan fungsi khusus
                Intent toast = new Intent(MainActivity.this, CountActivity.class);
                startActivity(toast);
            }
        });

        findViewById(R.id.cdMenu3).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolDua ditekan, lakukan aksi yang diinginkan
                // Misalnya, pindah ke aktivitas lain atau jalankan fungsi khusus
                Intent sianida = new Intent(MainActivity.this, SianidaActivity.class);
                startActivity(sianida);
            }
        });

        findViewById(R.id.cdMenu5).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolDua ditekan, lakukan aksi yang diinginkan
                // Misalnya, pindah ke aktivitas lain atau jalankan fungsi khusus
                Intent twoactivity = new Intent(MainActivity.this, TwoActivity.class);
                startActivity(twoactivity);
            }
        });

        findViewById(R.id.cdMenu6).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Example location: Jakarta, Indonesia
                Uri geoLocation = Uri.parse("geo:-6.2088,106.8456");
                openMaps(geoLocation);
            }
        });
    }

    private void setAlarm() {
        Intent alarmIntent = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        // Add extra details for the alarm, e.g., alarm time, label, etc.
        // alarmIntent.putExtra(...
        startActivity(alarmIntent);
    }
    private void openMaps(Uri geoLocation) {
        Intent maps = new Intent(Intent.ACTION_VIEW);
        maps.setData(geoLocation);
        if (maps.resolveActivity(getPackageManager()) != null) {
            startActivity(maps);
        }
    }


}
```

> Button *HelloWorld, Count, Sianida dan TwoActivity* menggunakan Explicit Intent, dan untuk project *SetAlarm* beserta *Maps* menggunakan Implicit Intent.

> Menu halaman utama dan tombol-tombol aplikasi sudah berhasil dibuat. Maka selanjutnya yang kita lakukan adalah menambahkan coding pada `AndroidManifest.xml` agar aplikasi dapat berjalan.

**2. AndroidManifest.xml**
Didalam `AndroidManifest.xml` kita tambahkan semua java class dari semua project kita sebelumnya. Berikut nama java class dari berbagai project yang telah saya buat:

a. Project Hello World = HelloActivity.java 

b. Project Count = CountActivity.java 

c. Project Scroll Movie = SianidaActivity.java 

d. Project TwoActivity = TwoActivity.java dan Two2Activity.java 

e. Project Set Alarm = MainActivity.java 

f. Project Maps = MainActivity.java (karena merupakan Implicit Intent, jadi code untuk SetAlarm dan Maps langsung dibuat disini)

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-permission
        android:name="com.android.alarm.permission.SET_ALARM" />
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Design.Light"
        tools:targetApi="31">

        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.SET_ALARM" />
                <category android:name="android.intent.category.DEFAULT" />
                <action android:name="android.intent.action.VIEW" />
                <data android:scheme="geo" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>


        <activity
            android:name=".HelloActivity"
            android:exported="true" />

        <activity
            android:name=".TwoActivity"
            android:exported="true" />

        <activity
            android:name=".Two2Activity"
            android:exported="true" />

        <activity
            android:name=".CountActivity"
            android:exported="true" />

        <activity
            android:name=".SianidaActivity"
            android:exported="true" />

        <activity
            android:name=".SplashScreen"
            android:exported="true"
            android:theme="@style/SplashScreen">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

    </application>

</manifest>
```

**3. Code All Projects (XML files / res)**
> Pada menu values :
- `Strings.xml` 
```
<resources>
    <string name="app_name">cipaapps</string>
    <string name="Hello_World">Hello World!!</string>

    <string name="button_main">Send</string>
    <string name="editText_main">Enter Your Message Here</string>
    <string name="text_header">Message Received</string>
    <string name="buttton_second">Reply</string>
    <string name="editText_second">Enter Your Reply Here</string>
    <string name="text_header_reply">Reply Received</string>

    <string name="button_label_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">1</string>
    <string name="toast_massage">Hello Toast!</string>
    <string name="button_label_restart">Restart</string>
    <string name="enter_fibonacci_limit">Masukkan Angka Limit</string>

    <string name="article_title"> Kasus Sianida</string>
    <string name="article_subtitle">ICE COLD!</string>

    <string name="article_text"> Film dokumenter Ice Cold: Murder, Coffee and Jessica Wongso memaparkan pertanyaan tak terjawab tentang persidangan yang dilalui Jessica Wongso. Dengan menyajikan perspektif baru, film ini hadir bertahun-tahun setelah kematian sahabat Jessica, Wayan Mirna Salihin.


Film ini menggambarkan bagaimana Jessica yang mengajak teman-temannya, termasuk Mirna, untuk bertemu setelah sekian lama tak berjumpa. Pertemuan di salah satu kafe di mal ibu kota tersebut pun berlangsung lancar, sebelum akhirnya Mirna pingsan sesaat setelah meminum kopi yang sebelumnya dipesan Jessica.Dokumenter ini turut menyajikan rekaman CCTV pada waktu kejadian, berbagai footage berita saat persidangan berlangsung, hingga wawancara eksklusif dengan beberapa sumber, termasuk Jessica Wongso.


Persidangan atas dugaan pembunuhan Mirna Salihin digelar lima bulan setelah kematiannya. Sidang tersebut melalui 32 kali persidangan dengan menghadirkan puluhan saksi di pengadilan. Hasilnya, Jessica Wongso divonis bersalah atas kematian Mirna dan dijatuhi hukuman 20 tahun penjara.
Kasus yang berjalan cukup lama tersebut menyita banyak perhatian dari masyarakat Indonesia. Musababnya, banyak misteri tak terjawab selama rangkaian persidangan yang panjang tersebut. Salah satunya adalah mengenai akses untuk mendapatkan bubuk sianida yang tidak bisa didapatkan oleh orang sembarangan. Selain itu, motif Jessica di balik pembunuhan tersebut pun belum menemukan jawabannya.


Film dokumenter buatan Netflix ini menyoroti rangkaian persidangan yang saat itu menjadi sidang pertama yang disiarkan secara langsung di berbagai stasiun televisi Indonesia. Selain itu, kasus ini juga diliput secara intens oleh media massa, baik nasional maupun internasional.Tak hanya itu, pihak rumah produksi Beach House Pictures juga berhasil mendapatkan akses untuk mewawancarai Jessica Wongso secara langsung dari balik tahanan. Dalam video trailer yang diluncurkannya, ditampilkan juga sejumlah wawancara eksklusif yang dilakukan dengan beberapa narasumber. Mulai dari ayah dan saudara kembar  Mirna Salihin, pengacara Jessica Wongso, jurnalis yang mendalami kasus tersebut, hingga bagaimana saat itu kasus ini begitu ramai diberitakan oleh media massa Indonesia dan internasional.</string>

</resources>
```

- `Colors.xml` 
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="birumuda">#ABCBFA</color>
    <color name="salem">#F8C6E6</color>
    <color name ="purple">#E3A2ED</color>
    <color name="hijau">#92A676</color>
    <color name="biru">#8FC2EA</color>
    <color name="hijaumuda">#C2E69C</color>
    <color name="kuning">#FFEB3B</color>
    <color name="orange">#FF9800</color>
    <color name="cream">#E6C18A</color>
</resources>
```

- `Dimens.xml` 
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <dimen name="padding_regular">10dp</dimen>
    <dimen name="line_spacing">5sp</dimen>
</resources>
```

> Pada menu themes :
- `themes.xml`
```
<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="SplashScreen" parent="Theme.MaterialComponents.DayNight.NoActionBar">
        <item name="android:windowBackground">@drawable/splashscreen</item>
        <item name="android:statusBarColor">?attr/colorOnPrimary</item>
    </style>
</resources>
```

> Pada menu drawable :
- `backgroundlauncher.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@color/birumuda"/>
    <item>
        <bitmap
            android:src="@drawable/logo"
            android:gravity="center" />
    </item>
</layer-list>
```

***A. Code Project Splash Screen**

> `SplashScreen.java`
```
package com.cipaapps;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;

import androidx.appcompat.app.AppCompatActivity;

public class SplashScreen extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                startActivity(new Intent(SplashScreen.this, MainActivity.class));
                finish();
            }
        }, 2500);
    }
}
```

**B. Code Project Hello World**
> `activity_hello.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".HelloActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bg4"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"/>

    <TextView
        android:id="@+id/txthello"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:gravity="center"
        android:text="Hello World!!"
        android:textColor="@color/hijaumuda"
        android:textSize="20pt"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.503"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.413"
        tools:ignore="TextSizeCheck" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

> `HelloActivity.java`
```
package com.cipaapps;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

public class HelloActivity extends AppCompatActivity{
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_hello);
    }
}
```

**C. Code Project Count**
> `activity_count.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:ignore="ExtraText"
    tools:context=".CountActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="@drawable/bg5"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop" />


    <Button
        android:id="@+id/button_limit"
        android:layout_width="354dp"
        android:layout_height="76dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="8dp"
        android:background="@color/hijau"
        android:onClick="setLimit"
        android:text="Masukkan Angka Limit"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.507"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />

    <Button
        android:id="@+id/button_count"
        android:layout_width="173dp"
        android:layout_height="70dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="24dp"
        android:background="@color/hijau"
        android:onClick="countUp"
        android:text="Count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.039"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />

    <Button
        android:id="@+id/button_restart"
        android:layout_width="173dp"
        android:layout_height="72dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="24dp"
        android:background="@color/hijau"
        android:onClick="back1"
        android:text="Restart"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.965"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <TextView
        android:id="@+id/show_count"
        android:layout_width="305dp"
        android:layout_height="442dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:gravity="center_vertical"
        android:text="1"
        android:textAlignment="center"
        android:textColor="@color/black"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.505"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_limit"
        app:layout_constraintVertical_bias="0.51"
        tools:ignore="RtlCompat" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

> `CountActivity.java`
```
package com.cipaapps;

import android.annotation.SuppressLint;
import android.app.AlertDialog;
import android.content.DialogInterface;
import android.graphics.Color;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;


public class CountActivity extends AppCompatActivity {
    private TextView show_count;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 1;
    private int limit = -1; // Inisialisasi limit dengan nilai default


    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_count);

        show_count = findViewById(R.id.show_count);
    }

    public void countUp(View view) {
        if (count == 0) {
            show_count.setText("0");
        }
        else if (count == 1) {
            show_count.setText("1");
        }
        else {
            if (limit != -1 && count > limit) {
                // Jika count melebihi limit, atur ulang perhitungan
                count = 0;
                fibNMinus1 = 1;
                fibNMinus2 = 0;
                show_count.setText(getString(R.string.count_initial_value));
            }
            else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;

                //Mengatur warna teks berdasarkan angka Fibonacci
                int colorResId = R.color.colorAccent; // Warna Default
                switch (count % 11) {
                    case 1:
                        colorResId = R.color.colorAccent; // Warna Pink Tua
                        break;
                    case 2:
                        colorResId = R.color.hijaumuda; // Warna Hijau Muda
                        break;
                    case 3:
                        colorResId = R.color.purple; // Warna Ungu
                        break;
                    case 4:
                        colorResId = R.color.salem; // Warna Salem
                        break;
                    case 5:
                        colorResId = R.color.birumuda; // Warna Biru Muda
                        break;
                    case 6 :
                        colorResId = R.color.kuning; // Warna Kuning
                        break;
                    case 7:
                        colorResId = R.color.hijau; // Warna Hijau
                        break;
                    case 8:
                        colorResId = R.color.cream; // Warna Cream
                        break;
                    case 9:
                        colorResId = R.color.pink; // Warna Pink
                        break;
                    case 10:
                        colorResId = R.color.biru; // Warna Biru
                        break;
                    case 11:
                        colorResId = R.color.orange; // Warna Orange
                        break;
                }
                show_count.setTextColor(getResources().getColor(colorResId));
                show_count.setText(String.valueOf(fibCurrent));
            }
        }

        count++;
    }

    public void back1(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        show_count.setText(getString(R.string.count_initial_value));
    }

    public void setLimit(View view) {
        // Create and display a dialog to set the limit
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set Limit");

        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);

        builder.setPositiveButton("OK", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                // Get the limit from the input and set it for calculations
                String limitStr = input.getText().toString();
                limit = Integer.parseInt(limitStr);
            }
        });

        builder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                dialog.cancel();
            }
        });

        builder.show();
    }
}
```

**D. Code Project Scroll Movie**
> `activity_scrollmovie.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    tools:context=".SianidaActivity">

    <TextView
        android:id="@+id/article_heading"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/biru"
        android:padding="@dimen/padding_regular"
        android:text="@string/article_title"
        android:textAppearance="@android:style/TextAppearance.DeviceDefault.Large"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    <ScrollView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/article_heading">

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="vertical">

            <TextView
                android:id="@+id/article_subheading"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:padding="@dimen/padding_regular"
                android:text="@string/article_subtitle"
                android:textAlignment="center"
                android:textAppearance="@android:style/TextAppearance.DeviceDefault"
                android:textColor="@color/colorPrimary" />

            <TextView
                android:id="@+id/article"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:autoLink="web"
                android:lineSpacingExtra="@dimen/line_spacing"
                android:padding="@dimen/padding_regular"
                android:text="@string/article_text"
                tools:ignore="VisualLintLongText" />
        </LinearLayout>
    </ScrollView>
</RelativeLayout>
```

> `SianidaActivity.java`
```
package com.cipaapps;

import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;

public class SianidaActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_scrollmovie);
    }
}
```

## E. Code Project Two Activity
> `activity_twoactivity.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".TwoActivity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bg1" />

    <TextView
        android:id="@+id/text_header_reply"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="@string/text_header_reply"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textStyle="bold"
        android:visibility="invisible"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"/>

    <TextView
        android:id="@+id/text_message_reply"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        android:visibility="invisible"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text_header_reply" />

    <Button
        android:id="@+id/button_main"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:layout_marginRight="16dp"
        android:text="@string/button_main"
        android:background="@color/pink"
        android:onClick="LaunchSecondActivity"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        tools:ignore="UsingOnClickInXml"/>

    <EditText
        android:id="@+id/editText_main"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="@string/editText_main"
        android:inputType="textLongMessage"
        android:minHeight="48dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button_main"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `activity_two2activity.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    tools:context=".Two2Activity">

    <ImageView
        android:id="@+id/background"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:adjustViewBounds="true"
        android:scaleType="centerCrop"
        android:src="@drawable/bg1" />

    <TextView
        android:id="@+id/text_header"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="16dp"
        android:text="@string/text_header"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textStyle="bold"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/text_message"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginLeft="8dp"
        android:layout_marginTop="8dp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/text_header" />

    <Button
        android:id="@+id/button_second"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:layout_marginRight="16dp"
        android:text="@string/buttton_second"
        android:onClick="returnReply"
        android:background="@color/pink"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <EditText
        android:id="@+id/editText_second"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="@string/editText_second"
        android:inputType="textLongMessage"
        android:minHeight="48dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toStartOf="@+id/button_second"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

> `TwoActivity.java`
```
package com.cipaapps;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

public class TwoActivity extends AppCompatActivity {

    private static final String LOG_TAG = TwoActivity.class.getSimpleName();

    public static final String EXTRA_MESSAGE = "com.example.android.Two2Activity.extra.MESSAGE";

    public static final int TEXT_REQUEST = 1;

    private EditText mMessageEditText;

    private TextView mReplyHeadTextView;

    private TextView mReplyTextView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_twoactivity);

        mMessageEditText = findViewById(R.id.editText_main);
        mReplyHeadTextView = findViewById(R.id.text_header_reply);
        mReplyTextView = findViewById(R.id.text_message_reply);
    }

    public void LaunchSecondActivity(View view) {
        Log.d(LOG_TAG, "Button clicked!");
        Intent intent = new Intent(this, Two2Activity.class);
        String message = mMessageEditText.getText().toString();
        intent.putExtra(EXTRA_MESSAGE, message);
        startActivityForResult(intent, TEXT_REQUEST);
    }

    @Override
    public void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);

        if (requestCode == TEXT_REQUEST) {
            if (resultCode == RESULT_OK) {
                String reply = data.getStringExtra(Two2Activity.EXTRA_REPLY);

                mReplyHeadTextView.setVisibility(View.VISIBLE);
                mReplyTextView.setText(reply);
                mReplyTextView.setVisibility(View.VISIBLE);
            }
        }
    }
}
```

> `Two2Activity.java`
```
package com.cipaapps;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class Two2Activity extends AppCompatActivity {

    public static final String EXTRA_REPLY ="com.example.android.Two2Activity.extra.REPLY";
    public static final String EXTRA_MESSAGE ="com.example.android.Two2Activity.extra.MESSAGE";
    private EditText mReply;

    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_two2activity);

        mReply = findViewById(R.id.editText_second);

        Intent intent = getIntent();
        String message = intent.getStringExtra(Two2Activity.EXTRA_MESSAGE);

        TextView textView = findViewById(R.id.text_message);
        textView.setText(message);
    }
    public void returnReply(View view){
        String reply = mReply.getText().toString();
        Intent replyIntent = new Intent();
        setResult(RESULT_OK, replyIntent);
        finish();
    }
}
```

**Code Project SetAlarm dan Maps**
> Pertama, buatlah ikon tombol terlebih dahulu pada `activity_main.xml`, bersama dengan ikon tombol aplikasi lainnya :

- `Set Alarm`
```
<androidx.cardview.widget.CardView
                android:id="@+id/cdMenu4"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">

                    <ImageView
                        android:id="@+id/imageView3"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/alarm__1_" />

                    <TextView
                        android:id="@+id/textView3"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Alarm"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>
        </LinearLayout>
```

- `Maps`
```
<androidx.cardview.widget.CardView
                android:id="@+id/cdMenu6"
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="10dp"
                android:layout_weight="1"
                app:cardCornerRadius="20dp"
                app:cardElevation="7dp">

                <LinearLayout
                    android:layout_width="match_parent"
                    android:layout_height="match_parent"
                    android:orientation="vertical">

                    <ImageView
                        android:id="@+id/imageView5"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:layout_margin="16dp"
                        android:layout_weight="1"
                        app:srcCompat="@drawable/gps" />

                    <TextView
                        android:id="@+id/textView5"
                        android:layout_width="match_parent"
                        android:layout_height="wrap_content"
                        android:fontFamily="serif"
                        android:text="Maps"
                        android:textAlignment="center"
                        android:textSize="18dp"
                        android:textStyle="bold" />
                </LinearLayout>
```

> Lalu tambahkan code Implicit Intent pada `MainActivity.java` :
- `SetAlarm`
```
findViewById(R.id.cdMenu4).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                setAlarm();
            }
        });
private void setAlarm() {
        Intent alarmIntent = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        // Add extra details for the alarm, e.g., alarm time, label, etc.
        // alarmIntent.putExtra(...
        startActivity(alarmIntent);
    }
```

- `Maps`
```
findViewById(R.id.cdMenu6).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Example location: Jakarta, Indonesia
                Uri geoLocation = Uri.parse("geo:-6.2088,106.8456");
                openMaps(geoLocation);
            }
        });
private void openMaps(Uri geoLocation) {
        Intent maps = new Intent(Intent.ACTION_VIEW);
        maps.setData(geoLocation);
        if (maps.resolveActivity(getPackageManager()) != null) {
            startActivity(maps);
        }
    }
```

> Selanjutnya buka `AndroidManifest.xml` dan tambahkan code untuk izin membuka Alarm :
```
<uses-permission android:name="com.android.alarm.permission.SET_ALARM" />
```

> Tambahkan code berikut pada bagian *application* agar set alarm dapat berjalan :
```
<activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.SET_ALARM" />
                <category android:name="android.intent.category.DEFAULT" />
                <action android:name="android.intent.action.VIEW" />
                <data android:scheme="geo" />
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity>
```



## Penjelasan & Hasil Program Tugas 3 

> Pada tugas 3 saya melakukan perubahan pada nama aplikasi, lalu gambar icon aplikasi dan juga pada splashscreen, untuk cara dan isi code nya sama seperti pada tugas 2 hanya menyesuaikan saja dengan yang baru.

**Fill in All The Code in This Project :**
> 1. ***Gradle Script*** => `build.gradle.kts (Module :app)`
```
plugins {
    id("com.android.application")
}

android {
    namespace = "com.cipaapps"
    compileSdk = 34

    defaultConfig {
        applicationId = "com.cipaapps"
        minSdk = 21
        targetSdk = 33
        versionCode = 1
        versionName = "1.0"

        testInstrumentationRunner = "androidx.test.runner.AndroidJUnitRunner"
    }

    buildTypes {
        release {
            isMinifyEnabled = false
            proguardFiles(getDefaultProguardFile("proguard-android-optimize.txt"), "proguard-rules.pro")
        }
    }
    compileOptions {
        sourceCompatibility = JavaVersion.VERSION_1_8
        targetCompatibility = JavaVersion.VERSION_1_8
    }
    buildToolsVersion = "34.0.0"
}

dependencies {
    val fragment_version = "1.6.1"
    implementation("androidx.appcompat:appcompat:1.6.1")
    implementation("com.google.android.material:material:1.10.0")
    implementation("androidx.constraintlayout:constraintlayout:2.1.4")
    testImplementation("junit:junit:4.13.2")
    androidTestImplementation("androidx.test.ext:junit:1.1.5")
    androidTestImplementation("androidx.test.espresso:espresso-core:3.5.1")
    implementation("androidx.fragment:fragment:$fragment_version")
}
```
- Setelah itu klik `Sync now`

> 2. ***AndroidManifest.xml***
- Lengkapi code ini pada `AndroidManifest.xml` yang sudah berisikan dengan code-code di project sebelumnya.
```
<activity android:name=".VideoPlayerActivity" />
```

> 3. ***Java***

=> Pada `MainActivity.java` saya melakukan penambahan code, yaitu isi code keseluruhannya adalah :
- `MainAcitivity.java`
```
package com.cipaapps;

import android.annotation.SuppressLint;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import androidx.appcompat.app.AppCompatActivity;


public class MainActivity extends AppCompatActivity {

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.cdMenu5).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                setAlarm();
            }
        });

        findViewById(R.id.cdMenu1).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolSatu ditekan, pindah ke HelloActivity
                Intent helloworld = new Intent(MainActivity.this, HelloActivity.class);
                startActivity(helloworld);
            }
        });

        findViewById(R.id.cdMenu2).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolDua ditekan, lakukan aksi yang diinginkan
                // Misalnya, pindah ke aktivitas lain atau jalankan fungsi khusus
                Intent toast = new Intent(MainActivity.this, CountActivity.class);
                startActivity(toast);
            }
        });

        findViewById(R.id.cdMenu3).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolDua ditekan, lakukan aksi yang diinginkan
                // Misalnya, pindah ke aktivitas lain atau jalankan fungsi khusus
                Intent sianida = new Intent(MainActivity.this, SianidaActivity.class);
                startActivity(sianida);
            }
        });

        findViewById(R.id.cdMenu4).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolDua ditekan, lakukan aksi yang diinginkan
                // Misalnya, pindah ke aktivitas lain atau jalankan fungsi khusus
                Intent twoactivity = new Intent(MainActivity.this, TwoActivity.class);
                startActivity(twoactivity);
            }
        });

        findViewById(R.id.cdMenu7).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Ketika tombolDua ditekan, lakukan aksi yang diinginkan
                // Misalnya, pindah ke aktivitas lain atau jalankan fungsi khusus
                Intent fragmentactivity = new Intent(MainActivity.this, FragmentActivity.class);
                startActivity(fragmentactivity);
            }
        });

        findViewById(R.id.cdMenu6).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Example location: Jakarta, Indonesia
                Uri geoLocation = Uri.parse("geo:-6.2088,106.8456");
                openMaps(geoLocation);
            }
        });
    }

    private void setAlarm() {
        Intent alarmIntent = new Intent(android.provider.AlarmClock.ACTION_SET_ALARM);
        // Add extra details for the alarm, e.g., alarm time, label, etc.
        // alarmIntent.putExtra(...
        startActivity(alarmIntent);
    }
    private void openMaps(Uri geoLocation) {
        Intent maps = new Intent(Intent.ACTION_VIEW);
        maps.setData(geoLocation);
        if (maps.resolveActivity(getPackageManager()) != null) {
            startActivity(maps);
        }
    }

}
```
> Note : Isi code pada keseluruhan tugas 3 ini tetap sama seperti pada isi code tugas 2 yaitu seperti *Java class* dan untuk *res/layout* hanya sedikit merubah design, pada tugas 3 ini saya hanya mencantumkan dan menjelaskan code-code yang ditambahkan untuk `Fragment` saja.


- Untuk package name bisa di sesuaikan dengan package name project kita masing-masing, disini saya melanjutkan dari package name project sebelumnya.

=> `FragmentActivity.java`
```
package com.cipaapps;

import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentManager;
import androidx.fragment.app.FragmentStatePagerAdapter;
import androidx.viewpager2.widget.ViewPager2;

import android.annotation.SuppressLint;
import android.content.Context;
import android.graphics.drawable.ColorDrawable;
import android.os.Bundle;

import com.google.android.material.tabs.TabLayout;

import java.util.Objects;

public class FragmentActivity extends AppCompatActivity {

    TabLayout tabLayout;
    ViewPager2 viewPager2;
    ViewAdapter adapter;

    @SuppressLint({"NewApi", "MissingInflatedId"})
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_movie);

        Objects.requireNonNull(getSupportActionBar()).setBackgroundDrawable(new ColorDrawable(getColor(R.color.cream)));

        tabLayout = findViewById(R.id.tab);
        viewPager2 = findViewById(R.id.view);
        adapter = new ViewAdapter(this);
        viewPager2.setAdapter(adapter);

        tabLayout.addOnTabSelectedListener(new TabLayout.OnTabSelectedListener() {
            @Override
            public void onTabSelected(TabLayout.Tab tab) {
                viewPager2.setCurrentItem(tab.getPosition());
            }

            @Override
            public void onTabUnselected(TabLayout.Tab tab) {

            }

            @Override
            public void onTabReselected(TabLayout.Tab tab) {

            }
        });

        class Halaman extends FragmentStatePagerAdapter {
            Context context;
            int jumlah_tab;

            Halaman(Context context, FragmentManager fm, int jml_tab)
            {
                super(fm);
                this.context=context;
                this.jumlah_tab=jml_tab;
            }

            @NonNull
            @Override
            public Fragment getItem(int posisition){
                switch (posisition){
                    case 0:return new ActionFragment();
                    case 1:return new ComedyFragment();
                    case 2:return new RomanceFragment();
                }
                return null;
            }

            @Override
            public int getCount(){
                return jumlah_tab;
            }
        }

        viewPager2.registerOnPageChangeCallback(new ViewPager2.OnPageChangeCallback() {
            @Override
            public void onPageSelected(int position) {
                super.onPageSelected(position);
                tabLayout.getTabAt(position).select();
            }
        });

    }
}
```
=> Membuat file fragment dengan cara klik kanan pada `MainActivity.java` lalu pilih dan klik fragment, setelah itu kita pilih dan klik fragment (Blank), setelah itu kita beri nama `ActionFragment`, `ComedyFragment`, `RomanceFragment`. Untuk file fragment sudah sekaligus dengan file layout xml nya (code berada pada bagian res `layout`)

- `ActionFragment.java` :
```
package com.cipaapps;

import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Button;
import android.widget.Toast;

import androidx.fragment.app.Fragment;


public class ActionFragment extends Fragment {

    private static final String TAG = "ActionFragment";

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        setHasOptionsMenu(true);
        View view = inflater.inflate(R.layout.fragment_action, container, false);

        // Find the button by its ID
        Button avengerButton = view.findViewById(R.id.avenger);
        Button myNameButton = view.findViewById(R.id.myname);
        Button spidermanButton = view.findViewById(R.id.spiderman);

        // Set click listener for each button
        avengerButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Log.d(TAG, "Avenger button clicked");
                playVideo(R.raw.avenger);
            }
        });

        myNameButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Log.d(TAG, "MyName button clicked");
                playVideo(R.raw.myname);
            }
        });

        spidermanButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Log.d(TAG, "Spiderman button clicked");
                playVideo(R.raw.spiderman);
            }
        });

        return view;
    }

    @Override
    public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
        inflater.inflate(R.menu.menu_tab, menu);
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        if (item.getItemId() == R.id.tab_action) {
            Toast.makeText(getActivity(), "Clicked on " + item.getTitle(), Toast.LENGTH_SHORT)
                    .show();
        }
        return true;
    }

    private void playVideo(int videoResource) {
        String videoPath = "android.resource://" + getActivity().getPackageName() + "/" + videoResource;
        Intent intent = new Intent(getActivity(), VideoPlayerActivity.class);
        intent.putExtra("VIDEO_PATH", videoPath);
        startActivity(intent);
    }
}
```
- `ComedyFragment.java` :
```
package com.cipaapps;

import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Button;
import android.widget.Toast;

import androidx.fragment.app.Fragment;


public class ComedyFragment extends Fragment {

    private static final String TAG = "ComedyFragment";

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        setHasOptionsMenu(true);
        View view = inflater.inflate(R.layout.fragment_comedy, container, false);

        // Find the button by its ID
        Button cektokosebelahButton = view.findViewById(R.id.cektokosebelah);
        Button friendzoneButton = view.findViewById(R.id.friendzone);
        Button hospitalplaylistButton = view.findViewById(R.id.hospitalplaylist);

        // Set click listener for each button
        cektokosebelahButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Log.d(TAG, "Cektokosebelah2 button clicked");
                playVideo(R.raw.cektokosebelah2);
            }
        });

        friendzoneButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Log.d(TAG, "Friendzone button clicked");
                playVideo(R.raw.friendzone);
            }
        });

        hospitalplaylistButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Log.d(TAG, "HospitalPlaylist button clicked");
                playVideo(R.raw.hospitalplaylist);
            }
        });

        return view;
    }

    @Override
    public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
        inflater.inflate(R.menu.menu_tab, menu);
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        if (item.getItemId() == R.id.tab_comedy) {
            Toast.makeText(getActivity(), "Clicked on " + item.getTitle(), Toast.LENGTH_SHORT)
                    .show();
        }
        return true;
    }

    private void playVideo(int videoResource) {
        String videoPath = "android.resource://" + getActivity().getPackageName() + "/" + videoResource;
        Intent intent = new Intent(getActivity(), VideoPlayerActivity.class);
        intent.putExtra("VIDEO_PATH", videoPath);
        startActivity(intent);
    }
}
```

- `RomanceFragment.java` :
```
package com.cipaapps;

import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.LayoutInflater;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Button;
import android.widget.Toast;

import androidx.fragment.app.Fragment;

import com.cipaapps.VideoPlayerActivity;


public class RomanceFragment extends Fragment {

    private static final String TAG = "RomanceFragment";

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container,
                             Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        setHasOptionsMenu(true);
        View view = inflater.inflate(R.layout.fragment_romance, container, false);

        // Find the button by its ID
        Button centurygirlButton = view.findViewById(R.id.centurygirl);
        Button cheerupButton = view.findViewById(R.id.cheerup);
        Button hiddenloveButton = view.findViewById(R.id.hiddenlove);

        // Set click listener for each button
        centurygirlButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Log.d(TAG, "Centurygirl button clicked");
                playVideo(R.raw.centurygirl);
            }
        });

        cheerupButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Log.d(TAG, "Cheerup button clicked");
                playVideo(R.raw.cheerup);
            }
        });

        hiddenloveButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Log.d(TAG, "Hiddenlove button clicked");
                playVideo(R.raw.hiddenlove);
            }
        });

        return view;
    }

    @Override
    public void onCreateOptionsMenu(Menu menu, MenuInflater inflater) {
        inflater.inflate(R.menu.menu_tab, menu);
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        if (item.getItemId() == R.id.tab_romance) {
            Toast.makeText(getActivity(), "Clicked on " + item.getTitle(), Toast.LENGTH_SHORT)
                    .show();
        }
        return true;
    }

    private void playVideo(int videoResource) {
        String videoPath = "android.resource://" + getActivity().getPackageName() + "/" + videoResource;
        Intent intent = new Intent(getActivity(), VideoPlayerActivity.class);
        intent.putExtra("VIDEO_PATH", videoPath);
        startActivity(intent);
    }
}
```

=> Lalu buat java class dengan nama `ViewAdapter.java`, yang berisi code :
```
package com.cipaapps;

import androidx.annotation.NonNull;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentActivity;
import androidx.viewpager2.adapter.FragmentStateAdapter;

public class ViewAdapter extends FragmentStateAdapter {
    public ViewAdapter(@NonNull FragmentActivity fragmentActivity) {
        super(fragmentActivity);
    }

    @NonNull
    @Override
    public Fragment createFragment(int position) {
        switch (position){
            case 0:
                return new ActionFragment();
            case 1:
                return new ComedyFragment();
            case 2:
                return new RomanceFragment();
            default:
                return new ActionFragment();
        }
    }

    @Override
    public int getItemCount() {
        return 3;
    }
}
```

=> Setelah itu membuat java class untuk memutar video dengan nama `VideoPlayerActivity.java`, yang berisi code :
```
package com.cipaapps;

import android.content.pm.ActivityInfo;
import android.net.Uri;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.view.ViewGroup;
import android.widget.MediaController;
import android.widget.RelativeLayout;
import android.widget.VideoView;

import androidx.annotation.NonNull;
import androidx.annotation.Nullable;
import androidx.appcompat.app.AppCompatActivity;


public class VideoPlayerActivity extends AppCompatActivity {

    private VideoView videoView; // Deklarasi VideoView sebagai variabel global
    private int originalOrientation;

    @Override
    protected void onCreate(@Nullable Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_video_player);

        // Get the video URI from the intent
        String videoPath = getIntent().getStringExtra("VIDEO_PATH");
        Uri uri = Uri.parse(videoPath);

        // Set up VideoView
        videoView = findViewById(R.id.videoView); // Inisialisasi variabel videoView
        videoView.setVideoURI(uri);

        // Set up MediaController
        MediaController mediaController = new MediaController(this);
        mediaController.setAnchorView(videoView);
        videoView.setMediaController(mediaController);

        // Start playing the video
        videoView.start();

        // Get the original orientation
        originalOrientation = getResources().getConfiguration().orientation;

        // Adjust video layout based on the original orientation
        adjustVideoLayout(originalOrientation);
    }

    @Override
    protected void onResume() {
        super.onResume();
        // Detect orientation changes and adjust VideoView layout
        int currentOrientation = getResources().getConfiguration().orientation;
        if (currentOrientation != originalOrientation) {
            adjustVideoLayout(currentOrientation);
            originalOrientation = currentOrientation;
        }
    }

    private void adjustVideoLayout(int orientation) {
        if (orientation == ActivityInfo.SCREEN_ORIENTATION_LANDSCAPE ||
                orientation == ActivityInfo.SCREEN_ORIENTATION_REVERSE_LANDSCAPE) {
            // Landscape mode
            setFullscreen(true);
        } else {
            // Portrait or other orientations
            setFullscreen(false);
        }
    }

    private void setFullscreen(boolean fullscreen) {
        if (fullscreen) {
            // Hide action bar
            if (getSupportActionBar() != null) {
                getSupportActionBar().hide();
            }

            // Set VideoView layout parameters for fullscreen
            RelativeLayout.LayoutParams params = new RelativeLayout.LayoutParams(
                    ViewGroup.LayoutParams.MATCH_PARENT,
                    ViewGroup.LayoutParams.MATCH_PARENT
            );
            params.addRule(RelativeLayout.CENTER_IN_PARENT);
            videoView.setLayoutParams(params);

            // Hide navigation bar and status bar
            getWindow().getDecorView().setSystemUiVisibility(
                    View.SYSTEM_UI_FLAG_FULLSCREEN |
                            View.SYSTEM_UI_FLAG_HIDE_NAVIGATION |
                            View.SYSTEM_UI_FLAG_IMMERSIVE_STICKY);
        } else {
            // Show action bar
            if (getSupportActionBar() != null) {
                getSupportActionBar().show();
            }

            // Set VideoView layout parameters for normal mode
            RelativeLayout.LayoutParams params = new RelativeLayout.LayoutParams(
                    ViewGroup.LayoutParams.MATCH_PARENT,
                    ViewGroup.LayoutParams.WRAP_CONTENT
            );
            params.addRule(RelativeLayout.CENTER_IN_PARENT);
            videoView.setLayoutParams(params);

            // Show navigation bar and status bar
            getWindow().getDecorView().setSystemUiVisibility(
                    View.SYSTEM_UI_FLAG_VISIBLE);
        }
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.menu_video_player, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        if (item.getItemId() == R.id.action_back) {
            // Tambahkan logika untuk kembali ke halaman sebelumnya atau finish activity
            finish();
            return true;
        }
        return super.onOptionsItemSelected(item);
    }
}
```


> 4. ***res***

=> Pada bagian `Drawable` saya menambahkan *Drawable Resource File* dengan nama `bg_cardview.xml`, yang berisikan code :
```
<!-- cardview_pressed_effect.xml -->
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:state_pressed="true">
        <shape android:shape="rectangle">
            <!-- Ganti warna latar belakang yang diinginkan saat CardView ditekan -->
            <solid android:color="#F6F7F9" />
            <corners android:radius="20dp"/>
        </shape>
    </item>
    <item>
        <!-- Warna latar belakang default saat tidak ditekan -->
        <shape android:shape="rectangle">
            <solid android:color="#008BD7EE" />\

        </shape>
    </item>
</selector>
```

=> `values`

- `colors.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="birumuda">#95AFD5</color>
    <color name="salem">#F8C6E6</color>
    <color name ="purple">#E3A2ED</color>
    <color name="hijau">#87986D</color>
    <color name="biru">#788A99</color>
    <color name="hijaumuda">#C2E69C</color>
    <color name="kuning">#FFEB3B</color>
    <color name="orange">#FF9800</color>
    <color name="cream">#E6C18A</color>
    <color name="hijautua">#3F4A2F</color>
    <color name="hijausoft">#9FC17C</color>
    <color name="coklat">#574545</color>
    <color name="choco">#A69E9E</color>
</resources>
```

=> `strings.xml` (tambahkan code strings.xml dibawah ini dengan code strings.xml pada project sebelumnya yaitu tugas 2) :
```
<resources>
 <string name="app_name">SerendipityApps</string>
    <!-- TODO: Remove or change this placeholder text -->
<string name="hello_blank_fragment">Hello blank fragment</string>
</resources>
```
=> `themes`

- `themes.xml` dan `themes.xml(night)` (sama isi code nya) :
```
<resources xmlns:tools="http://schemas.android.com/tools">
    <!-- Base application theme. -->
    <style name="SplashScreen" parent="Theme.MaterialComponents.DayNight.NoActionBar">
        <item name="android:windowBackground">@drawable/splashscreenapp</item>
        <item name="android:statusBarColor">?attr/colorOnPrimary</item>
    </style>

    <!-- Base application theme. -->
    <style name="Base.Theme.TabExperiment" parent="Theme.MaterialComponents.DayNight.DarkActionBar">
        <!-- Primary brand color. -->
        <item name="colorPrimary">@color/colorPrimary</item>
        <item name="colorPrimaryVariant">@color/cream</item>
        <item name="colorOnPrimary">@color/white</item>
        <!-- Secondary brand color. -->
        <item name="colorSecondary">@color/hijau</item>
        <item name="colorSecondaryVariant">@color/hijaumuda</item>
        <item name="colorOnSecondary">@color/black</item>
        <!-- Status bar color. -->
        <item name="android:statusBarColor">@color/choco</item>
        <item name="android:navigationBarColor">@color/choco</item>
        <!-- Customize your light theme here. -->
    </style>

    <style name="Theme.TabExperiment" parent="Base.Theme.TabExperiment" />
</resources>
```

=> Untuk menambahkan video pada Android Studio disini saya memakai `res/raw/video_kita.mp4`, yaitu caranya yang pertama kita klik kanan terlebih dahulu di bagian `res` lalu kita pilih dan klik `new` lalu pilih dan klik bagian `Android Resource Directory`, setelah itu ada bagian    `Resource type` kita pilih `raw` lalu kita klik OK. Lalu setelah itu langsung saja kita copy paste video yang kita ingin masukkan ke dalam project kita ke dalam `raw`.

=> `layout`

=> Pada `activity_main.xml` saya melakukan penambahan dan perubahan code untuk design nya, yaitu isi code keseluruhannya adalah :
- `activity_main.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<ScrollView
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg_menu"
    tools:context=".MainActivity">

    <RelativeLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content">

        <TextView
            android:id="@+id/title_view"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_centerHorizontal="true"
            android:text="Menu Program"
            android:fontFamily="serif"
            android:textColor="@color/black"
            android:textStyle="bold"
            android:textSize="35sp"
            android:layout_marginTop="35dp"/>

        <GridLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:layout_below="@+id/title_view"
            android:layout_marginStart="35dp"
            android:layout_marginTop="45dp"
            android:layout_marginEnd="40dp"
            android:layout_marginBottom="35dp"
            android:columnCount="10"
            android:rowCount="10">

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu1"
                android:layout_width="80dp"
                android:layout_height="100dp"
                android:layout_row="0"
                android:layout_rowWeight="1"
                android:layout_column="0"
                android:layout_columnWeight="1"
                android:layout_gravity="fill"
                android:layout_margin="8dp"
                app:cardCornerRadius="8dp"
                app:cardElevation="8dp">

                <LinearLayout
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical|center_horizontal"
                    android:gravity="center"
                    android:orientation="vertical">

                    <ImageView
                        android:layout_width="50dp"
                        android:layout_height="50dp"
                        android:src="@drawable/worldwide" />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:layout_marginTop="10dp"
                        android:fontFamily="sans-serif"
                        android:text="HELLO WORLD!"
                        android:textAlignment="center"
                        android:textColor="@color/black"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu2"
                android:layout_width="80dp"
                android:layout_height="100dp"
                android:layout_row="0"
                android:layout_rowWeight="1"
                android:layout_column="1"
                android:layout_columnWeight="1"
                android:layout_gravity="fill"
                android:layout_margin="8dp"
                app:cardCornerRadius="8dp"
                app:cardElevation="8dp">

                <LinearLayout
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical|center_horizontal"
                    android:gravity="center"
                    android:orientation="vertical">

                    <ImageView
                        android:layout_width="50dp"
                        android:layout_height="50dp"
                        android:src="@drawable/mathematics_symbols" />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:layout_marginTop="10dp"
                        android:fontFamily="serif"
                        android:text="FIBONACCI"
                        android:textAlignment="center"
                        android:textColor="@color/black"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu3"
                android:layout_width="80dp"
                android:layout_height="100dp"
                android:layout_row="1"
                android:layout_rowWeight="1"
                android:layout_column="0"
                android:layout_columnWeight="1"
                android:layout_gravity="fill"
                android:layout_margin="8dp"
                app:cardCornerRadius="8dp"
                app:cardElevation="8dp">

                <LinearLayout
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical|center_horizontal"
                    android:gravity="center"
                    android:orientation="vertical">

                    <ImageView
                        android:layout_width="50dp"
                        android:layout_height="50dp"
                        android:src="@drawable/script" />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:layout_marginTop="10dp"
                        android:fontFamily="serif"
                        android:text="ICE COLD!"
                        android:textAlignment="center"
                        android:textColor="@color/black"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu4"
                android:layout_width="80dp"
                android:layout_height="100dp"
                android:layout_row="1"
                android:layout_rowWeight="1"
                android:layout_column="1"
                android:layout_columnWeight="1"
                android:layout_gravity="fill"
                android:layout_margin="8dp"
                app:cardCornerRadius="8dp"
                app:cardElevation="8dp">

                <LinearLayout
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical|center_horizontal"
                    android:gravity="center"
                    android:orientation="vertical">

                    <ImageView
                        android:layout_width="50dp"
                        android:layout_height="50dp"
                        android:src="@drawable/messaging" />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:layout_marginTop="10dp"
                        android:fontFamily="serif"
                        android:text="TWO ACTIVITY"
                        android:textAlignment="center"
                        android:textColor="@color/black"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu5"
                android:layout_width="80dp"
                android:layout_height="100dp"
                android:layout_row="2"
                android:layout_rowWeight="1"
                android:layout_column="0"
                android:layout_columnWeight="1"
                android:layout_gravity="fill"
                android:layout_margin="8dp"
                app:cardCornerRadius="8dp"
                app:cardElevation="8dp">

                <LinearLayout
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical|center_horizontal"
                    android:gravity="center"
                    android:orientation="vertical">

                    <ImageView
                        android:layout_width="50dp"
                        android:layout_height="50dp"
                        android:src="@drawable/alarm__1_" />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:layout_marginTop="10dp"
                        android:fontFamily="serif"
                        android:text="ALARM"
                        android:textAlignment="center"
                        android:textColor="@color/black"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu6"
                android:layout_width="80dp"
                android:layout_height="100dp"
                android:layout_row="2"
                android:layout_rowWeight="1"
                android:layout_column="1"
                android:layout_columnWeight="1"
                android:layout_gravity="fill"
                android:layout_margin="8dp"
                app:cardCornerRadius="8dp"
                app:cardElevation="8dp">

                <LinearLayout
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical|center_horizontal"
                    android:gravity="center"
                    android:orientation="vertical">

                    <ImageView
                        android:layout_width="50dp"
                        android:layout_height="50dp"
                        android:src="@drawable/gps" />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:layout_marginTop="10dp"
                        android:fontFamily="serif"
                        android:text="G-MAPS"
                        android:textAlignment="center"
                        android:textColor="@color/black"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu7"
                android:layout_width="80dp"
                android:layout_height="100dp"
                android:layout_row="3"
                android:layout_rowWeight="1"
                android:layout_column="0"
                android:layout_columnWeight="1"
                android:layout_gravity="fill"
                android:layout_margin="8dp"
                app:cardCornerRadius="8dp"
                app:cardElevation="8dp">

                <LinearLayout
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical|center_horizontal"
                    android:gravity="center"
                    android:orientation="vertical">

                    <ImageView
                        android:layout_width="50dp"
                        android:layout_height="50dp"
                        android:src="@drawable/movies" />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:layout_marginTop="10dp"
                        android:fontFamily="serif"
                        android:text="MOVIES"
                        android:textAlignment="center"
                        android:textColor="@color/black"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu8"
                android:layout_width="80dp"
                android:layout_height="100dp"
                android:layout_row="3"
                android:layout_rowWeight="1"
                android:layout_column="1"
                android:layout_columnWeight="1"
                android:layout_gravity="fill"
                android:layout_margin="8dp"
                app:cardCornerRadius="8dp"
                app:cardElevation="8dp">

                <LinearLayout
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical|center_horizontal"
                    android:gravity="center"
                    android:orientation="vertical">

                    <ImageView
                        android:layout_width="50dp"
                        android:layout_height="50dp"
                        android:src="@drawable/serendipityapps" />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:layout_marginTop="10dp"
                        android:fontFamily="serif"
                        android:text="EMPTY"
                        android:textAlignment="center"
                        android:textColor="@color/black"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu9"
                android:layout_width="80dp"
                android:layout_height="100dp"
                android:layout_row="4"
                android:layout_rowWeight="1"
                android:layout_column="0"
                android:layout_columnWeight="1"
                android:layout_gravity="fill"
                android:layout_margin="8dp"
                app:cardCornerRadius="8dp"
                app:cardElevation="8dp">

                <LinearLayout
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical|center_horizontal"
                    android:gravity="center"
                    android:orientation="vertical">

                    <ImageView
                        android:layout_width="50dp"
                        android:layout_height="50dp"
                        android:src="@drawable/serendipityapps" />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:layout_marginTop="10dp"
                        android:fontFamily="serif"
                        android:text="EMPTY"
                        android:textAlignment="center"
                        android:textColor="@color/black"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

            <androidx.cardview.widget.CardView
                android:id="@+id/cdMenu10"
                android:layout_width="80dp"
                android:layout_height="100dp"
                android:layout_row="4"
                android:layout_rowWeight="1"
                android:layout_column="1"
                android:layout_columnWeight="1"
                android:layout_gravity="fill"
                android:layout_margin="8dp"
                app:cardCornerRadius="8dp"
                app:cardElevation="8dp">

                <LinearLayout
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    android:layout_gravity="center_vertical|center_horizontal"
                    android:gravity="center"
                    android:orientation="vertical">

                    <ImageView
                        android:layout_width="50dp"
                        android:layout_height="50dp"
                        android:src="@drawable/serendipityapps" />

                    <TextView
                        android:layout_width="wrap_content"
                        android:layout_height="wrap_content"
                        android:layout_marginTop="10dp"
                        android:fontFamily="serif"
                        android:text="EMPTY"
                        android:textAlignment="center"
                        android:textColor="@color/black"
                        android:textStyle="bold" />
                </LinearLayout>
            </androidx.cardview.widget.CardView>

        </GridLayout>

        <TextView
            android:id="@+id/bottom_text"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginBottom="35dp"
            android:layout_alignParentBottom="true"
            android:layout_centerHorizontal="true"
            android:fontFamily="monospace"
            android:text="© 2024 Syifa Aurellia"
            android:textColor="@color/black"
            android:textSize="15sp"
            android:textStyle="bold" />

    </RelativeLayout>

</ScrollView>
```

- `activity_movie.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/white"
    tools:context=".FragmentActivity">


    <com.google.android.material.tabs.TabLayout
        android:id="@+id/tab"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@color/choco"
        app:tabSelectedTextColor="@color/white"
        app:tabIndicatorColor="@color/white"
        tools:layout_editor_absoluteX="1dp"
        tools:layout_editor_absoluteY="3dp"
        tools:ignore="MissingConstraints">

        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Action"
            tools:layout_editor_absoluteX="0dp"
            tools:layout_editor_absoluteY="3dp" />

        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Comedy" />

        <com.google.android.material.tabs.TabItem
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Romance" />
    </com.google.android.material.tabs.TabLayout>

    <androidx.viewpager2.widget.ViewPager2
        android:id="@+id/view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_marginTop="50dp"
        android:background="@color/white"
        tools:layout_editor_absoluteX="1dp"
        tools:layout_editor_absoluteY="52dp" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

- `activity_video_player.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <VideoView
        android:id="@+id/videoView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>
</RelativeLayout>
```

- `fragment_action.xml` :
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    xmlns:tools="http://schemas.android.com/tools"
    android:padding="25dp"
    tools:context=".ActionFragment">

    <ImageView
        android:id="@+id/imgMovie"
        android:layout_width="150dp"
        android:layout_height="170dp"
        android:src="@drawable/film1"/>

    <TextView
        android:id="@+id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_marginStart="16dp"
        android:textSize="16sp"
        android:textColor="@color/black"
        android:text="AVENGERS : END GAME"/>

    <TextView
        android:id="@+id/Deskription"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginTop="10dp"
        android:maxLines="5"
        android:textColor="@color/black"
        android:text="The story of the Avengers efforts to restore parts of the universe that were destroyed after the events of Infinity War. Using time travel technology, they attempt to steal the Infinity Stones to overcome the destruction caused by Thanos. An epic battle takes place, culminating in a great sacrifice and victory that changes the fate of the universe."/>


    <Button
        android:id="@+id/avenger"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/Deskription"
        android:text="Watch Trailer Now"
        android:onClick="playAvengerTrailer"/>


    <ImageView
        android:id="@+id/imgMovie2"
        android:layout_width="150dp"
        android:layout_height="170dp"
        android:layout_marginTop="200dp"
        android:src="@drawable/film4"/>

    <TextView
        android:id="@+id/tvTitle2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/imgMovie2"
        android:layout_marginStart="16dp"
        android:layout_marginTop="200dp"
        android:textSize="16sp"
        android:textColor="@color/black"
        android:text="MY NAME"/>

    <TextView
        android:id="@+id/Deskription2"
        android:layout_toRightOf="@id/imgMovie2"
        android:layout_below="@id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginTop="210dp"
        android:maxLines="5"
        android:textColor="@color/black"
        android:text="The story of Yoon Ji-woo, a woman who disguises herself as a member of a criminal gang to investigate her father's death. On his journey to find the truth, Ji-woo becomes involved in conflicts and dark secrets that lead to a battle between justice and ambition in the criminal world. This story shows Ji-woo's struggle to understand his identity while avenging his family, bringing a sense of tension and intrigue to each episode."/>

    <Button
        android:id="@+id/myname"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_toRightOf="@id/imgMovie2"
        android:layout_below="@id/Deskription2"
        android:text="Watch Trailer Now"
        android:onClick="playMyNameTrailer"/>

    <ImageView
        android:id="@+id/imgMovie3"
        android:layout_width="150dp"
        android:layout_height="170dp"
        android:layout_marginTop="400dp"
        android:src="@drawable/film5"/>

    <TextView
        android:id="@+id/tvTitle3"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/imgMovie3"
        android:layout_marginStart="16dp"
        android:layout_marginTop="400dp"
        android:textSize="16sp"
        android:textColor="@color/black"
        android:text="SPIDERMAN : NO WAY HOME"/>

    <TextView
        android:id="@+id/Deskription3"
        android:layout_toRightOf="@id/imgMovie3"
        android:layout_below="@id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginTop="420dp"
        android:maxLines="5"
        android:textColor="@color/black"
        android:text="Peter Parker tries to fix the mess after his Spider-Man identity is revealed and his personal life is threatened. Peter enlists the help of Doctor Strange to use magic gone wrong, opening the multiverse and bringing forth a version of Spider-Man from a parallel reality. Along with the other Spider-Men, Peter confronts villains from the past and faces serious consequences in their efforts to right those wrongs."
        />

    <Button
        android:id="@+id/spiderman"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_toRightOf="@id/imgMovie3"
        android:layout_below="@id/Deskription3"
        android:text="Watch Trailer Now"
        android:onClick="playSpidermanTrailer" />
</RelativeLayout>
```

- `fragment_comedy.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:padding="25dp">

    <ImageView
        android:id="@+id/imgMovie"
        android:layout_width="150dp"
        android:layout_height="170dp"
        android:src="@drawable/film2"/>

    <TextView
        android:id="@+id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_marginStart="16dp"
        android:textSize="16sp"
        android:textColor="@color/black"
        android:text="CEK TOKO SEBELAH 2"/>

    <TextView
        android:id="@+id/Deskription"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginTop="10dp"
        android:maxLines="5"
        android:textColor="@color/black"
        android:text="The film Cek Toko Sebelah 2 continues the story of the Soleh family and their humorous conflict when they discover that the shop next door to them is about to be renovated into a hipster cafe. In his efforts to maintain a traditional shop, Soleh must face the challenges of modernization while maintaining family relationships. With a distinctive comedy flavor, this film depicts changing times and family values in a light and entertaining atmosphere."
        />

    <Button
        android:id="@+id/cektokosebelah"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/Deskription"
        android:text="Watch Trailer Now"
        android:onClick="playCektokosebelah2Trailer"/>

    <ImageView
        android:id="@+id/imgMovie2"
        android:layout_width="150dp"
        android:layout_height="170dp"
        android:layout_marginTop="200dp"
        android:src="@drawable/film6"/>

    <TextView
        android:id="@+id/tvTitle2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_marginStart="16dp"
        android:layout_marginTop="200dp"
        android:textSize="16sp"
        android:textColor="@color/black"
        android:text="FRIENDZONE"/>

    <TextView
        android:id="@+id/Deskription2"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginTop="210dp"
        android:maxLines="5"
        android:textColor="@color/black"
        android:text="The story centers on old friends, Palm and Gink, who love each other but are afraid to express their feelings. The two had a close relationship, but when Palm confessed her feelings, Gink stated that she only saw him as a friend. The film presents Palm's emotional journey in maintaining their friendship, touching on themes of unrequited love and the complexity of sibling relationships."
        />

    <Button
        android:id="@+id/friendzone"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/Deskription2"
        android:text="Watch Trailer Now"
        android:onClick="playFriendzoneTrailer"/>

    <ImageView
        android:id="@+id/imgMovie3"
        android:layout_width="150dp"
        android:layout_height="170dp"
        android:layout_marginTop="400dp"
        android:src="@drawable/film7"/>

    <TextView
        android:id="@+id/tvTitle3"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_marginStart="16dp"
        android:layout_marginTop="400dp"
        android:textSize="16sp"
        android:textColor="@color/black"
        android:text="HOSPITAL PLAYLIST"/>

    <TextView
        android:id="@+id/Deskription3"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginTop="410dp"
        android:maxLines="5"
        android:textColor="@color/black"
        android:text="The Korean drama Hospital Playlist tells the story of five doctors who are friends and work together in the same hospital. They not only lead busy professional lives in the medical world, but also overcome challenges and joys in their personal lives. With warm humor and depth of character, the series provides an emotional and realistic portrait of friendship, love, and life in a hospital." />

    <Button
        android:id="@+id/hospitalplaylist"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/Deskription3"
        android:text="Watch Trailer Now"
        android:onClick="playHospitalPlaylistTrailer"/>
</RelativeLayout>
```

- `fragment_romance.xml`
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:padding="25dp">

    <ImageView
        android:id="@+id/imgMovie"
        android:layout_width="150dp"
        android:layout_height="170dp"
        android:src="@drawable/film3"/>

    <TextView
        android:id="@+id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginLeft="16dp"
        android:layout_toRightOf="@id/imgMovie"
        android:text="20TH CENTURY GIRL"
        android:textColor="@color/black"
        android:textSize="16sp" />

    <TextView
        android:id="@+id/Deskription"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/tvTitle"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginStart="16dp"
        android:layout_marginTop="10dp"
        android:maxLines="5"
        android:textColor="@color/black"
        android:text="Tells the story of Na Bo-ra, a student who vows to follow Baek Hyun-jin for the sake of her sick friend. However, Bo-ra falls in love with Poong Woon-ho, Hyun-jin's best friend. In the confusion of the love triangle, Bo-ra hides her feelings so as not to hurt her best friend who turns out to love Woon-ho. When Woon-ho returns to New Zealand, Bo-ra and Yeon-du arrive at the train station at the right time, allowing them to confess their feelings before going their separate ways. However, Woon-ho suddenly disappears from Bo-ra's life, leaving her heart broken.

Over time, Bo-ra enters university and lives an adult life. In 2019, he received an art exhibition invitation from Joseph, Woon-ho's younger brother. Here, Bo-ra learns that Woon-ho died in an accident years ago. Joseph thanks Bo-ra for remembering his brother and reveals that Woon-ho's happiest moments were with Bo-ra. While watching the video Woon-ho made, Bo-ra reflects on the happy memories they shared.

Set in 1999 and 2019, it takes the audience on Bo-ra's emotional journey full of confusion, love, friendship and loss. This film depicts the complexity of human relationships over time, with a story that touches the heart and leaves a deep impression." />

    <Button
        android:id="@+id/centurygirl"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/Deskription"
        android:text="Watch Trailer Now"
        android:onClick="playCenturygirlTrailer"/>

    <ImageView
        android:id="@+id/imgMovie2"
        android:layout_width="150dp"
        android:layout_height="170dp"
        android:layout_marginTop="200dp"
        android:src="@drawable/film8"/>

    <TextView
        android:id="@+id/tvTitle2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_marginStart="16dp"
        android:layout_marginTop="200dp"
        android:textSize="16sp"
        android:textColor="@color/black"
        android:text="CHEER UP"/>

    <TextView
        android:id="@+id/Deskription2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/tvTitle"
        android:layout_marginStart="16dp"
        android:layout_marginLeft="12dp"
        android:layout_marginTop="210dp"
        android:layout_toRightOf="@id/imgMovie"
        android:maxLines="5"
        android:textColor="@color/black"
        android:text="Tells the story of a group of high school students who band together to form a cheerleading team at their school, trying to overcome academic pressure and teenage problems. With the struggles, conflicts, and friendships that develop among the team members, they learn to overcome life's difficulties and find strength in their unity. This story presents the dynamics of school life full of enthusiasm, with a touch of comedy and warmth in experiencing adolescence." />

    <Button
        android:id="@+id/cheerup"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/Deskription2"
        android:text="Watch Trailer Now"
        android:onClick="playCheerupTrailer"/>

    <ImageView
        android:id="@+id/imgMovie3"
        android:layout_width="150dp"
        android:layout_height="175dp"
        android:layout_marginTop="400dp"
        android:src="@drawable/film9"/>

    <TextView
        android:id="@+id/tvTitle3"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_marginStart="16dp"
        android:layout_marginTop="400dp"
        android:textSize="16sp"
        android:textColor="@color/black"
        android:text="HIDDEN LOVE"/>

    <TextView
        android:id="@+id/Deskription3"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/tvTitle"
        android:layout_marginStart="16dp"
        android:layout_marginLeft="16dp"
        android:layout_marginTop="410dp"
        android:layout_toRightOf="@id/imgMovie"
        android:maxLines="5"
        android:textColor="@color/black"
        android:text="The storyline is about the complicated relationships among a group of close friends who grow up together and face various life trials. With secrets and conflicts emerging, they must struggle to understand and accept each other, while going on a journey to find love and identity. Through a story full of intrigue and emotion, Hidden Love reveals hidden layers of relationships and shows the journey towards maturity and understanding." />

    <Button
        android:id="@+id/hiddenlove"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="10dp"
        android:layout_toRightOf="@id/imgMovie"
        android:layout_below="@id/Deskription3"
        android:text="Watch Trailer Now"
        android:onClick="playHiddenloveTrailer"/>
</RelativeLayout>
```
=> Pada directory `drawable` kita bisa tambahkan gambar seperti poster film yang ingin kita tampilkan, dan jangan lupa untuk menambahkan icon `baseline_more_vert_24.xml` dengan cara klik kanan pada `drawable` lalu klik New, setelah itu kita pilih dan klik Vector Asset. Setelah itu kita klik clip art lalu kita pilih icon nya, jika sudah ketemu kita klik OK lalu kita klik next. Sama halnya ketika kita ingin menambahkan menu kembali pada halaman `VideoPlayerActivity` yaitu dengan langkah-langkah yang sama seperti sebelumnya dan jangan lupa untuk menambahkan icon `baseline_arrorw_circle_left_24.xml` lalu klik OK dan kita klik next.

=> Selanjutnya kita klik kanan pada `res` lalu pilih dan klik `Android Resource Directory` setelah itu kita beri nama "menu" lalu klik OK. Setelah itu kita buat Menu Resource File dengan nama `menu_tab.xml` lalu isi dengan code :
```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:tools="http://schemas.android.com/tools"
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">
    <item
        android:id="@+id/tab_action"
        android:icon="@drawable/baseline_more_vert_24"
        android:title="Action"/>

    <item
        android:id="@+id/tab_comedy"
        android:icon="@drawable/baseline_more_vert_24"
        android:title="Comedy"/>

    <item
        android:id="@+id/tab_romance"
        android:icon="@drawable/baseline_more_vert_24"
        android:title="Romance"/>
</menu>
```

=> Sama halnya ketika ingin menambahkan code menu untuk kembali, dengan cara kita klik kanan pada directory `menu` dan buat Menu Resource File dengan nama `menu_video_player.xml` lalu isi dengan code :
```
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:id="@+id/action_back"
        android:icon="@drawable/baseline_arrow_circle_left_24"
        android:title="Back"
        app:showAsAction="always" />
</menu>
```

> **Hasil Program Tugas 3 :**

![Screenshot_2024-01-15-14-53-31-029_com zmiiabyv21 1](https://github.com/MohAzmii04/zmiiaby.v2.1_UAS_Pemograman-Mobile/assets/115864496/88a983dc-81d5-44d3-bae4-35fa11736675)


#Demo Tugass



https://github.com/MohAzmii04/zmiiaby.v2.1_UAS_Pemograman-Mobile/assets/115864496/eb9d7dbc-77e5-4a30-ab1d-08ac74fec78c



## Semoga Bermanfaat, Terima Kasih 
