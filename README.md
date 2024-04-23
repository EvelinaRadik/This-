Sure! Here is a Kotlin code snippet for an Android Studio project that checks if a ticket number entered by the user is lucky or not:

1. Create a new Kotlin class named MainActivity:

kotlin
import android.os.Bundle
import android.util.Log
import androidx.appcompat.app.AppCompatActivity
import kotlinx.android.synthetic.main.activity_main.*
import kotlin.math.floor

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        checkButton.setOnClickListener {
            val ticketNumber = ticketNumberEditText.text.toString()
            if (ticketNumber.length == 6) {
                val firstHalf = ticketNumber.substring(0, 3)
                val secondHalf = ticketNumber.substring(3)

                val firstSum = firstHalf.map { it.toString().toInt() }.sum()
                val secondSum = secondHalf.map { it.toString().toInt() }.sum()

                if (firstSum == secondSum) {
                    resultTextView.text = "Congratulations! This is a lucky ticket!"
                } else {
                    resultTextView.text = "Sorry, this is not a lucky ticket."
                }
            } else {
                resultTextView.text = "Please enter a 6-digit ticket number."
            }
        }
    }
}


2. Add the following XML code to the activity_main.xml layout file:

xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/ticketNumberEditText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="Enter 6-digit ticket number"
        android:inputType="number"
        android:layout_centerHorizontal="true"/>

    <Button
        android:id="@+id/checkButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Check"
        android:layout_below="@id/ticketNumberEditText"
        android:layout_centerHorizontal="true"/>

    <TextView
        android:id="@+id/resultTextView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text=""
        android:layout_below="@id/checkButton"
        android:layout_centerHorizontal="true"/>

</RelativeLayout>


3. Run the app on your Android device or emulator.

Now you can enter a 6-digit ticket number in the EditText field and click the Check button to see if the ticket is lucky or not.
