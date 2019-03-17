---
title: PHP CSV输出及相关调整
date: 2019-03-17 11:45:02
tags: 笔记
---
## CSV输出
`
fputcsv(resource $handle , array $fields):int
`
核心函数，将`$filelds`数组中的数据作为一行记录插入到`$hanlde`文件中，具体参见[PHP:fputcsv()](http://us3.php.net/manual/zh/function.fputcsv.php)

使用实例
```php
//要插入的数据
$arr = array(姓名,性别,年龄);
//要插入数据的csv文件
$fp = fopen("test.csv","w");
//插入操作
if ($fp) {
    fputcsv($fp, $arr);
}
//关闭文件
fclose($fp);
```
默认的UTF-8编码有时可能会导致输出结果出现乱码，这时可以用
- `
iconv ( $in_charset , $out_charset , $str ) : string
`
具体参见[PHP:iconv()](http://us3.php.net/manual/zh/function.iconv.php)
- `
mb_convert_encoding ( $str , $to_encoding ) : string
`
具体参见[PHP:mb_convert_encoding()](http://us3.php.net/manual/zh/function.mb-convert-encoding.php)

## 生成ZIP文件
### 无密码
```php
$zip = new ZipArchive();
$result = $zip->open($zip_file_path, ZipArchive::CREATE);
if ($result) {
    $zip->addFile($compress_file_path);
    $zip->close();
}
```
### 有密码
```php
exec("zip -P ".$password." ".$zip_file." ".$compress_file_path);
```
由于之前的`ZipArchive`类没有提供有密码压缩的方法所以用`exec()`函数调用`zip`命令行实现。
