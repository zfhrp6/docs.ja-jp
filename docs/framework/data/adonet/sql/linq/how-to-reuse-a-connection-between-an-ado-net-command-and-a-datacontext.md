---
title: "方法 : ADO.NET コマンドおよび DataContext 間の接続を再利用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 196b3c8735168ea935aa1a0d3917dd34b2aa390f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>方法 : ADO.NET コマンドおよび DataContext 間の接続を再利用する
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]の一部である、[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]テクノロジ ファミリ、によって提供されるサービスに基づいています[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]、間の接続を再利用することができます、[!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)]コマンドと<xref:System.Data.Linq.DataContext>です。  
  
## <a name="example"></a>例  
 [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] コマンドおよび <xref:System.Data.Linq.DataContext> 間の同じ接続を再利用する方法を次の例に示します。  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>参照  
 [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [ADO.NET および LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)  
 [データベースとの通信](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
