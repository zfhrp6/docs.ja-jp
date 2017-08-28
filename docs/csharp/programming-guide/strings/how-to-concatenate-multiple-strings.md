---
title: "方法: 複数の文字列を連結する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
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
ms.openlocfilehash: b191a61258a496115a4d7045046f9b4a2dbee58c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a>方法: 複数の文字列を連結する (C# プログラミング ガイド)
*連結*とは、ある文字列を別の文字列の末尾に追加するプロセスです。 `+` 演算子を使用して文字列リテラルまたは文字列定数を連結すると、コンパイラによって 1 つの文字列が作成されます。 実行時の連結は発生しません。 ただし、文字列変数の場合は実行時にのみ連結できます。 この場合、方法によるパフォーマンスの違いを理解することをお勧めします。  
  
## <a name="example"></a>例  
 ソース コードを読みやすくするために、長い文字列リテラルを短い文字列に分割している例を次に示します。 これらの文字列は、コンパイル時に 1 つの文字列に連結されます。 関係する文字列の数に関係なく、実行時にパフォーマンス コストは発生しません。  
  
 [!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a>例  
 文字列変数を連結するには、`+` または `+=` 演算子を使用するか、<xref:System.String.Concat%2A?displayProperty=fullName>、<xref:System.String.Format%2A?displayProperty=fullName>、または <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName> メソッドを使用します。 `+` 演算子は使い方が簡単で、直感的なコードにすることができます。 1 つのステートメントで複数の + 演算子を使用している場合でも、文字列の内容がコピーされるのは 1 回のみです。 ただし、ループなどでこの操作を複数回実行すると、効率の問題が発生する可能性があります。 たとえば次のようなコードがあるとします。  
  
 [!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  C# コンパイラでは、文字列連結操作の null 文字列は空の文字列と同様に扱われますが、元の null 文字列の値は変換されません。  
  
 (1 つのループ内などで) 多数の文字列を連結しない場合、このコードのパフォーマンス コストはそれほどかからない可能性があります。 <xref:System.String.Concat%2A?displayProperty=fullName> メソッドと <xref:System.String.Format%2A?displayProperty=fullName> メソッドについても同様です。  
  
 ただし、パフォーマンスが重要な場合は、常に <xref:System.Text.StringBuilder> クラスを使用して文字列を連結することをお勧めします。 次のコードでは、`+` 演算子のチェーン効果を使用せず、<xref:System.Text.StringBuilder> クラスの <xref:System.Text.StringBuilder.Append%2A> メソッドを使用して文字列を連結しています。  
  
 [!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.String>   
 <xref:System.Text.StringBuilder>   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [文字列](../../../csharp/programming-guide/strings/index.md)

