---
title: "方法 : 文字列を比較する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "比較 (文字列を) [C#]"
  - "文字列 [C#], 比較"
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# 方法 : 文字列を比較する (C# プログラミング ガイド)
文字列を比較すると、一方の文字列が他方の文字列よりも長いまたは短いという結果、または 2 つの文字列が等しいという結果が得られます。  結果を決める規則は、*序数の比較*と*カルチャに依存した比較*のどちらを実行するかによって異なります。  特定のタスクに対して正しい種類の比較を使用することが重要です。  
  
 言語規則に関係なく 2 つの文字列値を比較または並べ替える必要がある場合、基本序数比較を使用します。  基本序数比較 \(`System.StringComparison.Ordinal`\) では、大文字と小文字が区別されます。したがって、2 つの文字列が文字レベルで一致している必要があります。たとえば、"and" と "And" または "AND" は等しくないと見なされます。  このバリエーションが頻繁に使用される  `System.StringComparison.OrdinalIgnoreCase` で、"and"、"And"、および "AND" が一致と見なされます。  `StringComparison.OrdinalIgnoreCase` は、ファイル名、パス名、ネットワーク パスを比較するため、およびユーザーのコンピューターのロケールに基づき変更されない値を持つその他の文字列を比較するためによく使用されます。  詳細については、「<xref:System.StringComparison?displayProperty=fullName>」を参照してください。  
  
 カルチャに依存した比較は、通常、エンド ユーザーが入力した文字列を比較および並べ替えるために使用されます。これは、これらの文字列の文字および並べ替え規則が、ユーザーのコンピューターのロケールによって異なる場合があるためです。  同じ文字を含む文字列でも、現在のスレッドのカルチャによっては異なった方法で並べ替えられる場合があります。  
  
> [!NOTE]
>  文字列を比較する場合、実行する比較の種類を明示的に指定するメソッドを使用する必要があります。  そのため、コードがより保守しやすくなり、またより読みやすくなります。  実行する比較の種類を指定できるようにするために、できるだけ、<xref:System.StringComparison> 列挙体のパラメーターを受け取る、<xref:System.String?displayProperty=fullName> クラスおよび <xref:System.Array?displayProperty=fullName> クラスのメソッドのオーバーロードを使用します。  文字列を比較する場合、`==` 演算子および `!=` 演算子の使用は避けるのが適切です。  また、<xref:System.String.CompareTo%2A?displayProperty=fullName> インスタンス メソッドの使用も避けてください。これは、オーバーロードが <xref:System.StringComparison> を受け取らないためです。  
  
## 使用例  
 ユーザーのコンピューターのロケールに基づき値が変更される文字列を正確に比較する方法を、次の例に示します。  また、C\# の*文字列インターン*機能も示します。  プログラムで 2 つ以上の同じ文字列変数を宣言すると、コンパイラはそれらをすべて同じ場所に保管します。  <xref:System.Object.ReferenceEquals%2A> メソッドを呼び出すことで、2 つの文字列がメモリ内の同じオブジェクトを実際に参照しているか確認できます。  例に示されているように、インターンを避けるために <xref:System.String.Copy%2A?displayProperty=fullName> メソッドを使用してください。  
  
 [!code-cs[csProgGuideStrings#11](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_1.cs)]  
  
## 使用例  
 <xref:System.StringComparison> 列挙体を受け取る <xref:System.String?displayProperty=fullName> メソッドを使用して文字列を比較する方法 \(推奨されている方法\) を、次の例に示します。  ここでは、<xref:System.String.CompareTo%2A?displayProperty=fullName> インスタンス メソッドは使用しません。これは、オーバーロードが <xref:System.StringComparison> を受け取らないためです。  
  
 [!code-cs[csProgGuideStrings#31](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_2.cs)]  
  
## 使用例  
 <xref:System.StringComparer?displayProperty=fullName> パラメーターを受け取る静的 <xref:System.Array> メソッドを使用したカルチャ依存の方法で、配列内の文字列を並べ替える方法および検索する方法を、次の例に示します。  
  
 [!code-cs[csProgGuideStrings#32](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_3.cs)]  
  
 <xref:System.Collections.Hashtable?displayProperty=fullName>、<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>、<xref:System.Collections.Generic.List%601?displayProperty=fullName> などのコレクション クラスには、要素またはキーの型が `string` の場合に <xref:System.StringComparer?displayProperty=fullName> パラメーターを受け取るコンストラクターがあります。  通常は、これらのコンストラクターをできるだけ使用し、`Ordinal` または `OrdinalIgnoreCase` を指定する必要があります。  
  
## 参照  
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.StringComparer?displayProperty=fullName>   
 [文字列](../../../csharp/programming-guide/strings/index.md)   
 [文字列の比較](../Topic/Comparing%20Strings%20in%20the%20.NET%20Framework.md)   
 [アプリケーションのグローバライズとローカライズ](/visual-studio/ide/globalizing-and-localizing-applications)