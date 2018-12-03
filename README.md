# Mp3Recorder

Android 录制MP3音频，使用 lame 实时转码

窃来的，忘记几年前从哪里找到的代码，好几个项目都用，很方便，提取出来形成引用包

#### 引用

##### Project build.gradle配置

```groovy
allprojects {
  repositories {
    ...
    maven { url 'https://jitpack.io' }
  }
}
```

##### Module build.gradel配置

```groovy
dependencies {
        implementation 'com.github.Dean1990:Mp3Recorder:-SNAPSHOT'
}
```

#### 使用

```xml
//需要先声明权限
<uses-permission android:name="android.permission.RECORD_AUDIO"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
```



开始录音

```java
//动态申请权限
if (mRecorder == null) {
	mRecorder = new Mp3Recorder();
	mRecorder.setOnRecordListener(new Mp3Recorder.OnRecordListener() {
		@Override
		public void onStart() {
			//开始录音
		}

		@Override
		public void onStop() {
			//停止录音
		}
	});
}
if (!mRecorder.isRecording())
	try {
		mRecorder.startRecording("/sdcard","record.mp3");
	} catch (IOException e) {
		e.printStackTrace();
	}
```



停止录音

```java
if (mRecorder!=null && mRecorder.isRecording()){
	mRecorder.stopRecording();
}
```

