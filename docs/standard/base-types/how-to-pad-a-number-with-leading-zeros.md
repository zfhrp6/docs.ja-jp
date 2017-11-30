---
title: "方法: 数値に先行するゼロを埋め込む"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6266807a01e8119ae1410a1ba09cab55c788b4d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>方法: 数値に先行するゼロを埋め込む
整数値に先行ゼロを追加するには、精度指定子と[標準の数値書式指定文字列](../../../docs/standard/base-types/standard-numeric-format-strings.md) "D" を使用します。 整数値と浮動小数点数値の両方に先行ゼロを追加するには、[カスタム数値書式指定文字列](../../../docs/standard/base-types/custom-numeric-format-strings.md)を使用します。 このトピックでは、この両方の方法で数値に先行ゼロを埋め込む方法を説明します。  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>特定の長さになるまで整数値に先行ゼロを埋め込むには  
  
1.  整数値を表示する際の最小桁数を決定します。 この数には先行桁数も含みます。  
  
2.  整数値を 10 進数値と 16 進数値のどちらで表示するかを決定します。  
  
    -   表示するには、整数、10 進値として呼び出すその`ToString(String)`メソッド、およびパス、文字列"D*n*"の値として、`format`パラメーター、場所 *n* 文字列の最小の長さを表します。  
  
    -   表示するには、整数の 16 進数値として呼び出すその`ToString(String)`メソッドと、文字列のパス"X*n*"の値として、`format`パラメーター、場所 *n* 文字列の最小の長さを表します。  
  
     などもメソッドでは、この書式指定文字列を使用することができます<xref:System.String.Format%2A>または<xref:System.Console.WriteLine%2A>を使用して[複合書式指定](../../../docs/standard/base-types/composite-formatting.md)です。  
  
 次の例は、書式指定された数値全体の長さが 8 文字以上になるように、先行ゼロを使用してさまざまな数値を書式指定します。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>特定の数の先行ゼロを整数値に埋め込むには  
  
1.  整数値に表示する先行ゼロの数を決定します。  
  
2.  整数値を 10 進数値と 16 進数値のどちらで表示するかを決定します。 10 進数値として書式指定する場合には標準書式指定子 "D" を使用する必要があります。16 進数値として書式指定する場合には標準書式指定子 "X" を使用する必要があります。  
  
3.  整数値の `ToString("D").Length` メソッドまたは `ToString("X").Length` メソッドを使用して、先行ゼロが埋め込まれていない数値文字列の長さを決定します。  
  
4.  書式指定した文字列に埋め込む先行ゼロの数を、埋め込まれていない数値の文字列の長さに加算します。 これにより、埋め込み文字列全体の長さが定義されます。  
  
5.  整数値を呼び出す`ToString(String)`メソッド、およびパス文字列"D*n*"10 進数文字列のおよび"X*n*"16 進数文字列の場合、  *n*埋め込み文字列全体の長さを表します。 使用することも、"D*n*"または"X*n*"複合書式指定をサポートするメソッドに文字列の書式を設定します。  
  
 次の例は、整数値に 5 つの先行ゼロを埋め込みます。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>特定の長さになるまで数値に先行ゼロを埋め込むには  
  
1.  文字列形式の数値の整数部分の桁数を決定します。 合計桁数には先行ゼロも含みます。  
  
2.  ゼロの最小数を表すゼロ プレースホルダー ("0") を使用するカスタム数値書式指定文字列を定義します。  
  
3.  数値の `ToString(String)` メソッドを呼び出し、カスタム書式指定文字列を渡します。 カスタム書式指定文字列は、複合書式指定をサポートしているメソッドでも使用できます。  
  
 次の例は、書式指定された数値全体の長さが 8 文字以上の整数になるように、先行ゼロを使用してさまざまな数値を書式指定します。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>特定の数の先行ゼロを数値に埋め込むには  
  
1.  数値に埋め込む先行ゼロの数を決定します。  
  
2.  埋め込みのない数値文字列での整数部の桁数を決定します。 この操作を行うには、次の手順を実行します。  
  
    1.  文字列形式の数値に小数点が含まれるかどうかを決定します。  
  
    2.  小数点記号を含める場合は、整数部分の文字数を決定します。  
  
         または  
  
         小数点記号を含めない場合は、文字列の長さを決定します。  
  
3.  文字列に表示する各先行ゼロの位置にゼロ プレースホルダー ("0") を使用し、既定の文字列の各桁の位置にゼロ プレースホルダーまたは桁プレースホルダー ("#") を使用するカスタム書式指定文字列を作成します。  
  
4.  数値の `ToString(String)` メソッド、または複合書式指定をサポートするメソッドのパラメーターとして、カスタム書式指定文字列を指定します。  
  
 次の例は、2 つの <xref:System.Double> 値を 5 つの先行ゼロで埋め込みます。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a>関連項目  
 [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [複合書式指定](../../../docs/standard/base-types/composite-formatting.md)
