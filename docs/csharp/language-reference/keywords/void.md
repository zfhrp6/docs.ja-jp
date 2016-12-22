---
title: "void (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
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
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# void (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)   
 [値型](../../../csharp/language-reference/keywords/value-types.md)   
 [メソッド](../../../fsharp/language-reference/members/methods.md)   
 [unsafe コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)