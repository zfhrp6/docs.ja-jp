---
title: "SQL Server のセキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4b8eafeedd03097488b1493b5654db360eab94fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sql-server-security"></a>SQL Server のセキュリティ
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] には、安全なデータベース アプリケーションの作成を支援するさまざまな機能が備わっています。  
  
 データの盗難や破壊など、セキュリティに関する基本的な考慮事項は、使用している [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のバージョンに関係なく当てはまります。 また、データの整合性もセキュリティの問題として考慮する必要があります。 データの保護を怠り、その場しのぎでデータの操作を許可すると、不注意でまたは意図的に不正確な値に置き換えられたり、完全に削除されてしまうことによってデータの価値が失われてしまうこともあります。 加えて、機密情報の適切な保管方法など、遵守すべき法的要件が存在します。 特定の司法管轄域の法令によっては、一部の種類の個人データについて、保管すること自体が完全に禁止されている場合もあります。  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] の各バージョンにはそれぞれ異なるセキュリティ機能があり、Windows と同様、新しいバージョンほど機能が強化されています。 ただし、セキュリティ機能だけでは、データベース アプリケーションの安全性は保証されません。この点を理解することが重要です。 データベース アプリケーションの要件、実行環境、配置モデル、物理的な場所、およびユーザー数は、アプリケーションごとに異なります。 使用範囲がローカルに限定されている一部のアプリケーションでは最小限のセキュリティで済む場合もありますが、インターネット経由で配置されたアプリケーションには、きわめて強固なセキュリティ対策と継続的な監視および評価が要求されます。  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] データベース アプリケーションのセキュリティ要件は、事後的対策としてではなく設計時に考慮することが大切です。 開発サイクルの初期段階で脅威を評価すれば、どこで脆弱性が見つかろうと潜在的な損害を緩和する機会は得ることができます。  
  
 アプリケーションの初期設計に問題がなくても、システムの進化に伴って新しい脅威が出現する可能性があります。 データベースを多層的に防御することにより、セキュリティ侵害によって受ける損害を最小限に抑えることができます。 防御の第 1 段階は、本当に必要な権限以外は決して付与しないという方針の下、攻撃者に与える隙を減らすことです。  
  
 このセクションの各トピックでは、開発者に関係のある [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のセキュリティ機能を簡単に説明します。[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックの関連項目へのリンクのほか、より掘り下げて解説したリソースへのリンクも示しています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL Server セキュリティの概要](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] のアーキテクチャおよびセキュリティ機能について説明します。  
  
 [SQL Server におけるアプリケーション セキュリティのシナリオ](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 ADO.NET および [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] アプリケーションに該当するさまざまなセキュリティ シナリオを取り上げます。  
  
 [SQL Server Express のセキュリティ](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express のセキュリティ上の考慮事項について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [セキュリティと保護 (データベース エンジン)](http://msdn2.microsoft.com/library/bb510589\(SQL.100\).aspx.)  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックのセキュリティ トピックです。  
  
 [SQL Server のセキュリティに関する考慮事項](http://go.microsoft.com/fwlink/?LinkId=98587)  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックのセキュリティ トピックです。  
  
## <a name="see-also"></a>参照  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server と ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
