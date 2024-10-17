# Workshop-01 Develop an android application to pass the data between the activities using Intent.

## AIM:
Develop an android application pass the data between the activities using Intent.

## EQUIPMENTS REQUIRED:
Android Studio(Latest Version)


## PROGRAM:
/*
Program to pass the data between the activities using Intent.
Developed by: Priya R
Registeration Number : 212222040124
*/

### activity_main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/inputName"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="20dp"
        android:layout_marginTop="50dp"
        android:layout_marginEnd="20dp"
        android:autofillHints=""
        android:hint="@string/enter_name"
        android:inputType="text"
        android:minHeight="48dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="VisualLintTextFieldSize" />

    <EditText
        android:id="@+id/inputAge"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="20dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="20dp"
        android:autofillHints=""
        android:hint="@string/enter_age"
        android:inputType="number"
        android:minHeight="48dp"
        android:textColorHint="#546E7A"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/inputName"
        tools:ignore="VisualLintTextFieldSize" />

    <EditText
        android:id="@+id/inputEmail"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="20dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="20dp"
        android:autofillHints=""
        android:hint="@string/enter_email"
        android:inputType="textEmailAddress"
        android:minHeight="48dp"
        android:textColorHint="#546E7A"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/inputAge"
        tools:ignore="VisualLintTextFieldSize" />

    <EditText
        android:id="@+id/inputContact"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginStart="20dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="20dp"
        android:autofillHints=""
        android:hint="@string/enter_contact_number"
        android:inputType="phone"
        android:minHeight="48dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/inputEmail"
        tools:ignore="HardcodedText,TextContrastCheck,VisualLintTextFieldSize" />

    <Button
        android:id="@+id/submitBtn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/submit"
        app:layout_constraintTop_toBottomOf="@+id/inputContact"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="30dp" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### MainActivity.java
```
package com.example.workshop_1;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    EditText inputName, inputAge, inputEmail, inputContact;
    Button submitBtn;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        inputName = findViewById(R.id.inputName);
        inputAge = findViewById(R.id.inputAge);
        inputEmail = findViewById(R.id.inputEmail);
        inputContact = findViewById(R.id.inputContact);
        submitBtn = findViewById(R.id.submitBtn);

        submitBtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                // Get the input values
                String name = inputName.getText().toString();
                String age = inputAge.getText().toString();
                String email = inputEmail.getText().toString();
                String contact = inputContact.getText().toString();

                // Create an Intent to pass the data
                Intent intent = new Intent(MainActivity.this, DisplayActivity.class);
                intent.putExtra("USER_NAME", name);
                intent.putExtra("USER_AGE", age);
                intent.putExtra("USER_EMAIL", email);
                intent.putExtra("USER_CONTACT", contact);

                // Start the DisplayActivity
                startActivity(intent);
            }
        });
    }
}
```

### activity_display.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".DisplayActivity">

    <TextView
        android:id="@+id/displayName"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Name: "
        android:textSize="18sp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="50dp"
        android:layout_marginStart="20dp"
        android:layout_marginEnd="20dp" />

    <TextView
        android:id="@+id/displayAge"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Age: "
        android:textSize="18sp"
        app:layout_constraintTop_toBottomOf="@+id/displayName"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="20dp"
        android:layout_marginStart="20dp"
        android:layout_marginEnd="20dp" />

    <TextView
        android:id="@+id/displayEmail"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Email: "
        android:textSize="18sp"
        app:layout_constraintTop_toBottomOf="@+id/displayAge"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="20dp"
        android:layout_marginStart="20dp"
        android:layout_marginEnd="20dp" />

    <TextView
        android:id="@+id/displayContact"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="Contact: "
        android:textSize="18sp"
        app:layout_constraintTop_toBottomOf="@+id/displayEmail"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="20dp"
        android:layout_marginStart="20dp"
        android:layout_marginEnd="20dp" />

</androidx.constraintlayout.widget.ConstraintLayout>

```

### DisplayActivity.java:
```
package com.example.workshop_1;

import androidx.appcompat.app.AppCompatActivity;
import android.annotation.SuppressLint;
import android.os.Bundle;
import android.widget.TextView;

public class DisplayActivity extends AppCompatActivity {

    TextView displayName, displayAge, displayEmail, displayContact;

    @SuppressLint("SetTextI18n")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_display);

        // Find TextViews
        displayName = findViewById(R.id.displayName);
        displayAge = findViewById(R.id.displayAge);
        displayEmail = findViewById(R.id.displayEmail);
        displayContact = findViewById(R.id.displayContact);

        // Get the data from Intent
        String name = getIntent().getStringExtra("USER_NAME");
        String age = getIntent().getStringExtra("USER_AGE");
        String email = getIntent().getStringExtra("USER_EMAIL");
        String contact = getIntent().getStringExtra("USER_CONTACT");

        // Set the data to the TextViews
        displayName.setText("Name: " + name);
        displayAge.setText("Age: " + age);
        displayEmail.setText("Email: " + email);
        displayContact.setText("Contact: " + contact);
    }
}
```

### AndroidManifest.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Workshop_1"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"


        android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity android:name=".DisplayActivity"></activity>
    </application>

</manifest>
```
## OUTPUT

![image](https://github.com/user-attachments/assets/783e5c9d-9e54-4313-8d85-4698432f9efd)

![image](https://github.com/user-attachments/assets/8bdc7003-d04d-42a2-be48-1200091420e0)



## RESULT
Thus an android application to pass the data between the activities using Intent is developed and executed successfully.
