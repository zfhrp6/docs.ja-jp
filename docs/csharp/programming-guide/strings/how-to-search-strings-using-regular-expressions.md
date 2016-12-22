---
title: "方法 : 正規表現を使用して文字列を検索する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "検索 (文字列を) [C#]"
  - "文字列 [C#]、検索 (正規表現を使用して)"
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : 正規表現を使用して文字列を検索する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

文字列の検索には、<xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> クラスを使用できます。  単純な検索から、正規表現を活用した複雑な検索まで、さまざまな検索があります。  <xref:System.Text.RegularExpressions.Regex> クラスを使用して文字列を検索する 2 つの例を次に示します。  詳細については、「[.NET Framework の正規表現](../Topic/.NET%20Framework%20Regular%20Expressions.md)」を参照してください。  
  
## 使用例  
 次のコードは、大文字と小文字を区別せずに配列の文字列を単純に検索するコンソール アプリケーションです。  静的メソッド <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> では、検索する文字列と、検索パターンを含む文字列を前提として、検索を実行します。  この場合、3 つ目の引数は、大文字と小文字の区別を無視することを示します。  詳細については、「<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>」を参照してください。  
  
 [!code-cs[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## 使用例  
 次のコードは、正規表現を使用して、配列の各文字列の形式を検証するコンソール アプリケーションです。  各文字列が電話番号の形式であることが検証されます。つまり、3 グループの数値がダッシュで区切られ、最初の 2 グループには 3 桁の数値が含まれ、3 つ目のグループには 4 桁の数値が含まれることが検証されます。  この操作は、正規表現 `^\\d{3}-\\d{3}-\\d{4}$` を使用して実行されます。  詳細については、「[正規表現言語 \- クイック リファレンス](../Topic/Regular%20Expression%20Language%20-%20Quick%20Reference.md)」を参照してください。  
  
 [!code-cs[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## 参照  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [文字列](../../../csharp/programming-guide/strings/index.md)   
 [.NET Framework の正規表現](../Topic/.NET%20Framework%20Regular%20Expressions.md)   
 [正規表現言語 \- クイック リファレンス](../Topic/Regular%20Expression%20Language%20-%20Quick%20Reference.md)