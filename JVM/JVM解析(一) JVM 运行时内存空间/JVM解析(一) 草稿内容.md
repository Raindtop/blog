Demo.java

```
public class Test {


    private static int add(int c){
        return c + 10;
    }


    public static void main(String[] args) {
        int a, b, c;
        a = 1;
        b = 2;
        c = add(a*b);
        c = c*(a+b);
    }

}
```

Demo.class (编译后的文件)

```
Classfile /Home/JMM/Demo.class
  Last modified 2019-10-29; size 546 bytes
  MD5 checksum 3526f85e07771be800502f7e10b50a3a
  Compiled from "Test.java"
public class net.ziruo.juc.Test
  minor version: 0
  major version: 52
  flags: ACC_PUBLIC, ACC_SUPER
Constant pool:
   #1 = Methodref          #4.#24         // java/lang/Object."<init>":()V
   #2 = Methodref          #3.#25         // net/ziruo/juc/Test.add:(I)I
   #3 = Class              #26            // net/ziruo/juc/Test
   #4 = Class              #27            // java/lang/Object
   #5 = Utf8               <init>
   #6 = Utf8               ()V
   #7 = Utf8               Code
   #8 = Utf8               LineNumberTable
   #9 = Utf8               LocalVariableTable
  #10 = Utf8               this
  #11 = Utf8               Lnet/ziruo/juc/Test;
  #12 = Utf8               add
  #13 = Utf8               (I)I
  #14 = Utf8               c
  #15 = Utf8               I
  #16 = Utf8               main
  #17 = Utf8               ([Ljava/lang/String;)V
  #18 = Utf8               args
  #19 = Utf8               [Ljava/lang/String;
  #20 = Utf8               a
  #21 = Utf8               b
  #22 = Utf8               SourceFile
  #23 = Utf8               Test.java
  #24 = NameAndType        #5:#6          // "<init>":()V
  #25 = NameAndType        #12:#13        // add:(I)I
  #26 = Utf8               net/ziruo/juc/Test
  #27 = Utf8               java/lang/Object
{
  public net.ziruo.juc.Test();
    descriptor: ()V
    flags: ACC_PUBLIC
    Code:
      stack=1, locals=1, args_size=1
         0: aload_0
         1: invokespecial #1                  // Method java/lang/Object."<init>":()V
         4: return
      LineNumberTable:
        line 8: 0
      LocalVariableTable:
        Start  Length  Slot  Name   Signature
            0       5     0  this   Lnet/ziruo/juc/Test;

  private static int add(int);
    descriptor: (I)I
    flags: ACC_PRIVATE, ACC_STATIC
    Code:
      stack=2, locals=1, args_size=1
         0: iload_0
         1: bipush        10
         3: iadd
         4: ireturn
      LineNumberTable:
        line 12: 0
      LocalVariableTable:
        Start  Length  Slot  Name   Signature
            0       5     0     c   I

  public static void main(java.lang.String[]);
    descriptor: ([Ljava/lang/String;)V
    flags: ACC_PUBLIC, ACC_STATIC
    Code:
      stack=3, locals=4, args_size=1
         0: iconst_1
         1: istore_1
         2: iconst_2
         3: istore_2
         4: iload_1
         5: iload_2
         6: imul
         7: invokestatic  #2                  // Method add:(I)I
        10: istore_3
        11: iload_3
        12: iload_1
        13: iload_2
        14: iadd
        15: imul
        16: istore_3
        17: return
      LineNumberTable:
        line 18: 0
        line 19: 2
        line 20: 4
        line 21: 11
        line 22: 17
      LocalVariableTable:
        Start  Length  Slot  Name   Signature
            0      18     0  args   [Ljava/lang/String;
            2      16     1     a   I
            4      14     2     b   I
           11       7     3     c   I
}
```

​				· **操作数栈**：

​						· 在编译时期已经确定最大大小(?)

​				· **局部变量表**

​						` 局部变量表在class文件中已经定义，在方法的Code属性max_locals[**目前没有在class文件中发现这个属性，待定**]数据项中确定该方法需要分配的最大局部变量表的容量。

​				· 动态链接

​				 在Java源文件被编译到字节码文件时，所有的变量和方法引用都作为符号引用（Symbilic Reference）保存在class文件的常量池里。

比如：描述一个方法调用了另外的其他方法时，就是通过常量池中指向方法的符号引用来表示的，**动态链接的作用就是为了将这些符号引用转换位调用方法的直接引用**。