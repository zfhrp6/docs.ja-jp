---
title: "string (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "string"
  - "string_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "文字列 [C#]、リファレンス"
  - "@ リテラル文字列"
  - "リテラル文字列 [C#]"
  - "string キーワード [C#]"
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# string (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`string` 型は、Unicode 文字のシーケンスを表します。文字数がゼロの場合もあります。   `string` は、.NET Framework の <xref:System.String> のエイリアスです。  
  
 `string` は参照型ですが、等値演算子 \(`==` および `!=`\) は、`string` オブジェクトの参照ではなく、値を比較するように定義されます。  値を比較することで、文字列が等しいかを直感的にテストできます。  次に例を示します。  
  
```c#  
  
      string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 文字列の内容が等しいので、"True"、"False" の順に表示されますが、`a` および `b` は同じ文字列インスタンスを参照しません。  
  
 \+ 演算子は、文字列を連結します。  
  
```c#  
  
string a = "good " + "morning";  
```  
  
 これは、"good morning" を含む文字列オブジェクトを作成します。  
  
 文字列は*変更不可*です。文字列オブジェクトの作成後、そのコンテンツを変更することはできません。構文では変更可能に見えても、変更不可です。  たとえば、このコードを作成すると、コンパイラは新しい文字列オブジェクトを格納する新しいシーケンス オブジェクトを生成し、その新しいオブジェクトが b に代入されます。  文字列 "h" がガベージ コレクションの対象になります。  
  
```c#  
  
      string b = "h";  
b += "ello";  
```  
  
 \[\] 演算子は、`string` の各文字への読み取り専用アクセスに使用できます。  
  
```c#  
  
      string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 リテラル文字列は `string` 型であり、二重引用符で囲む形式と、@ と二重引用符で囲む形式の 2 とおりがあります。  二重引用符で囲む場合は、リテラル文字列の前後に二重引用符 \("\) を付けます。  
  
```c#  
"good morning"  // a string literal  
```  
  
 リテラル文字列には、任意の文字リテラルを含めることができます。  これにはエスケープ シーケンスが含まれます。  次の例では、円記号にエスケープ シーケンス `\\`、文字 f に`\u0066`、改行に `\n` を使用しています。  
  
```  
  
      string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  エスケープ コード `\`u`dddd` \(`dddd` は 4 桁の数字\) は、Unicode 文字 U \+ `dddd` を表します。  8 桁の Unicode エスケープ コード `\Udddddddd` も認識できます。  
  
 逐語的リテラル文字列の場合は、先頭に @ を付け、さらに前後に二重引用符を付けます。  次に例を示します。  
  
```c#  
@"good morning"  // a string literal  
```  
  
 逐語的文字列の場合の利点は、エスケープ シーケンスが処理されないため、たとえば、完全修飾ファイル名が書きやすくなることです。  
  
```c#  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 @ と二重引用符で囲まれた文字列中に二重引用符を含めるには、二重引用符を二重にします。  
  
```c#  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 また、C\# キーワードである参照 \([\/reference \(メタデータのインポート\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)\) 識別子を使用する場合も、@ 記号を使用します。  
  
 C\# での文字列の詳細については、「[文字列](../../../csharp/programming-guide/strings/index.md)」を参照してください。  
  
## 使用例  
 [!CODE [csrefKeywordsTypes#17](../CodeSnippet/VS_Snippets_VBCSharp/csrefKeywordsTypes#17)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [文字列を使用するためのベスト プラクティス](../Topic/Best%20Practices%20for%20Using%20Strings%20in%20the%20.NET%20Framework.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)   
 [値型](../../../csharp/language-reference/keywords/value-types.md)   
 [基本的な文字列操作](../Topic/Basic%20String%20Operations%20in%20the%20.NET%20Framework.md)   
 [新しい文字列の作成](../Topic/Creating%20New%20Strings%20in%20the%20.NET%20Framework.md)   
 [数値結果テーブルの書式設定](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)