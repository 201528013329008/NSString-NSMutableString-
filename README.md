# NSString-NSMutableString-
 不可变|可变字符串
 
 
一. NSString
NSString 是一个不可变的字符串类,继承自 NSObject ,用NSString创建出来的字符串对象,一经创建就不能再修改了.我们可以对它执行查找或比较等操作,但是不能通过增加,删除它的字符来动态地改变它.
　　NSString主要的方法都在Foundation/NSString.h中定义的,NSString提供了很多方法的接口,但是这些方法的实现都是由内部具体实现的.下面将对NSString的主要方法进行说明
这里我们通过一个具体的例子来进行分析。
创建字符串对象：
NSString *str1 = @'This is a string 1';
格式化创建字符串
NSString *str2 = [NSString stringWithFormat:@'This is a string %d',2];
计算字符串中的字符个数：
NSUInteger strLength = [str1 length];
利用stringWithString 将一个字符串赋值到另一个字符串：
NSString *strCopy = [NSString stringWithString:str1];
stringByAppendingString，拼接字符串，将一个字符串复制到另一个字符串的末尾：
NSString *strByAppend = [str1 stringByAppendingString:str2];
stringByAppendingFormat，格式化拼接字符串
NSString *strByAppend = [str1 stringByAppendingFormat:@'%@',@'aaaaaaa'];
isEqualToString，判断两个字符串是否相等：
if ([str1 isEqualToString:str2]) {
NSLog(@'字符串str1 == str2');
}else{
NSLog(@'字符串str1 != str2');
}
compare : 方法测试一个值是否在数值上小于、等于或大于另一个值。
如： [intNumber compare : myNumber]
若intNumber 小于 myNumber ，返回NSOrderedAscending ;
相等 ，返回NSOrderdSame;
大于 ，返回NSOrderdDescending；
NSString *strSubFrom = [str1 substringFromIndex:5];
NSComparisonResult comparison = [str1 compare:str2];
if (comparison == NSOrderedAscending) {
NSLog(@'str1 < str2');
}
else if(comparison == NSOrderedSame)
NSLog(@'str1 == str2');
else
NSLog(@'str1 > str2');
uppercaseString,将字符串转换为大写。
NSString *strUpepr = [str1 uppercaseString];
lowercaseString,将字符串转换为小写。
NSString *strLower = [str1 lowercaseString];
capitalizedString,首字母大写，其余小写
NSString *strCapitalized = [str1 capitalizedString];
stringByAppendingString,在字符串后面添加固定的字符串：
NSString *strByAppend = [str1 stringByAppendingString:str2];
stringByAppendingFormat，格式化拼接字符串
NSString *strByAppend = [str1 stringByAppendingFormat:@'%@',@'aaaaaaa'];
substringToIndex，获取str的前5个字符组成的字符串：
NSString *strSubTo = [str1 substringToIndex:5];
substringFromIndex，获取str从第5个字符开始，与后面字符组成的字符串：
NSString *strSubFrom = [str1 substringFromIndex:5];
substringWithRange，获取从第三个字符开始的四个字节长度的字符串
NSRange range = NSMakeRange(2, 4);
NSString *strSubRange = [str1 substringWithRange:range];
rangeOfString ， 获取ios在str中出现的位置：
NSRange range = [str3 rangeOfString:@'d,'];
NSLog(@'查找的字符串的位置:%lu 字符串长度:%lu',range.location,range.length);
componentsSeparatedByString，将字符串按照特定的字符分解为数组
NSString *str3 = @'a,b,c,d,e,f,g';
NSArray *arr = [str3 componentsSeparatedByString:@','];
hasPrefix,判断字符串str1前缀是否是'this'
BOOL isHasPrefix = [str1 hasPrefix:@'this'];
hasSuffix,判断字符串str1后缀是否是' is'
BOOL isHasSuffix = [str1 hasSuffix:@' is'];
UTF8String,将字符串转换为c语言格式
const char *charStr = [str1 UTF8String];



二. NSMutableString
NSMutableString对象代表一个字符序列可变的字符串，而且NSMutableString是NSString的子类，因此前面介绍的NSString所包含的方法，NSMutableString都可以直接使用，NSMutableString对象也可直接当成NSString对象使用。
创建可变字符串
NSMutableString *mutableStr1 = [[NSMutableString alloc]init];
stringWithCapacity,创建一直字符串长度的字符串
NSMutableString *mutableStr2 = [NSMutableString stringWithCapacity:10];
stringWithString，用不可变字符串创建可变字符串：
NSMutableString *mutableStr3 = [NSMutableString stringWithString:str1];
setString，给字符串赋值
[mutableStr1 setString:@'world'];
appendString,拼接字符串
[mutableStr1 appendString:@'this is NSMutableString'];
appendFormat，格式化拼接字符串
[mutableStr1 appendFormat:@'%@',mutableStr2];
insertString: atIndex: ，在mutableStr2 的第六个字符后边插入字符串mutableStr3：
[mutableStr2 insertString:mutableStr3 atIndex:6];
deleteCharactersInRange:NSMakeRange() , 根据范围删除子字符串：
NSRange range = NSMakeRange(2, 4);
[mutableStr1 deleteCharactersInRange:range];
replaceCharactersInRange:withString:,替换指定范围内的字符串
[mutableStr1 replaceCharactersInRange:range withString:mutableStr2];
