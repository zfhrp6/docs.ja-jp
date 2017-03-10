---
title: "Troubleshooting Data Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Char data type, converting"
  - "Decimal data type, conversions"
  - "data types [Visual Basic], troubleshooting"
  - "literals, default types"
  - "type characters, literal"
  - "Mod operator [Visual Basic], in floating-point operations"
  - "troubleshooting Visual Basic, data types"
  - "troubleshooting data types"
  - "floating-point numbers, precision"
  - "Boolean data type, converting"
  - "literal types"
  - "literal type characters"
  - "floating-point numbers, imprecision"
  - "String data type, converting"
  - "floating-point numbers, comparison"
  - "floating-point numbers"
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# Troubleshooting Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ここでは、組み込みデータ型の演算で起きる一般的な問題についていくつか説明します。  
  
## 浮動小数点式での比較が等しくならない  
 浮動小数点数 \([Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) および [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md)\) を扱うときは、数値が 2 進数の小数として格納されることに注意してください。  つまり、2 進数 \(k と n が整数である k \/ \(2 ^ n\) の形式\) ではない値は正確に格納できません。  たとえば、0.5 \(\= 1\/2\) や 0.3125 \(\= 5\/16\) は正確な値を格納できますが、0.2 \(\= 1\/5\) や 0.3 \(\= 3\/10\) は近似値のみを格納できます。  
  
 このような不正確性があるため、浮動点演算の結果が常に正確であると見なすことはできません。  特に、理論的には等しい 2 つの値が、わずかに異なる数値として表現される場合があります。  
  
||  
|-|  
|浮動小数点の値を比較するには|  
|1.  <xref:System> 名前空間にある <xref:System.Math> クラスの <xref:System.Math.Abs%2A> メソッドを使用して、2 つの数値の絶対的な差を計算します。<br />2.  許容できる最大の差を決めます。2 つの数値の差がこれより小さい場合、2 つが等価であると見なしても実用上の問題がないような値にしてください。<br />3.  差の絶対値と許容可能な差を比較します。|  
  
 次のコード例は、2 つの `Double` 値を比較する誤った方法と正しい方法を示しています。  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/visualbasic/troubleshooting-data-types_1.vb)]  
  
 この例では、<xref:System.Double> 構造体の <xref:System.Double.ToString%2A> メソッドを使用しているので、`CStr` キーワードを使用する場合より高い精度が得られます。  既定では 15 桁ですが、"G17" 形式を使うと 17 桁に拡張されます。  
  
## Mod 演算子が正確な結果を返さない  
 浮動小数点数が正確に格納されないことがあるため、オペランドの少なくとも 1 つが浮動小数点数である場合に、[Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md) が予期しない結果を返す可能性があります。  
  
 [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) は、浮動小数点表現を使用しません。  `Single` および `Double` に正確に格納されない多くの値が、`Decimal` には正確に格納されます \(たとえば 0.2 や 0.3\)。  `Decimal` に格納すると浮動小数点に格納した場合より演算は遅くなりますが、それによって得られる精度はパフォーマンスを犠牲にする価値があります。  
  
||  
|-|  
|浮動小数点数の整数剰余を求めるには|  
|1.  変数を `Decimal` で宣言します。<br />2.  リテラルの型文字 `D` を使って、強制的にリテラルを `Decimal` にします。これは、値が `Long` データ型で扱えない大きさである場合に備えるためです。|  
  
 浮動小数点数のオペランドによって誤差が生じる例を次に示します。  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/visualbasic/troubleshooting-data-types_2.vb)]  
  
 この例では、<xref:System.Double> 構造体の <xref:System.Double.ToString%2A> メソッドを使用しているので、`CStr` キーワードを使用する場合より高い精度が得られます。  既定では 15 桁ですが、"G17" 形式を使うと 17 桁に拡張されます。  
  
 `zeroPointTwo` は `Double` 型なので、0.2 を格納すると、小数部分が永久に繰り返される 0.20000000000000001 という値になります。  この値で 2.0 を除算すると、答えは 9.9999999999999995 となり、剰余が 0.19999999999999991 となります。  
  
 `decimalRemainder` の式では、リテラルの型文字 `D` が指定されているため、2 つのオペランドは 10 進型 \(`Decimal`\) になり、0.2 が正確に表現されます。  したがって、`Mod` 演算子は、予期されるとおりの剰余 0.0 を生成します。  
  
 `decimalRemainder` を `Decimal` で宣言するだけでは十分ではないことに注意してください。  強制的にリテラルを `Decimal` にすることも必要です。そうしなければ、リテラルは既定で `Double` を使用し、`decimalRemainder` は `doubleRemainder` と同じ不正確な値を受け取ります。  
  
