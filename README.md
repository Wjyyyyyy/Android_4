# perference_hz
##实验四_扩展的Activity



![](https://github.com/Wjyyyyyy/Image/blob/master/4.1.png)
![](https://github.com/Wjyyyyyy/Image/blob/master/4.2.png)
![](https://github.com/Wjyyyyyy/Image/blob/master/4.3.png)
![](https://github.com/Wjyyyyyy/Image/blob/master/4.4.png)
![](https://github.com/Wjyyyyyy/Image/blob/master/4.5.png)


关键代码：



MainActivity.java
```
@Override
protected void onCreate(Bundle savedInstanceState) {
    //onCreate方法保存Activity的状态
    super.onCreate(savedInstanceState);
   // setContentView(R.layout.activity_main);
    // activity_mainw为自带的hello word不需要调用
    getFragmentManager().beginTransaction().add(android.R.id.content, new PrFragment()).commit();
    //Fragment对象
}
```



PrFragment.java
```
@Override
public void onCreate(Bundle savedInstanceState){
    super.onCreate(savedInstanceState);
    //onCreate方法保存Activity的状态
    addPreferencesFromResource(R.xml.perference);
    //调用XML文件perference
}
```



布局代码：
```
<PreferenceScreen xmlns:android="http://schemas.android.com/apk/res/android">
    <PreferenceCategory android:title="ln-line preference">
        <CheckBoxPreference
            android:summary="this is a checkbox"
            android:title="CheckBox Preference"
            android:key="checkBox"
            >
        </CheckBoxPreference>
    </PreferenceCategory>
    <PreferenceCategory android:title="Dialog-based preferences">
        <EditTextPreference
            android:dialogTitle="Enter your favorite animal"
            android:summary="An example that uses an edit text dialog"
            android:title="Edit text preference"
            android:key="editText"
           >
        </EditTextPreference>
        <ListPreference
            android:summary="An example that uses a list dialog"
            android:title="List preference"
            android:key="list"
            android:dialogTitle="Choose one"
            android:entries="@array/list"
            android:entryValues="@array/list">
            <!-- 此处用到了values文件下的strings.xml文件 -->
            <!--
            strings.xml文件关键代码如下
            <item>Alpha Option 01</item>
            <item>Beta Option 02</item>
            <item>Charlie Option 03</item>
            -->
        </ListPreference>
    </PreferenceCategory>
    <PreferenceCategory android:title="Launch preference">
        <PreferenceScreen
            android:summary="Shows another screen of preference"
            android:key="screen"
            android:title="Screen Preference"
            >
            <CheckBoxPreference
                android:key="another_checkBox"
                android:title="Toggle Preference"
                android:summary="Preference that is on the next screen but same hierarchy"
                >
            </CheckBoxPreference>
        </PreferenceScreen>
        <PreferenceScreen
            android:title="Intent preference"
            android:summary="Launches an Activity from an Intent">
            <intent
                android:action="android.intent.action.VIEW"
                android:data="https://www.gogle.com">
                <!-- 跳出网站谷歌 -->
            </intent>
        </PreferenceScreen>
    </PreferenceCategory>
    <PreferenceCategory android:title="Preference attributes">
        <CheckBoxPreference
            android:key="parent_checkBox"
            android:title="Parent checkBox preference"
            android:summary="This is visually a parent">
            <!-- 父类 -->
        </CheckBoxPreference>
        <CheckBoxPreference
            android:dependency="parent_checkBox"
            android:key="child_checkBox"
            android:title="Child checkBox preference"
            android:summary="This is visually a child">
            <!-- 子类 -->
        </CheckBoxPreference>
    </PreferenceCategory>
</PreferenceScreen>
```














