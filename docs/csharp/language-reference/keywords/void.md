---
title: "void (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "void_CSharpKeyword"
  - "void"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "void キーワード [C#]"
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# void (C# リファレンス)
メソッドは、値を返さないことを使用すると、`void` メソッドの戻り値を指定します。  
  
 `void` はメソッドのパラメーター リストでは使用できません。  パラメーターや戻り値を持たないメソッドの宣言は、次のとおりです。  
  
```  
public void SampleMethod()  
{  
    // Body of the method.  
}  
  
```  
  
 また、`void` は、unsafe コンテキストで不明な型へのポインターを宣言するときにも使用されます。  詳細については、「[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)」を参照してください。  
  
 `void` は、.NET Framework の <xref:System.Void?displayProperty=fullName> 型のエイリアスです。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)   
 [値型](../../../csharp/language-reference/keywords/value-types.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [unsafe コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)