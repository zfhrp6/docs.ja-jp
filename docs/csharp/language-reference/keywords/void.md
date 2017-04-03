---
title: "void (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
dev_langs:
- CSharp
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b4aa3c7c54e5e4d53975262adbbd9b54c701a69e
ms.lasthandoff: 03/13/2017

---
# <a name="void-c-reference"></a>void (C# リファレンス)
メソッドの戻り値の型として使用した場合、`void` はメソッドが値を返さないことを指定します。  
  
 `void` は、メソッドのパラメーター リストに含めることはできません。 パラメーターを取らず、値を返さないメソッドは、次のように宣言されます。  
  
```  
public void SampleMethod()  
{  
    // Body of the method.  
}  
  
```  
  
 `void` は、不明な型へのポインターを宣言するために、unsafe コンテキストでも使用されます。 詳しくは、「[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)」をご覧ください。  
  
 `void` は、.NET Framework <xref:System.Void?displayProperty=fullName> 型のエイリアスです。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)   
 [値型](../../../csharp/language-reference/keywords/value-types.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
