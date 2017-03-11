---
title: "/moduleassemblyname (C# Compiler Option) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/moduleassemblyname"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "moduleassemblyname compiler option [C#]"
  - "/moduleassemblyname compiler option [C#]"
  - ".moduleassemblyname compiler option [C#]"
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# /moduleassemblyname (C# Compiler Option)
.netmodule がアクセスできる非パブリック型のアセンブリを指定します。  
  
## 構文  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## Arguments  
 `assembly_name`  
 非パブリック型にアクセスできる"アセンブリの名前。  
  
## 解説  
 **\/moduleassemblyname** は、次の条件が true である場合は"のビルド時には使用しないでください。:  
  
-   .netmodule が非パブリック型にアクセスする既存のアセンブリが必要です。  
  
-   .netmodule をビルドするアセンブリの名前を把握しています。  
  
-   既存のアセンブリが .netmodule をビルドするアセンブリにフレンド アセンブリ アクセスを許可します。  
  
 .netmodule のビルドの詳細については、「[\/target:module \(Create Module to Add to Assembly\)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)」を参照してください。  
  
 フレンド アセンブリの詳細については、「[フレンド アセンブリ](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 このオプションは開発環境内では利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
 このコンパイラ オプションは、Visual Studio で利用できず、プログラムで変更することもできません。  
  
## 使用例  
 この例では、プライベート型のアセンブリをビルドし、csman\_an\_assembly というアセンブリにフレンド アセンブリ アクセスを許可しています。  
  
```  
// moduleassemblyname_1.cs  
// compile with: /target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## 使用例  
 このサンプルでは、.netmodule からそのアセンブリ moduleassemblyname\_1.dll にアクセスする .netmodule をビルドします。  この .netmodule はアセンブリにビルドされていることを確認して、次 **\/moduleassemblyname**を指定し、csman\_an\_assembly 呼び出します。非パブリックにアクセスできるように"が型 csman\_an\_assembly にフレンド アセンブリ アクセスを許可したアセンブリをします。  
  
```  
// moduleassemblyname_2.cs  
// compile with: /moduleassemblyname:csman_an_assembly /target:module /reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## 使用例  
 このコード サンプルでは、アセンブリ csman\_an\_assembly をビルドし、以前にビルドしたアセンブリと"を参照してください。  
  
```  
// csman_an_assembly.cs  
// compile with: /addmodule:moduleassemblyname_2.netmodule /reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
  **An\_Internal\_Class.Test called**   
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)