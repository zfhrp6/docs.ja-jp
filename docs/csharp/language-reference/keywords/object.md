---
title: object (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 67eaf7f1fd2f01e433395ed21701c3b7fad7c7b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267923"
---
# <a name="object-c-reference"></a>object (C# リファレンス)
`object` 型は、.NET Framework の <xref:System.Object> のエイリアスです。 C# の統一型システムでは、すべての型 (定義済み、ユーザー定義、参照型、および値型) が、直接または間接的に <xref:System.Object> を継承します。 `object` 型の変数には、任意の型の値を割り当てることができます。 値型の変数が object に変換されることを、*ボックス化*されると言います。 object 型の変数が値型に変換されることを、*ボックス化解除*されると言います。 詳細については、「[ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、`object` 型の変数で任意のデータ型の値を受け取る方法と、`object` 型の変数で .NET Framework の <xref:System.Object> に対するメソッドを使用する方法を示したものです。  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)  
 [値型](../../../csharp/language-reference/keywords/value-types.md)
