---
title: "SQL Server Compact および LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 24f620319cd469538cf4454be7caffececdf9213
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact および LINQ to SQL
SQL Server Compact は、Visual Studio と共にインストールされる既定のデータベースです。 詳細については、次を参照してください。 [PAVE 経由でを使用して SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc)です。  
  
 このトピックでは説明の使用法、構成、機能セット、およびスコープの主要な違い[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]をサポートします。  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>LINQ to SQL との関係における SQL Server Compact の特徴  
 既定では、SQL Server Compact がインストールされているすべての[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]のエディションであるため、開発用コンピューターで使用するために使用可能な[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]します。 SQL Server Compact を使用するアプリケーションの展開と[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]のとは異なる、[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]アプリケーションです。 SQL Server Compact は .NET Framework の一部ではないため、アプリケーションにパッケージ化するか、Microsoft サイトから個別にダウンロードする必要があります。  
  
 これには、次のような特徴があります。  
  
-   SQL Server Compact は DLL としてパッケージ化されており、データベース ファイル (.sdf 拡張子) に対して直接使用できます。  
  
-   SQL Server Compact は、クライアント アプリケーションと同じプロセスで実行されます。 SQL Server Compact との通信の効率と通信するよりもかなり大きくしたがって、[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]です。 その一方で、SQL Server Compact はコストを伴うマネージ コードとアンマネージ コード間の相互運用性が必要です。  
  
-   SQL Server Compact DLL のサイズは小さいです。 このため、アプリケーション全体のサイズが抑制されます。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ランタイムおよび SQLMetal コマンド ライン ツールが SQL Server Compact をサポートしています。  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] では、SQL Server Compact はサポートしていません。  
  
## <a name="feature-set"></a>機能セット  
 SQL Server Compact の機能セットが、機能セットよりもはるかに簡単[!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]に影響を与える次の方法で[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]アプリケーション。  
  
-   SQL Server Compact は、ストアド プロシージャまたはビューをサポートしません。  
  
-   SQL Server Compact は、一部のデータ型と SQL 関数のみをサポートします。  
  
-   SQL Server Compact は、一部の SQL コンストラクトのみをサポートします。  
  
-   SQL Server Compact は、最小限のオプティマイザーを備えています。 一部のクエリがタイムアウトを可能性があることができます。  
  
-   SQL Server Compact は、部分信頼をサポートしません。  
  
## <a name="see-also"></a>参照  
 [参照](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
