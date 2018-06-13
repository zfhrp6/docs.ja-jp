---
title: void (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: e66efc287fc3ed0fcc15963a827fccb788c38753
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267289"
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
