### LoadError - dlsym(0x7fbbeb6837d0, Init_ffi_c): symbol not found - /Library/Ruby/Gems/2.6.0/gems/ffi-1.13.1/lib/ffi_c.bundle

```shell
arch -x86_64 sudo gem install cocoapods
arch -x86_64 sudo gem install ffi
arch -x86_64 pod install
```

### Can't find 'node' binary to build React Native bundle If you have non-standard nodejs installation

```shell
ln -s $(which node) /usr/local/bin/node
```

### 打包出现：assertion failed expected 2 archs in otool output

finder -> application 选中 xcode，按下command+i，选择使用Rosetta打开，然后重新开启xcode