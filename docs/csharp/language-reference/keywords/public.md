---
title: public (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: abf7219359c108108b1ce3a3fde3dc10f9a8732d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="public-c-reference"></a>public (C# リファレンス)
`public` キーワードは、型と型のメンバーを示すアクセス修飾子です。 パブリック アクセスは、最も制限の少ないアクセス レベルです。 次の例のように、パブリック メンバーへのアクセスには制限がありません。  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 詳しくは、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」および「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例では、2 つのクラス (`PointTest` と `MainClass`) が宣言されています。 `PointTest` のパブリック メンバー `x` および `y` は、`MainClass` から直接アクセスされます。  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 `public` アクセス レベルを [private](../../../csharp/language-reference/keywords/private.md) または [protected](../../../csharp/language-reference/keywords/protected.md) に変更すると、次のエラー メッセージが表示されます。  
  
 'PointTest.y' はアクセスできない保護レベルになっています。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
