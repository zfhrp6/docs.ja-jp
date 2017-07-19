---
title: "方法: 数値に先行するゼロを埋め込む | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "書式指定 [.NET Framework], 数"
  - "数値の書式指定 [.NET Framework]"
  - "数値 [.NET Framework], 書式指定文字列"
  - "数値書式指定文字列 [.NET Framework]"
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法: 数値に先行するゼロを埋め込む
整数値に先行ゼロを追加するには、精度指定子と[標準の数値書式指定文字列](../../../docs/standard/base-types/standard-numeric-format-strings.md) "D" を使用します。  整数値と浮動小数点数値の両方に先行ゼロを追加するには、[カスタム数値書式指定文字列](../../../docs/standard/base-types/custom-numeric-format-strings.md)を使用します。  このトピックでは、この両方の方法で数値に先行ゼロを埋め込む方法を説明します。  
  
### 特定の長さになるまで整数値に先行ゼロを埋め込むには  
  
1.  整数値を表示する際の最小桁数を決定します。  この数には先行桁数も含みます。  
  
2.  整数値を 10 進数値と 16 進数値のどちらで表示するかを決定します。  
  
    -   整数値を 10 進数値として表示するには、`ToString(String)` メソッドを呼び出し、パラメーターの値として文字列 "D*n*"`format` を渡します。この*n* は、文字列の最小長を表します。  
  
    -   整数値を 16 進数値として表示するには、`ToString(String)` メソッドを呼び出し、パラメーターの値として文字列 "X`format` *n*" を渡します。この*n* は、文字列の最小長を表します。  
  
     また、<xref:System.String.Format%2A> や <xref:System.Console.WriteLine%2A> など、[複合書式指定](../../../docs/standard/base-types/composite-formatting.md)を使用するメソッドでもこの書式指定文字列を使用できます。  
  
 次の例は、書式指定された数値全体の長さが 8 文字以上になるように、先行ゼロを使用してさまざまな数値を書式指定します。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### 特定の数の先行ゼロを整数値に埋め込むには  
  
1.  整数値に表示する先行ゼロの数を決定します。  
  
2.  整数値を 10 進数値と 16 進数値のどちらで表示するかを決定します。  10 進数値として書式指定する場合には標準書式指定子 "D" を使用する必要があります。16 進数値として書式指定する場合には標準書式指定子 "X" を使用する必要があります。  
  
3.  整数値の `ToString("D").Length` メソッドまたは `ToString("X").Length` メソッドを使用して、先行ゼロが埋め込まれていない数値文字列の長さを決定します。  
  
4.  書式指定した文字列に埋め込む先行ゼロの数を、埋め込まれていない数値の文字列の長さに加算します。  これにより、埋め込み文字列全体の長さが定義されます。  
  
5.  整数値の `ToString(String)` メソッドを呼び出し、10 進数値文字列の場合は "D*n*"、16 進数値の場合は "X*n*" を渡します。*n* は埋め込み文字列全体の長さを表します。  書式指定文字列 "D*n*" または "X*n*"は、複合書式指定をサポートするメソッドでも使用できます。  
  
 次の例は、整数値に 5 つの先行ゼロを埋め込みます。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### 特定の長さになるまで数値に先行ゼロを埋め込むには  
  
1.  文字列形式の数値の整数部分の桁数を決定します。  合計桁数には先行ゼロも含みます。  
  
2.  ゼロの最小数を表すゼロ プレースホルダー \("0"\) を使用するカスタム数値書式指定文字列を定義します。  
  
3.  数値の `ToString(String)` メソッドを呼び出し、カスタム書式指定文字列を渡します。  カスタム書式指定文字列は、複合書式指定をサポートしているメソッドでも使用できます。  
  
 次の例は、書式指定された数値全体の長さが 8 文字以上の整数になるように、先行ゼロを使用してさまざまな数値を書式指定します。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### 特定の数の先行ゼロを数値に埋め込むには  
  
1.  数値に埋め込む先行ゼロの数を決定します。  
  
2.  埋め込みのない数値文字列での整数部の桁数を決定します。  この操作を行うには、次の手順を実行します。  
  
    1.  文字列形式の数値に小数点が含まれるかどうかを決定します。  
  
    2.  小数点記号を含める場合は、整数部分の文字数を決定します。  
  
         または  
  
         小数点記号を含めない場合は、文字列の長さを決定します。  
  
3.  文字列に表示する各先行ゼロの位置にゼロ プレースホルダー \("0"\) を使用し、既定の文字列の各桁の位置にゼロ プレースホルダーまたは桁プレースホルダー \("\#"\) を使用するカスタム書式指定文字列を作成します。  
  
4.  数値の `ToString(String)` メソッド、または複合書式指定をサポートするメソッドのパラメーターとして、カスタム書式指定文字列を指定します。  
  
 次の例は、2 つの <xref:System.Double> 値を 5 つの先行ゼロで埋め込みます。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## 参照  
 [カスタム数値書式指定文字列](../../../docs/standard/base-types/custom-numeric-format-strings.md)   
 [標準の数値書式指定文字列](../../../docs/standard/base-types/standard-numeric-format-strings.md)   
 [複合書式指定](../../../docs/standard/base-types/composite-formatting.md)