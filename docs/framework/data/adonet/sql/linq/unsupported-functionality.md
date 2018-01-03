---
title: "サポートされていない機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 244d9ee7accd3686729542d0f0a15966bcde7b78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="unsupported-functionality"></a>サポートされていない機能
LINQ to SQL では、次の SQL 機能は、既存の共通言語ランタイム (CLR) および .NET Framework の構成要素の変換からは公開できません。  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     `LIKE` は直接変換によってサポートされませんが、同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。 詳細については、「<xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>」を参照してください。  
  
-   `DATEDIFF`  
  
     LINQ to SQL では、`DATEDIFF` のサポートが制限されています。 同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。  
  
-   `ROUND`  
  
     LINQ to SQL では、`ROUND` のサポートが制限されています。 詳細については、次を参照してください。 [System.Math メソッド](system-math-methods.md)です。  
  
## <a name="see-also"></a>参照  
 [データ型と関数](data-types-and-functions.md)
