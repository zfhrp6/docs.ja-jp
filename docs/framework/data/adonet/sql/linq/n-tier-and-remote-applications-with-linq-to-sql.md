---
title: "LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 004e64584027d40368592097c76ad0830e942f07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>LINQ to SQL を使用する n 層アプリケーションとリモート アプリケーション
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用する n 層つまり多層アプリケーションを作成することができます。 通常、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]データ コンテキスト、エンティティ クラス、およびクエリ構築ロジック上にある、中間層のデータ アクセス層 (DAL) とします。 ビジネス ロジックと非永続的データは、エンティティとデータ コンテキストの部分クラスと部分メソッドの中に完全に実装できます。または、別個のクラスに実装することもできます。  
  
 クライアントまたはプレゼンテーション層は、中間層のリモート インターフェイス上のメソッドを呼び出し、その層の DAL は、<xref:System.Data.Linq.DataContext> メソッドにマップされるクエリまたはストアド プロシージャを実行します。 中間層は、通常、エンティティまたはプロキシ オブジェクトの XML 表現としてデータをクライアントに返します。  
  
 中間層では、データ コンテキストによってエンティティが作成され、データ コンテキストはエンティティの状態を追跡し、データベースからの遅延読み込み、および変更内容のデータベースへの送信を管理します。 これらのエンティティは、`DataContext` にいわばアタッチされます。 ただし、シリアル化によってエンティティが別の層に送られた後は、エンティティがデタッチされます。つまり、その状態が `DataContext` によって追跡されなくなります。 更新のためにクライアントによって戻されるエンティティは、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が変更内容をデータベースに送信する前に、データ コンテキストに再びアタッチされる必要があります。 オプティミスティック同時実行チェックのために元の値またはタイムスタンプが必要とされる場合、クライアントはこれらを中間層に戻す必要があります。  
  
 ASP.NET アプリケーションでは、このような複雑な操作の大部分が <xref:System.Web.UI.WebControls.LinqDataSource> によって管理されます。 詳細については、次を参照してください。 [NIB: LinqDataSource Web サーバー コントロールの概要](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136)です。  
  
## <a name="additional-resources"></a>その他のリソース  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] を使用する n 層アプリケーションの実装方法について、詳しくは以下のトピックを参照してください。  
  
-   [ASP.NET での LINQ to SQL N 層](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [Web サービスを使用した LINQ to SQL N 層](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [密結合クライアント サーバー アプリケーションと LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [N 層ビジネス ロジックの実装](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [N 層アプリケーションでのデータ取得および CUD 操作 (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 ADO.NET データセットを使用する n 層アプリケーションの詳細については、次を参照してください。 [n 層アプリケーションでデータセットを操作](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)です。  
  
## <a name="see-also"></a>参照  
 [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
