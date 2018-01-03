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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8cf28a7535cb09946654d4fb43b2f5567fff40c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