## Boolean 型が数値型に正確に変換されない  
 [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) 値は数字としては格納されず、格納された値は数字と等しくなりません。  以前のバージョンとの互換性維持のため、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、`Boolean` 型と数値型を相互に変換するための変換用のキーワード \([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)、`CBool`、`CInt` など\) が用意されています。  ただし、他の言語では、この変換が別の方法で実行されることもあります。たとえば、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] のメソッドがそうです。  
  
 コードを作成する際、`True` および `False` に相当する数値を利用しないようにしてください。  ブール型 \(`Boolean`\) の変数に対しては、できるだけ本来の論理値だけを使用してください。  ブール型 \(`Boolean`\) と数値を混在させる必要がある場合は、選択した変換メソッドを十分理解してから行ってください。  
  
### Visual Basic における変換  
 変換用の `CType` キーワードまたは `CBool` キーワードを使って数値型を `Boolean` 型に変換すると、0 は `False` になり、それ以外のすべての値は `True` になります。  変換用のキーワードを使って `Boolean` 値を数値型に変換すると、`False` は 0 になり、`True` は \-1 になります。  
  
### フレームワークにおける変換  
 <xref:System> 名前空間にある <xref:System.Convert> クラスの <xref:System.Convert.ToInt32%2A> メソッドを使うと、`True` は \+1 に変換されます。  
  
 `Boolean` 値を数値データ型に変換する必要がある場合は、使用する変換メソッドに注意してください。  
  
## 文字リテラルがコンパイル エラーを発生させる  
 型宣言文字がない場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ではデータ型がリテラルであると見なされます。  文字リテラル \(二重引用符 \(`" "`\) で囲まれた文字\) の既定の型は、`String` です。  
  
 `String` データ型は、[Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md) に拡張されません。  つまり、リテラルを `Char` 型の変数に代入する場合には、縮小変換を行うか、強制的にリテラルを `Char` 型にする必要があります。  
  
||  
|-|  
|Char リテラルを作成して変数または定数に代入するには|  
|1.  変数または定数を `Char` で宣言します。<br />2.  文字値は二重引用符 \(`" "`\) で囲みます。<br />3.  二重引用符の後にリテラルの型文字 `C` を付けて、強制的にリテラルを `Char` 型にします。  これが必要なのは型チェック スイッチ \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) が `On` の場合ですが、常にこのようにすることを推奨します。|  
  
 次のコード例は、リテラルを `Char` 型の変数に代入する誤った方法と正しい方法を示しています。  
  
 [!CODE [VbVbalrStatements#49](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrStatements#49)]  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/visualbasic/troubleshooting-data-types_4.vb)]  
  
 縮小変換は実行時にエラーになる可能性があるため、常にリスクを伴います。  たとえば、`String` から `Char` への変換は、`String` 値が 1 文字より多い場合にエラーになります。  したがって、`C` 型文字を使う方が推奨されるプログラミング方法です。  
  
## 文字列変換が実行時にエラーになる  
 [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) が拡大変換にかかわることはめったにありません。  `String` は同じ文字列型か `Object` にしか拡大されず、`String` に拡大されるのは `Char` と `Char()` \(`Char` 配列\) だけです。  その理由は、`String` の変数および定数には、他のデータ型には格納できない値が格納できるためです。  
  
 型チェック スイッチ \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) が `On` の場合、コンパイラは、すべての暗黙の縮小変換を認めません。  これには、`String` がかかわる縮小変換も含まれます。  その場合でも、`CStr` や [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md) などの変換キーワードをコードで使用できます。これらがあると、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] は変換を試みます。  
  
> [!NOTE]
>  `For Each…Next` コレクション内の要素からループ制御変数への変換に対して縮小変換エラーが抑制されます。  詳細および例については、「[For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)」の「縮小変換」セクションを参照してください。  
  
### 縮小変換の保護  
 縮小変換の欠点は、実行時にエラーになる可能性があることです。  たとえば、`String` 変数に "True" または "False" 以外の値が格納されている場合、`Boolean` には変換できません。  区切り記号が含まれている場合は、数値型への変換はエラーになります。  変換先のデータ型で許容される値が常に `String` 変数に格納されるという確信がない限り、変換は行わないでください。  
  
 `String` から別のデータ型に変換する必要がある場合、最も安全な手順は、変換を試みる部分を [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) で囲むことです。  このようにすると、ランタイム エラーを処理することができます。  
  
### 文字配列  
 単一の `Char` と `Char` 要素の配列は、どちらも `String` に拡張されます。  しかし、`String` は `Char()` に拡張されません。  `String` 値を `Char` 配列に変換するには、<xref:System.String?displayProperty=fullName> クラスの <xref:System.String.ToCharArray%2A> メソッドを使用します。  
  
### 無意味な値  
 一般に、`String` 値は他のデータ型にとって無意味な値です。変換は不自然であり、危険です。  `String` 変数は、できるだけ本来の文字の羅列だけに使うようにしてください。  他の型でこれに相当する値に依存するコードは書かないようにしてください。  
  
## 参照  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)