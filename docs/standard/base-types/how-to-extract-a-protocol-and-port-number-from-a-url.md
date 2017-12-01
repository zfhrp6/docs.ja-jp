---
title: "方法 : URL からプロトコルとポート番号を抽出する"
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
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10ab05ac8b24c0658be2f27809137c6b0bd4834f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>方法 : URL からプロトコルとポート番号を抽出する
次の例では、URL からプロトコルとポート番号を抽出します。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>プロトコルを返すメソッドに続けてコロンの後にポート番号。  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 この正規表現パターン `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` の解釈を次の表に示します。  
  
|パターン|説明|  
|-------------|-----------------|  
|`^`|文字列の先頭から照合を開始します。|  
|`(?<proto>\w+)`|1 つ以上の単語文字に一致します。 このグループの名前を付けます`proto`です。|  
|`://`|後に 2 つのスラッシュ記号が続くコロンと一致します。|  
|`[^/]+?`|スラッシュ記号以外の任意の文字の 1 回以上の (ただし、可能な限り少ない) 出現と一致します。|  
|`(?<port>:\d+)?`|後に 1 桁以上の文字が続くコロンの 0 回または 1 回の出現と一致します。 このグループの名前を付けます`port`です。|  
|`/`|スラッシュ記号に一致します。|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>メソッドを展開、`${proto}${port}`置換シーケンスは、正規表現パターン内でキャプチャされた 2 つの名前付きグループの値を連結します。 代わりに使用する明示的にによって返されるコレクション オブジェクトから取得された文字列を連結するのには、<xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>プロパティです。  
  
 この例では、 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> 2 つの代替文字列を持つメソッド`${proto}`と`${port}`、出力文字列に、キャプチャされたグループを含める。 キャプチャされたグループを取得するにはパターン一致から<xref:System.Text.RegularExpressions.GroupCollection>オブジェクトの代わりに、コードを次に示します。  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [.NET の正規表現](../../../docs/standard/base-types/regular-expressions.md)
