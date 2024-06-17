# FSTT SDK Android



## 1. Install STT SDK
## 2. SDK Integration
#### Initialize SDK
**java:**
```java
@Override
public void onCreate(@Nullable Bundle savedInstanceState, @Nullable PersistableBundle persistentState) {
    super.onCreate(savedInstanceState, persistentState);
    ...
    STTManager.init(getApplicationContext());
}
```
**kotlin:**
```kotlin
override fun onCreate() {
        super.onCreate()
        ...
    STTManager.init(applicationContext)
    }
```
#### Init gateway
**java:**
```java
STTManager.initGateway(appId, secretKey, new IInitGatewayCallback() {
    @Override
    public void onSuccess() {

    }

    @Override
    public void onFail(@Nullable AppException error) {

    }
});
```
**kotlin:**
```kotlin
STTManager.initGateway(appId, secretKey, object : IInitGatewayCallback {
    override fun onSuccess() {
    
    }

    override fun onFail(error: AppException?) {

    }
})
```
#### Register STT callback
**After registration, the SDK will return the corresponding status in the callback**
| Status     | Description |
| ----------- | ----------- |
| onStart      | Called at start record       |
| onRecording   | Called while in process recording        |
| onSuccess      | Called when completed record process and return result       |
| onFail   | Called when an error occurs in process recording        |
**java:**
```java
STTManager.registerSTTCallback(new ISTTCallback() {
    @Override
    public void onStart() {
        
    }

    @Override
    public void onRecording() {

    }

    @Override
    public void onFail(@Nullable AppException error) {

    }

    @Override
    public void onSuccess(@NonNull String result) {

    }
});
```
**kotlin:**
```kotlin
STTManager.registerSTTCallback(object : ISTTCallback {
    override fun onStart() {

    }

    override fun onRecording() {
    
    }

    override fun onFail(error: AppException?) {

    }

    override fun onSuccess(result: String) {

    })
})
```
## 3. SDK Features
#### Start STT
* Used to start record for STT
* When successful start, the SDK starts entering the recording state, it will be called on `onStart()` in callback. Handling start record successfully here.
* When start record fails, it will be processed at callback `onFail()` in callback.

**java:**
```java
STTManager.startSTT();
```
**kotlin:**
```kotlin
STTManager.startSTT()
```
#### Stop STT
* Used to stop record and process record to text result
* When successful, the SDK will be return text result on `onSuccess()` in callback. Handling stop record successfully here.
* When fails, it will be processed at callback `onFail()` in callback.

**java:**
```java
STTManager.stopSTT();
```
**kotlin:**
```kotlin
STTManager.stopSTT()
```