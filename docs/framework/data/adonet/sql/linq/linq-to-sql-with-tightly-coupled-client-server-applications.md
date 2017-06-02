---
title: "LINQ to SQL with Tightly-Coupled Client-Server Applications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# LINQ to SQL with Tightly-Coupled Client-Server Applications
プレゼンテーション層の密結合スマート クライアントと共に、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を中間層で使用することができます。  読み取り専用データ アクセス、オプティミスティック同時実行チェックなし、またはタイムスタンプを使用したオプティミスティック同時実行のシナリオの場合、非リモートのシナリオに比べて複雑さはほぼ同じです。  しかし、元の値を使用したオプティミスティック同時実行チェックをデータベースで行う必要がある場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は DataSet のようなレベルのデータ ラウンド トリップをサポートしません。  ただし、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中間層は任意のプラットフォーム上のクライアントとの間でデータをやり取りできます。  
  
 [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] には、クライアントにシリアル化された後のエンティティの状態を追跡するインフラストラクチャが用意されていません。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、小量の比較的アトミックな対話を、データ層とプレゼンテーション層の間で行うサービス指向アーキテクチャが実現されますが、元の値のラウンド トリップはまったく実行されません。  このため、密結合のスマート クライアントを [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] と共に使用し、元の値を使ったオプティミスティック同時実行制御をデータベースで行う場合には、プレゼンテーション層と中間層の間で変更内容を通信するための独自の機構を実装する必要があります。  中間層で [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用することの利点を考慮に入れて、この余分の作業を行うかどうかは、システム設計者の判断に任せられます。  一方、データベースでタイムスタンプを使用する場合には、変更追跡用のカスタム ロジックは必要ありません。  
  
## 参照  
 [N\-Tier and Remote Applications with LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)   
 [LINQ to SQL N\-Tier with Web Services](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)   
 [n 層アプリケーションでのデータセットの操作](../Topic/Work%20with%20datasets%20in%20n-tier%20applications.md)