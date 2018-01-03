---
title: "密結合クライアント サーバー アプリケーションと LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a2fa902cfbea3c6eb15e1832231bb3ed83de5497
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>密結合クライアント サーバー アプリケーションと LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]プレゼンテーション層の密結合のスマート クライアントと中間層で使用できます。 読み取り専用データ アクセス、オプティミスティック同時実行チェックなし、またはタイムスタンプを使用したオプティミスティック同時実行のシナリオの場合、非リモートのシナリオに比べて複雑さはほぼ同じです。 しかし、元の値を使用したオプティミスティック同時実行チェックをデータベースで行う必要がある場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は DataSet のようなレベルのデータ ラウンド トリップをサポートしません。 ただし、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中間層は任意のプラットフォーム上のクライアントとの間でデータをやり取りできます。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)][!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)]クライアントにシリアル化された後に、エンティティの状態を追跡するためのインフラストラクチャを提供されません。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ここで、データ層とプレゼンテーション層の間のやり取りは、小さな比較的アトミックなサービス指向アーキテクチャのできますが、元の値の任意のラウンド トリップは行われません。 このため、密結合のスマート クライアントを [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] と共に使用し、元の値を使ったオプティミスティック同時実行制御をデータベースで行う場合には、プレゼンテーション層と中間層の間で変更内容を通信するための独自の機構を実装する必要があります。 中間層で [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用することの利点を考慮に入れて、この余分の作業を行うかどうかは、システム設計者の判断に任せられます。 一方、データベースでタイムスタンプを使用する場合には、変更追跡用のカスタム ロジックは必要ありません。  
  
## <a name="see-also"></a>参照  
 [LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [Web サービスを使用した LINQ to SQL N 層](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [n 層アプリケーションでのデータセットの操作](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)
