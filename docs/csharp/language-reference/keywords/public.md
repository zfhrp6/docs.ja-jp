---
title: "public (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- public
- public_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: 21
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ae19bf9a33a9860a8960cde5dd4402e10418a094
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

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
  
 [!code-cs[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 `public` アクセス レベルを [private](../../../csharp/language-reference/keywords/private.md) または [protected](../../../csharp/language-reference/keywords/protected.md) に変更すると、次のエラー メッセージが表示されます。  
  
 'PointTest.y' はアクセスできない保護レベルになっています。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
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

