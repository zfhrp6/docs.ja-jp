---
title: ".NET における文字列の解析"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 811db42e04e73d7acbc03e303297b19fdf643384
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-strings-in-net"></a>.NET における文字列の解析
解析操作では、.NET の基本データ型を表す文字列をその基本データ型に変換します。 たとえば解析操作は、文字列を浮動小数点数や日付と時刻の値に変換するために使用します。 解析操作を実行するには、`Parse` メソッドがよく使用されます。 解析は書式設定の逆の操作 (基本データ型のその文字列形式への変換を含む) であるため、多くの同じ規則が適用されます。 実装するオブジェクトを使用して書式設定と同様、<xref:System.IFormatProvider>インターフェイスを実装するオブジェクトの使用の解析もカルチャの書式情報を提供する、<xref:System.IFormatProvider>文字列表現を解釈する方法を決定するインターフェイス. 詳細については、次を参照してください。[型の書式設定](../../../docs/standard/base-types/formatting-types.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [数値文字列の解析](../../../docs/standard/base-types/parsing-numeric.md)  
 文字列を .NET 型の数値に変換する方法について説明します。  
  
 [日付と時刻文字列の解析](../../../docs/standard/base-types/parsing-datetime.md)  
 文字列を .NET に変換する方法について説明**DateTime**型です。  
  
 [その他の文字列の解析](../../../docs/standard/base-types/parsing-other.md)  
 文字列に変換する方法について説明します**Char**、**ブール**、および**Enum**型です。  
  
## <a name="related-sections"></a>関連項目  
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)  
 書式指定子と書式プロバイダーのような基本的な書式の概念について説明します。  
  
 [.NET での型変換](../../../docs/standard/base-types/type-conversion.md)  
 型に変換する方法をについて説明します。  
  
 [基本データ型](../../../docs/standard/base-types/index.md)  
 .NET の基本型で実行できる一般的な操作をについて説明します。
