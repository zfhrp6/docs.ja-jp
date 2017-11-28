---
title: "string (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 87df2b158b173072aad5257594e1b1482ae61067
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="string-c-reference"></a>string (C# リファレンス)
`string` 型は、0 個以上の Unicode 文字のシーケンスを表します。 `string` は、.NET Framework の <xref:System.String> のエイリアスです。  
  
 `string` は参照型ですが、等値演算子 (`==` および `!=`) は、`string` オブジェクトの参照ではなく、値を比較するように定義されています。 これにより、文字列が等しいかを直感的にテストできます。 例:  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 文字列の内容が等しいので、"True"、"False" の順に表示されますが、`a` および `b` は同じ文字列インスタンスを参照しません。  
  
 + 演算子は、文字列を連結します。  
  
```csharp  
string a = "good " + "morning";  
```  
  
 これは、"good morning" を含む文字列オブジェクトを作成します。  
  
 文字列は "*変更不可*" です。文字列オブジェクトの作成後、そのコンテンツを変更することはできません。構文では変更可能に見えても、変更不可です。 たとえば、このコードを作成すると、コンパイラによって新しい文字列オブジェクトを格納する新しいシーケンス オブジェクトが生成され、その新しいオブジェクトが b に割り当てられます。 そして、文字列 "h" がガベージ コレクションの対象になります。  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 [] 演算子は、`string` の各文字への読み取り専用アクセスに使用できます。  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 リテラル文字列は `string` 型であり、二重引用符で囲む形式と、@-quoted 形式の 2 とおりがあります。 二重引用符で囲む場合は、リテラル文字列の前後に二重引用符 (") を付けます。  
  
```csharp  
"good morning"  // a string literal  
```  
  
 リテラル文字列には、任意の文字リテラルを含めることができます。 これにはエスケープ シーケンスが含まれます。 次の例では、円記号にエスケープ シーケンス `\\`、文字 f に `\u0066`、改行に `\n` を使用しています。  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  エスケープ コード `\udddd` (`dddd` は 4 桁の数字) は、Unicode 文字 U +`dddd` を表します。 8 桁の Unicode エスケープ コード `\Udddddddd` も認識できます。  
  
 verbatim 文字列リテラルの場合は、先頭に @ を付け、さらに前後に二重引用符を付けます。 例:  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 verbatim 文字列の場合の利点は、エスケープ シーケンスが "*処理されない*" ため、たとえば、完全修飾ファイル名が書きやすくなることです。  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 @-quoted 文字列に二重引用符を含めるには、二重引用符を二重にします。  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 また、C# キーワードである参照 ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) 識別子を使用する場合も、@ 記号を使用します。  
  
 C# での文字列の詳細については、「[文字列](../../../csharp/programming-guide/strings/index.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [文字列を使用するためのベスト プラクティス](../../../standard/base-types/best-practices-strings.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)  
 [値型](../../../csharp/language-reference/keywords/value-types.md)  
 [基本的な文字列操作](../../../standard/base-types/basic-string-operations.md)  
 [新しい文字列の作成](../../../standard/base-types/creating-new.md)  
 [数値結果テーブルの書式設定](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
