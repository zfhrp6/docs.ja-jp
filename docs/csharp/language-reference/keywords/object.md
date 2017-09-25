---
title: "object (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
dev_langs:
- CSharp
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 16
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
ms.openlocfilehash: 744debc51f68cc52f03bce09c9f276a66ae085e1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/25/2017

---
# <a name="object-c-reference"></a>object (C# リファレンス)
`object` 型は、.NET Framework の <xref:System.Object> のエイリアスです。 C# の統一型システムでは、すべての型 (定義済み、ユーザー定義、参照型、および値型) が、直接または間接的に <xref:System.Object> を継承します。 `object` 型の変数には、任意の型の値を割り当てることができます。 値型の変数が object に変換されることを、*ボックス化*されると言います。 object 型の変数が値型に変換されることを、*ボックス化解除*されると言います。 詳しくは、「[ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例は、`object` 型の変数で任意のデータ型の値を受け取る方法と、`object` 型の変数で .NET Framework の <xref:System.Object> に対するメソッドを使用する方法を示したものです。  
  
 [!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)   
 [値型](../../../csharp/language-reference/keywords/value-types.md)

