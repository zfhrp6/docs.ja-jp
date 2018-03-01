---
title: "void (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a71cac30132417abce60cdde54322b5f2067d39d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="void-c-reference"></a>void (C# リファレンス)
メソッドの戻り値の型として使用した場合、`void` はメソッドが値を返さないことを指定します。

`void` は、メソッドのパラメーター リストに含めることはできません。 パラメーターを取らず、値を返さないメソッドは、次のように宣言されます。

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` は、不明な型へのポインターを宣言するために、unsafe コンテキストでも使用されます。 詳しくは、「[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)」をご覧ください。

`void` は、.NET Framework の <xref:System.Void?displayProperty=nameWithType> 型のエイリアスです。

## <a name="c-language-specification"></a>C# 言語仕様
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)  
 [値型](../../../csharp/language-reference/keywords/value-types.md)  
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
