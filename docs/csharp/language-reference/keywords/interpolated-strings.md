---
title: "補間文字列 (C# および Visual Basic リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 補間文字列 (C# および Visual Basic リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

文字列の作成に使用されます。  補間文字列式は、式が含まれているテンプレート文字列のように見えます。  補間文字列式は、含まれる式を式の結果の ToString 表現に置き換えることで文字列を作成します。  引数に関しては、補間文字列は[複合書式指定](../Topic/Composite%20Formatting.md)より理解しやすいです。  補間文字列の例を次に示します。  
  
```c#  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")  
```  
  
 補間文字列の構造は、次のとおりです。  
  
```  
$ " <text> { <interpolation-expression> <optional-comma-field-width> <optional-colon-format> } <text> ... } "  
```  
  
 文字列リテラルを使用できる場所であればどこでも補間文字列を使用できます。  プログラムを実行すると、補間文字列リテラルを含むコードが実行されることになる場合、コードは補間式を評価することによって新しい文字列リテラルを算出します。  この計算は、補間文字列を含むコードが実行されるたびに発生します。  
  
 補間文字列に中かっこ "{" または "}" を含めるには、2 つの中かっこ "{{" または "}}" を使用します。  詳細については、「暗黙の型変換」を参照してください。  
  
## 暗黙の型変換  
 補間文字列からの暗黙的な型変換があります。  
  
```c#  
var s = $"hello, {name}" System.IFormattable s = $"Hello, {name}" System.FormattableString s = $"Hello, {name}"  
  
```  
  
 最初の例では、`string` 値を生成します。すべての文字列の補間値は既に計算されています。  この値は、最終的な結果であり、文字列型が含まれています。  二重中かっこ “{{“ および “}}” のすべての発生箇所は、単一の中かっこに変換されます。  
  
 2 番目の例では、インバリアント コンテキストを含む文字列に変換できる <xref:System.IFormattable> 変数を生成します。  これは、異なる言語で正しい数値形式とデータ形式を取得するのに役立ちます。  二重中かっこ “{{“ および “}}” のすべての出現箇所は、ToString を使って文字列を書式指定するまで、二重中かっこのままです。  含まれるすべての補間式は、{0}、\\{1\\} などに変換されます。  
  
```c#  
s.ToString(null, System.Globalization.CultureInfo.InvariantCulture);  
```  
  
 3 番目の例では、補間の計算によって作成されるオブジェクトを検査できるようにする <xref:System.FormattableString> を生成します。  たとえば、オブジェクトを検査し、それらが文字列としてどのように表示されるかを検査することにより、クエリを構築する場合に、インジェクション攻撃から保護されます。<xref:System.FormattableString> を使用することによって、InvariantCulture および CurrentCulture の文字列の結果の生成を簡単に操作できます。  二重中かっこ “{{“ および “}}” のすべての出現箇所は、書式指定するまで二重中かっこのままです。  含まれるすべての補間式は、{0}、\\{1\\} などに変換されます。  
  
## 例  
  
```c#  
$"Name = {name}, hours = {hours:hh}" var s = $"hello, {name}" System.IFormattable s = $"Hello, {name}" System.FormattableString s = $"Hello, {name}" $"{person.Name, 20} is {person.Age:D3} year {(p.Age == 1 ? "" : "s")} old."  
  
```  
  
 補間文字列式が $ で始まり、コンマ、コロン、または閉じ中かっこを検出するまで、コンパイラがそれに含まれる補間式をバランスの取れたテキストとしてスキャンするので、含まれる補間式内の引用符を引用する必要はありません。同じ理由から、最後の例では、書式指定をコロンで開始せずに、かっこを使用して条件式 \(`p.Age == 1 ? "" : "s"`\) を補間式に含めることができるようにします。含まれる補完式の外部 \(ただし、補間文字列式の内部\) では、通常通り、引用符をエスケープします。  
  
## 構文  
  
```  
expression: interpolated-string-expression interpolated-string-expression: interpolated-string-start interpolations interpolated-string-end interpolations: single-interpolation single-interpolation interpolated-string-mid interpolations single-interpolation: interpolation-start interpolation-start : regular-string-literal interpolation-start: expression expression , expression  
  
```  
  
## 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 詳細については、「[Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)」を参照してください。  
  
## 参照  
 <xref:System.IFormattable?displayProperty=fullName>   
 <xref:System.FormattableString?displayProperty=fullName>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)   
 [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)