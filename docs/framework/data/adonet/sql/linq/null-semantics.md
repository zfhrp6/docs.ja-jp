---
title: "null セマンティクス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8d32f73c8c2095c23ec164ad40fd1ab27ef1153a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="null-semantics"></a>null セマンティクス
次の表では、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ドキュメントで `null` (`Nothing` では [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) について説明している各部分へのリンクを示します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[SQL と CLR の型の不一致](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|このトピックの「null セマンティクス」セクションでは、3 つの状態を持つ SQL のブール値と、2 つの状態を持つ共通言語ランタイム (CLR: Common Language Runtime) の <xref:System.Boolean>、 `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)])、 `null` (C#)、および関連するその他の話題について説明します。|  
|[標準クエリ演算子の変換](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|このトピックの「null セマンティクス」セクションでは、 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]での null の比較のセマンティクスについて説明します。|  
|[System.String メソッド](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|このトピックの「.NET との相違」セクションでは、 <xref:System.String.LastIndexOf%2A> の戻り値が 0 の場合に、文字列が null の場合と、見つかった位置が 0 の場合の両方があることについて説明します。|  
|[数値のシーケンスの合計の計算](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|null のみを含むシーケンス、または空のシーケンスの場合に、 <xref:System.Linq.Enumerable.Sum%2A> 演算子が 0 ではなく `null` (`Nothing` では [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) に評価されることについて説明します。|  
  
## <a name="see-also"></a>参照  
 [データ型と関数](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
