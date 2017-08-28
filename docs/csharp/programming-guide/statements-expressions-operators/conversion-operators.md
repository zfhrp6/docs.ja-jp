---
title: "変換演算子 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c12fd13d6526d79363f973ce2a944c4823bf4104
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="conversion-operators-c-programming-guide"></a>変換演算子 (C# プログラミング ガイド)
C# を使用すると、クラスまたは構造体に関する変換を宣言し、クラスまたは構造体を別のクラスまたは構造体に、または基本型に変換することができます。 変換は演算子と同様の方法で定義され、変換先の型に由来する名前が付けられます。 変換する引数の型と変換結果の型の両方ではなく一方を、含んでいる型にする必要があります。  
  
 [!code-cs[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a>変換演算子の概要  
 変換演算子には、次の特徴があります。  
  
-   `implicit` として宣言される変換は、必要なときに自動的に発生します。  
  
-   `explicit` として宣言される変換には、キャストの呼び出しが必要です。  
  
-   すべての変換は、`static` として宣言する必要があります。  
  
## <a name="related-sections"></a>関連項目  
 詳細情報  
  
-   [変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [方法: 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Convert>   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [Chained user-defined explicit conversions in C#](http://go.microsoft.com/fwlink/?LinkId=112384) (C# でのユーザー定義の明示的変換の連結)

