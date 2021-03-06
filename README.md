
# rn-bdlocation

## Getting started

`$ npm install rn-bdlocation --save`

### Mostly automatic installation

`$ react-native link rn-bdlocation`

### Manual installation


#### iOS

1. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2. Go to `node_modules` ➜ `rn-bdlocation` and add `RNBaiduLocation.xcodeproj`
3. In XCode, in the project navigator, select your project. Add `libRNBaiduLocation.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4. Run your project (`Cmd+R`)<

#### Android

1. Open up `android/app/src/main/java/[...]/MainActivity.java`
  - Add `import com.reactlibrary.RNBaiduLocationPackage;` to the imports at the top of the file
  - Add `new RNBaiduLocationPackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':rn-bdlocation'
  	project(':rn-bdlocation').projectDir = new File(rootProject.projectDir, 	'../node_modules/rn-bdlocation/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
      compile project(':rn-bdlocation')
  	```

## additional installation(require)

####IOS
1. Drag 'node_modules/rn-bdlocation/ios/BMKLocationKit.framework' to your project in xcode 
2. `Build Phases` ➜ `Link binary with libaries` add
 ```
BMKLocationKit.framework

CoreLocation.framework

SystemConfiguration.framework

Security.framework

libsqlite3.0.tbd

CoreTelephony.framework

libc++.tbd

AdSupport.framework
```
3. Open `Build Settings` ➜ `Framework Search Paths` add $(SRCROOT)/../node_modules/rn-bdlocation/ios
4. Open AppDelegate.m 
```
#import "AppDelegate.h"
#import <RNBaiduLocation.h> //ADD THIS
......
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
   ....
   [RNBaiduLocation setKey:yourApiKey]; //ADD THIS
   ....
    return YES;
}
```

#### Android
1.open `AndroidManifest.xml`
```
<manifest>
        .....
    <application>
    ......     //ADD BEHIND THESE
        <meta-data
           android:name="com.baidu.lbsapi.API_KEY"   
           android:value=${yourApiKey}>
            </meta-data>
         <service android:name="com.baidu.location.f" android:enabled="true" android:process=":remote"> </service>
         ....
    </application>
</manifest>

```
## Usage
```typescript
import RNBaiduLocation from 'rn-bdlocation';
interface Location{
    latitude:number;
    longitude:number;
    country:string;
    city:string;
    province:string;
    district:string;
    street:string;
    streetNumber:string;
    cityCode:string;
}
interface CheckProps {
    gpsIsOpen:boolean;
    gpsPermissionIsOpen:boolean;
}
 init:()=>Promise<void>;    //when App start use

 getLocation:()=>Promise<Location>;
 
 toGpsSetting:()=>Promise<void>; //only Android
 
 toAppSetting:()=>Promise<void>;  
 
 checkPermission:()=>Promise<CheckProps>;
 
```
  