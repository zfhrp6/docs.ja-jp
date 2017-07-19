---
title: "Local Method Calls | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Local Method Calls
ローカル メソッド呼び出しとは、オブジェクト モデル内で実行される呼び出しです。  リモート メソッド呼び出しとは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が SQL に変換し、データベース エンジンに送信して実行される呼び出しです。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が呼び出しを SQL に変換できないときには、ローカル メソッド呼び出しが必要です。  それ以外の場合は、<xref:System.InvalidOperationException> がスローされます。  
  
## 例 1  
 次の例では、`Order` クラスは Northwind サンプル データベースの Orders テーブルに割り当てられています。  このクラスには、ローカル インスタンス メソッドが追加されています。  
  
 クエリ 1 では、`Order` クラスのコンストラクターがローカルで実行されます。  クエリ 2 では、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が `LocalInstanceMethod()` を SQL に変換しようとした場合は失敗し、<xref:System.InvalidOperationException> 例外がスローされるはずです。しかし、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はローカル メソッド呼び出しをサポートしているため、クエリ 2 で例外はスローされません。  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## 参照  
 [Background Information](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)