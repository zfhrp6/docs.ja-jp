---
title: "挿入文字列 (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b8a1fe0be82a0e09d61c66ed463199ff626c9faa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="interpolated-strings-c-reference"></a>挿入文字列 (C# リファレンス)

文字列の作成に使用されます。  挿入文字列は、*挿入式*が含まれているテンプレート文字列のように見えます。  挿入文字列は、含まれる挿入式をその文字列表現に置き換えた文字列を返します。 この機能は、C# 6 およびそれ以降のバージョンで使用できます。

挿入文字列の引数は、[複合書式指定文字列](../../../standard/base-types/composite-formatting.md#composite-format-string)よりもわかりやすいものです。  たとえば、挿入文字列には、  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
'{name}' の 2 つの補間式を含む、' {時間: hh}'。 同等の複合書式指定文字列は次のとおりです。

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

挿入文字列の構造は次のとおりです。  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

ここで、 

- *field-width* はフィールドの文字数を示す符号付き整数です。 これが正である場合、フィールドは右揃えとなり、負である場合は左揃えとなります。 

- *format-string* は、書式設定されるオブジェクトの種類に適した書式指定文字列です。 たとえば、<xref:System.DateTime> の値の場合、"D" または "d" などの、標準の日付と時刻の書式指定文字列になる可能性があります。

> [!IMPORTANT]
> 間の空白を持つことはできません、`$`と`"`文字列を開始します。 これにより、コンパイル時エラーが発生します。

 文字列リテラルを使用できる場所であればどこでも補間文字列を使用できます。  この挿入文字列は、挿入文字列を含むコードが実行されるたびに評価されます。 これにより、挿入文字列の定義と評価を分離することができます。  
  
 挿入文字列に中かっこ "{" または "}" を含めるには、2 つの中かっこ "{{" または "}}" を使用します。  詳細については、「暗黙の型変換」を参照してください。  

挿入文字列には、引用符 (")、コロン (:)、コンマ (,) など、特別な意味を持つその他の文字が含まれることがあります。これらの文字がリテラル テキストに出現する場合は、エスケープする必要があります。また、これらの文字が言語要素として挿入式に含まれる場合は、かっこで区切られた式に含める必要があります。 次の例では、引用符をエスケープして、結果文字列に引用符を含めています。さらに、かっこを使用して式 `(age == 1 ? "" : "s")` を区切り、コロンが書式指定文字列の先頭として解釈されないようにしています。

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

使用される文字列は逐語的補間、`$`文字が続く、`@`文字です。 逐語的文字列の詳細については、次を参照してください。、[文字列](string.md)トピックです。 次のコードでは、逐語的補間文字列を使用して、前のスニペットの変更済みバージョンを示します。

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

逐語的文字列に従っていないために、書式設定の変更が必要な`\`エスケープ シーケンスです。

> [!IMPORTANT]
> `$`トークンは、前に指定する必要があります、`@`逐語的補間文字列でトークンです。


## <a name="implicit-conversions"></a>暗黙の型変換  

挿入文字列から暗黙の型変換を行う方法は 3 種類あります。  

1. 挿入文字列から <xref:System.String> への変換。 次の例では、挿入文字列式を文字列表現で置き換えた文字列が返されます。 例:

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   これが、文字列解釈の最終的な結果です。 二重中かっこ ("{{" および "}}") のすべての発生箇所は、単一の中かっこに変換されます。 

2. 挿入文字列から <xref:System.IFormattable> 変数への変換。これは、単一の <xref:System.IFormattable> インスタンスから、カルチャ固有のコンテンツを持った複数の結果文字列の作成を可能にするものです。 これは、個々のカルチャに適切な数値書式や日付形式などの情報を含めるのに便利です。  二重中かっこ ("{{" および "}}") のすべての出現箇所は、明示的または暗黙的に <xref:System.Object.ToString> メソッドを呼び出して文字列を書式指定するまで、二重中かっこのままです。  含まれるすべての補間式は、{0}、\{1\} などに変換されます。  

   次の例では、リフレクションを使用することで、挿入文字列から作成された <xref:System.IFormattable> 変数のフィールドおよびプロパティ値だけでなく、メンバーも表示しています。 渡しても、<xref:System.IFormattable>変数を<xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>メソッドです。

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   挿入文字列の検査には、リフレクションを使用する必要があることに注意してください。 かどうか、メソッドなどの書式設定文字列に渡されます<xref:System.Console.WriteLine(System.String)>の書式指定項目は解決され、結果の文字列が返されます。 

3. 挿入文字列から複合書式指定文字列を表す <xref:System.FormattableString> 変数への変換。 たとえば、複合書式指定文字列を検査し、それが結果文字列としてどのように表示されるかを検査すると、クエリを構築する場合にインジェクション攻撃を防ぐことができます。 <xref:System.FormattableString> には、<xref:System.Globalization.CultureInfo.InvariantCulture> と <xref:System.Globalization.CultureInfo.CurrentCulture> の結果文字列を生成できる <xref:System.FormattableString.ToString> オーバーロードも含まれています。  二重中かっこ ("{{" および "}}") のすべての出現箇所は、書式指定するまで二重中かっこのままです。  含まれるすべての補間式は、{0}、\{1\} などに変換されます。  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a>言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
