---
title: ".NET Framework 型の文字列への変換"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c3abe140e62f112a15a1ad1b1b2a79c14364b26d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="converting-net-framework-types-to-strings"></a>.NET Framework 型の文字列への変換
.NET Framework の型を文字列に変換する場合を使用して、 **ToString**メソッドです。 **ToString**メソッドに渡される型の文字列形式を返します。 XML スキーマ (XSD) 仕様に対応する形式で文字列を返す .NET Framework 型を、次の表に示します。  
  
|.NET Framework 型|返される文字列型|  
|-------------------------|--------------------------|  
|Boolean|"true"、"false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|形式は、yyyy-MM-ddTHH:mm:sszzzzzz およびそのサブセットです。|  
|Timespan|PnYnMnTnHnMnS の形式。たとえば、`P2Y10M15DT10H30M20S` は 2 年 10 か月 15 日 10 時間 30 分 20 秒の期間です。|  
  
## <a name="see-also"></a>関連項目  
 [XML データ型の変換](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [.NET Framework データ型を文字列に変換します。](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
