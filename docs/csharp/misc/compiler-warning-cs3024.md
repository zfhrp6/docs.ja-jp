---
title: "コンパイラの警告 CS3024 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "CS3024"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3024"
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
caps.latest.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 7
---
# コンパイラの警告 CS3024
制約型 'type' が CLS に準拠していません。  
  
 CLS 非準拠の型をジェネリック型制約として使用すると、一部の言語で記述されたコードがジェネリック クラスを使用できなくなる可能性があるため、コンパイラはこの警告を発行します。  
  
### この警告を回避するには  
  
1.  型制約には、CLS 準拠の型を使用します。  
  
## 使用例  
 次の例では、複数の場所で CS3024 が生成されます。  
  
```  
// cs3024.cs // Compile with: /target:library [assembly: System.CLSCompliant(true)] [type: System.CLSCompliant(false)] public class TestClass // CS3024 { public ushort us; } [type: System.CLSCompliant(false)] public interface ITest // CS3024 {} public interface I<T> where T : TestClass {} public class TestClass_2<T> where T : ITest {} public class TestClass_3<T> : I<T> where T : TestClass {} public class TestClass_4<T> : TestClass_2<T> where T : ITest {} public class Test { public static int Main() { return 0; } }  
```  
  
## 参照  
 [型パラメーターの制約](../../csharp/programming-guide/generics/constraints-on-type-parameters.md)