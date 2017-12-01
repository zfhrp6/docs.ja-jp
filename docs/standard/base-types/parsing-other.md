---
title: ".NET の他の文字列の解析"
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
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: edd48993f50ec8b91ba7941a682d7de9f22aa12e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-other-strings-in-net"></a>.NET の他の文字列の解析
数値だけでなく、 <xref:System.DateTime> 、文字列型を表す文字列も解析できる<xref:System.Char>、<xref:System.Boolean>と<xref:System.Enum>データ型にします。  
  
## <a name="char"></a>Char  
 **Char** データ型に関連付けられている静的解析メソッドは、1 つの文字を含む文字列をUnicode 値に変換するのに便利です。 次のコードの例では、文字列を Unicode 文字に解析します。  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>ブール型  
 **ブール**データ型が含まれています、**解析**メソッドを実際にブール値を表す文字列を変換に使用できる**ブール**型です。 このメソッドは大文字と小文字を区別しません。また、"True" または "False" を含む文字列を正常に解析することができます。 **解析**メソッドに関連付けられている、**ブール**型は、空白文字で囲まれた文字列を解析もできます。 その他の文字列が渡された場合、<xref:System.FormatException>がスローされます。  
  
 次のコード例では、**解析**ブール値を文字列に変換します。  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>列挙  
 静的 **Parse** メソッドを使用して、列挙型を文字列の値に初期化できます。 このメソッドは、解析は、列挙型、文字列解析、および解析が大文字小文字を区別するかどうかどうかを示すブール型の省略可能なフラグを受け取ります。 解析している文字列は、コンマで区切られた複数の値を含めることができます。これは、1 つ以上の空の領域 (空白とも呼ばれます) が前後にある場合があります。 文字列に複数の値がある場合、返されたオブジェクトの値は、ビット演算 OR 演算と組み合わされたすべての指定された値の値です。  
  
 次の例では、**解析**列挙値を文字列形式に変換します。 <xref:System.DayOfWeek>列挙体に初期化**木曜日**文字列からです。  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>関連項目  
 [文字列の解析](../../../docs/standard/base-types/parsing-strings.md)  
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)  
 [.NET における型変換](../../../docs/standard/base-types/type-conversion.md)
