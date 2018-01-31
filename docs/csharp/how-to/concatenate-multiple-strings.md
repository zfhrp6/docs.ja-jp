---
title: "方法: 複数の文字列を連結する (C# ガイド)"
description: "C# で文字列を連結する方法は複数あります。 各選択のオプションと、それを選ぶ理由も示します。"
ms.date: 01/11/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4bc5e04edba48065746b96841b628ec5843c5e9
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>方法: 複数の文字列を連結する (C# ガイド)

*連結*とは、ある文字列を別の文字列の末尾に追加するプロセスです。 文字列を連結するには、+ 演算子を使用します。 文字列リテラルと文字列定数の場合、連結はコンパイル時に行われ、実行時には行われません。 文字列変数の連結は実行時にのみ行われます。

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

次の例では、ソース コードを読みやすくするために、連結を使用して長い文字列リテラルを短い文字列に分割しています。 これらの文字列は、コンパイル時に 1 つの文字列に連結されます。 関係する文字列の数に関係なく、実行時にパフォーマンス コストは発生しません。  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

文字列変数を連結するには、`+` または `+=` 演算子を使用するか、[文字列補間](../tutorials/string-interpolation.md) を使用するか、<xref:System.String.Concat%2A?displayProperty=nameWithType> メソッド、<xref:System.String.Format%2A?displayProperty=nameWithType> メソッド、または <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> メソッドを使用します。 `+` 演算子は使い方が簡単で、直感的なコードにすることができます。 1 つのステートメントで複数の + 演算子を使用している場合でも、文字列の内容がコピーされるのは 1 回のみです。 次のコードは、`+` 演算子を使用して文字列を連結する 2 つの例を示しています。

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

式によっては、次のコードに示すように、文字列補間を使用して文字列を連結する方が簡単な場合があります。
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  文字列連結操作において、C# コンパイラでは null 文字列は空の文字列と同様に扱われます。

文字列を連結する他のメソッドとして、<xref:System.String.Concat%2A?displayProperty=nameWithType> および <xref:System.String.Format%2A?displayProperty=nameWithType> があります。 これらのメソッドは、少ない数のコンポーネント文字列で文字列を作成する場合に有効です。 これらのメソッドは、連結した文字列を構成する文字列の数がわかっている場合にも有効です。

他にも、ループ内の文字列を結合する場合があります。このケースでは、結合するソース文字列の数はわからず、ソース文字列の実際の数は非常に大きくなる可能性があります。 <xref:System.Text.StringBuilder> クラスは、このようなシナリオのために設計されています。 次のコードでは、<xref:System.Text.StringBuilder> クラスの <xref:System.Text.StringBuilder.Append%2A> メソッドを使用して文字列を連結しています。  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

[文字列の連結または `StringBuilder` クラスを選択する理由](xref:System.Text.StringBuilder#StringAndSB)に関するページで詳細をご確認ください。

コレクションからの文字列を結合する別のオプションとして、[LINQ](../programming-guide/concepts/linq/index.md) および <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> メソッドを使用する方法があります。 このメソッドは、ラムダ式を使用してソース文字列を結合します。 ラムダ式は、各文字列を既存の蓄積に追加する処理を行います。 次の例では、配列内の各単語の間にスペースを追加することによって単語の配列を結合します。

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]  


## <a name="see-also"></a>参照  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [C# プログラミング ガイド](../programming-guide/index.md)  
 [文字列](../programming-guide/strings/index.md)
