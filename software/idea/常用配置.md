## 自动生成注释（创建类文件后自动生成注释）

Preferences -> Editor -> File and Code Templates -> Files

#### Class模版
```shell
#if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end
#parse("File Header.java")
/**
 * 
 * @author ckh
 * @date ${YEAR}-${MONTH}-${DAY}
 */
public class ${NAME} {
}
```

## 显示空白字符

Preferences -> Editor -> General -> Appearance

勾选 Show whitespaces

## .properties不显示中文，显示unicode编码

Preferences -> Editor -> File Encodings

设置 Default encoding for properties files 为 utf8

勾选后面的 Transparent native-to-ascii conversion


## 自动清除没用的import

Preferences -> Editor -> General -> Auto Import

勾选 Optimize imports on the fly