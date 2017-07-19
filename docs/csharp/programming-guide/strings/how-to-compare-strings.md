---
title: "方法 : 文字列を比較する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: 23
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 1699a488234a9de8dab9c060bb33e6afd2346780
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

---
# <a name="how-to-compare-strings-c-programming-guide"></a>方法 : 文字列を比較する (C# プログラミング ガイド)
文字列を比較する場合、1 つの文字列がその他の文字列よりも大きいか小さいか、または 2 つの文字列が等しいことを示す結果を生成します。 *序数に基づく比較*か、*カルチャで区別される比較*のいずれを実行しているかに応じて、結果を決定する規則は異なります。 特定のタスクに正しい種類の比較を使用することが重要です。  
  
 言語の規則に関係なく、2 つの文字列の値を比較または並べ替える必要がある場合、基本の序数に基づく比較を使用します。 基本の序数に基づく比較 (`System.StringComparison.Ordinal`) は、大文字と小文字を区別します。つまり、2 つの文字列は、文字レベルで一致している必要があります ("and" は、"And" や "AND" と等しくありません)。 頻繁に使用される変数の `System.StringComparison.OrdinalIgnoreCase` では、"and"、"And"、および "AND" は一致と見なされます。 `StringComparison.OrdinalIgnoreCase` は、ファイル名、パス名、ネットワーク パス、およびユーザーのコンピューターのロケールに基づいて変更されない値を持つその他の文字列を比較するために使用されます。 詳細については、「<xref:System.StringComparison?displayProperty=fullName>」を参照してください。  
  
 通常、文字および文字列の並べ替え規則は、ユーザーのコンピューターのロケールによって異なる可能性があるため、カルチャで区別される比較は、エンド ユーザーが入力する文字列を比較および並べ替えるために使用されます。 同一の文字を含む文字列でも、現在のスレッドのカルチャに応じて、異なる方法で並べ替えられます。  
  
> [!NOTE]
>  文字列を比較する場合、実行する比較の種類を明示的に指定するメソッドを使用する必要があります。 これらのメソッドを使用すると、コードを保守しやすく、読みやすくすることができます。 可能な限り、<xref:System.StringComparison> 列挙型のパラメーターを取る、<xref:System.String?displayProperty=fullName> と <xref:System.Array?displayProperty=fullName> クラスのメソッドのオーバーロードを使用し、どの種類の比較を実行するか指定できるようにします。 文字列を比較する場合、`==` 演算子と `!=` 演算子を使用しないことをお勧めします。 なお、いずれのオーバーロードも <xref:System.StringComparison> を取ることはないため、ここでは <xref:System.String.CompareTo%2A?displayProperty=fullName> インスタンス メソッドは使用しません。  
  
## <a name="example"></a>例  
 次の例では、ユーザーのコンピューターのロケールに基づいて、値が変更されない文字列を正しく比較する方法を示します。 さらに、C# の*文字列のインターン*機能も示しています。 プログラムで 2 つ以上の同じ文字列変数を宣言すると、コンパイラはそれらをすべて同じ場所に保管します。 <xref:System.Object.ReferenceEquals%2A> メソッドを呼び出すと、2 つの文字列がメモリ内の同じオブジェクトを実際に参照していることを確認できます。 インターンを回避するには、次の例のように、<xref:System.String.Copy%2A?displayProperty=fullName> メソッドを使用します。  
  
 [!code-cs[csProgGuideStrings#11](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.StringComparison> 列挙型を取る <xref:System.String?displayProperty=fullName> メソッドを使用して、推奨の方法で文字列を比較する方法を説明します。 なお、いずれのオーバーロードも <xref:System.StringComparison> を取ることはないため、ここでは <xref:System.String.CompareTo%2A?displayProperty=fullName> インスタンス メソッドは使用していません。  
  
 [!code-cs[csProgGuideStrings#31](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_2.cs)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.StringComparer?displayProperty=fullName> パラメーターを受け取る静的 <xref:System.Array> メソッドを使用したカルチャで区別される手法で、配列内の文字列を検索および並べ替える方法を示します。  
  
 [!code-cs[csProgGuideStrings#32](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_3.cs)]  
  
 <xref:System.Collections.Hashtable?displayProperty=fullName>、<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>、および <xref:System.Collections.Generic.List%601?displayProperty=fullName> などのコレクション クラスには、要素またはキーの種類が `string` の場合、<xref:System.StringComparer?displayProperty=fullName> パラメーターを取るコンストラクターが用意されています。 通常は、これらのコンストラクターをできるだけ使用し、`Ordinal` または `OrdinalIgnoreCase` を指定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.StringComparer?displayProperty=fullName>   
 [文字列](../../../csharp/programming-guide/strings/index.md)   
 [文字列の比較](../../../standard/base-types/comparing.md)   
 [アプリケーションのグローバライズとローカライズ](https://docs.microsoft.com/visualstudio/ide/globalizing-and-localizing-applications)
