# SingleMuiltiplePermission


# ★ Gradle Dependency
Add Gradle dependency in the build.gradle file of your application module (app in the most cases) :
First Tab:

```sh
allprojects {
    repositories {
        google()
        jcenter()
        maven { url 'https://jitpack.io' }
    }
}
```

AND

```sh
dependencies {
     compile 'com.github.ghosharunava:SingleMuiltiplePermission:V1.02'
}
```
Here, one interesting thing is that dangerous permissions are grouped into the Permission Group, as displayed in the table.

https://i.stack.imgur.com/kYpqt.png

But what does it mean? It means that you need to request for only one permission from group.

If any permission from permission group is granted, then other permissions from the same group will be granted automatically. Likewise if any permission from permission group is denied, then entire group will be denied.

Once READ_EXTERNAL_STORAGE is granted, application will also grant WRITE_EXTERNAL_STORAGE permission.

Example : Permissions are grouped into the Permission Group.
For Example, android.permission.READ_CALENDAR, and
android.permission.WRITE_CALENDAR,
these two permissions are grouped in android.permission-group.CALENDAR.

If any permission in a Permission Group is granted. Another permission in the same group will be automatically granted as well. In the above example, if READ_CALENDAR is granted, the the application will also grant WRITE_CALENDAR.


# ★ Taking Permision in Manifest:
 1.For Location [Fine Location/COARSE_LOCATION] 
 =>
 <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
 
 2.For Camera  [Camera]  
 =>
 <uses-permission android:name="android.permission.CAMERA"/>
 
 3.For File_STORAGE [READ_EXTERNAL_STORAGE/WRITE_EXTERNAL_STORAGE] 
 => 
 <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/> 
 
 4.For SMS [SEND_SMS/RECEIVE_SMS/READ_SMS/RECEIVE_WAP_PUSH/RECEIVE_MMS/READ_CELL_BROADCASTS] 
 => 
 <uses-permission android:name="android.permission.SEND_SMS"/>
 
 5.For CALENDAR [READ_CALENDAR/WRITE_CALENDAR] 
 => 
 <uses-permission android:name="android.permission.WRITE_CALENDAR"/>
 
 6.For CONTACTS[READ_CONTACTS/WRITE_CONTACTS/GET_ACCOUNTS] 
 => 
  <uses-permission android:name="android.permission.WRITE_CONTACTS"/>
 
 7.For CALL_PHONE [READ_PHONE_STATE/CALL_PHONE/READ_CALL_LOG/WRITE_CALL_LOG/ADD_VOICEMAIL/USE_SIP/PROCESS_OUTGOING_CALLS]
 => 
 <uses-permission android:name="android.permission.CALL_PHONE"/>
 
 8.For MICROPHONE [RECORD_AUDIO] 
 => 
  <uses-permission android:name="android.permission.ADD_VOICEMAIL"/>
 
 9.For Sensors [BODY_SENSORS] 
 => 
  <uses-permission android:name="android.permission.BODY_SENSORS"/>
 
 
   # How to call Permission class ?
    
  =>>
      new MultiplePermission(MainActivity.this, new MultiplePermission.GetPermissionResult() {
                    @Override
                    public void getPermissionMessage(String permissionStatus) {

                   if(permissionStatus.equals("OK")){
                            
                            Toast.makeText(MainActivity.this, "All Permissipon is taken", Toast.LENGTH_SHORT).show();
                        }
                        else{
                            Toast.makeText(MainActivity.this, "Not All Permissipon is taken", Toast.LENGTH_SHORT).show();
                        }
                    }
                },"Location","Camera","File_STORAGE","SMS","CALENDAR","CONTACTS","CALL_PHONE","Record_Audio","Sensors");
                
                

//**permissionStatus.equals("OK")= all Dangerous permission is garnted,else all Dangerous permission is not garnted yet**
