### Failed to install the app on the device because we couldn't execute the "ios-deploy" command

```shell
brew install ios-deploy
```

### D8: Cannot fit requested classes in a single dex file

project/app/build.gradle添加一下配置
```shell
defaultConfig {
    ...
    multiDexEnabled true
}
```
和以下配置
```shell
dependencies {
    ...
    implementation 'com.android.support:multidex:1.0.3'
}
```