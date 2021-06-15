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

### AudioRecorderManager.java:30: 错误: 找不到符号
```shell
# 作者GitHub更新4.3.1，虽然作者修改了gradle文件，但是AudioRecorderManager文件还是有问题，需要手动修改。
import android.support.v4.app.ActivityCompat;
import android.support.v4.content.ContextCompat;
# 手动修改一下：
import androidx.core.app.ActivityCompat;
import androidx.core.content.ContextCompat;
```

### event2/event-config.h' file not found
```shell
use_flipper!
# 改为
use_flipper!({ 'Flipper-Folly' => '2.3.0' })
```