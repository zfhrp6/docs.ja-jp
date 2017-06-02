---
title: "SQL Server のサーバー ロールとデータベース ロール | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# SQL Server のサーバー ロールとデータベース ロール
SQL Server では、すべてのバージョンで、個々のユーザーではなくロール \(つまり、ユーザーのグループ\) に対して権限を割り当てることのできるロール ベースのセキュリティが使用されています。  固定サーバー ロールおよび固定データベース ロールには、固定された一連の権限が割り当てられています。  
  
## 固定サーバー ロール  
 固定サーバー ロールは、固定された一連の権限とサーバー規模のスコープを持ちます。  SQL Server の管理を目的としており、このロールに割り当てられた権限を変更することはできません。  固定サーバー ロールには、データベースにユーザー アカウントがなくても、ログインを割り当てることができます。  
  
> [!IMPORTANT]
>  `sysadmin` 固定サーバー ロールは他のすべてのロールを内包し、無制限のスコープを持ちます。  本当に信頼できる場合以外は、このロールにプリンシパルを追加することは避けてください。  `sysadmin` ロールのメンバーには、サーバーのすべてのデータベースおよびリソースに対する取り消し不可能な管理特権が与えられます。  
  
 固定サーバー ロールに追加するユーザーは慎重に選ぶ必要があります。  たとえば、`bulkadmin` ロールでは、ユーザーがローカル ファイルの内容をテーブルに挿入できるため、データの整合性が損なわれる可能性があります。  固定サーバー ロールと権限を網羅した一覧については、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックを参照してください。  
  
## 固定データベース ロール  
 固定データベース ロールには、権限のグループを簡単に管理できるように、あらかじめ定義された一連の権限が割り当てられています。  `db_owner` ロールのメンバーは、データベースに対するすべての構成作業とメンテナンス作業を実行できます。  
  
 SQL Server の定義済みロールの詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|----------|--------|  
|[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックの「[サーバーレベルのロール](http://msdn.microsoft.com/library/ms188659.aspx)」および「[固定サーバー ロールの権限 \(データベース エンジン\)](http://msdn.microsoft.com/library/ms175892.aspx)」|[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] の固定サーバー ロールおよびそれに関連付けられている権限について説明します。|  
|[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックの「[データベースレベルのロール](http://msdn.microsoft.com/library/ms189121.aspx)」および「[固定データベース ロールの権限 \(データベース エンジン\)](http://msdn.microsoft.com/library/ms189612.aspx)」|固定データベース ロールおよびそれに関連付けられている権限について説明します。|  
  
## データベース ロールおよびユーザー  
 データベース ユーザー アカウントはデータベース オブジェクトを扱う関係上、ログインにマップされている必要があります。  データベース ユーザーをデータベース ロールに追加すると、そのロールに関連付けられたすべての権限セットが継承されます。  すべての権限を付与できます。  
  
 アプリケーションのセキュリティを計画する際は、`public` ロール、`dbo` ユーザー アカウント、および `guest` アカウントも考慮する必要があります。  
  
### public ロール  
 `public` ロールは、システム データベースを含め、すべてのデータベースに存在します。  このロールは削除できません。また、ユーザーを追加したり削除したりすることもできません。  他のすべてのユーザーおよびロールは既定で `public` ロールに所属するため、`public` ロールに付与された権限を継承します。  `public` には、すべてのユーザーに割り当てる必要のある権限だけを付与してください。  
  
### dbo ユーザー アカウント  
 `dbo` \(データベース所有者\) は、データベースのすべてのアクティビティを実行する暗黙権限を持ったユーザー アカウントです。  `sysadmin` 固定サーバー ロールのメンバーは、自動的に `dbo` にマップされます。  
  
> [!NOTE]
>  `dbo` はスキーマの名前としても使用されています。詳細については、「[SQL Server における所有権とユーザーとスキーマの分離](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)」を参照してください。  
  
 `dbo` ユーザー アカウントは、よく `db_owner` 固定データベース ロールと混同されます。  `sysadmin` のスコープがサーバー全体であるのに対し、`db_owner` のスコープはデータベースです。  `db_owner` ロールのメンバーであるからといって、`dbo` のユーザー権限があるとは限りません。  
  
### guest ユーザー アカウント  
 認証されて SQL Server のインスタンスへのログインが許可されたユーザーが、その後、データベースにアクセスするためには各データベースに別個のユーザー アカウントが存在している必要があります。  データベースごとにユーザー アカウントが要求されるため、SQL Server のインスタンスに接続したとしても、ユーザーは、サーバー上のすべてのデータベースにアクセスできるわけではありません。  この要件を回避するには、データベースに `guest` ユーザー アカウントを設定します。guest ユーザーは、データベースにユーザー アカウントがなくてもデータベースにログインしてアクセスできます。  
  
 `guest` アカウントは、SQL Server のすべてのバージョンが備えている組み込みのアカウントです。  新しいデータベースでは、既定で無効化されています。  このアカウントを有効にした場合でも、Transact\-SQL の REVOKE CONNECT FROM GUEST ステートメントを実行して、CONNECT 権限を取り消すことによって無効にできます。  
  
> [!IMPORTANT]
>  `guest` アカウントはできるだけ使用しないようにしてください。ユーザーごとに割り当てられたデータベース権限がなくても、すべてのログイン ユーザーが、このアカウントに付与されているデータベース権限を取得できるようになります。  `guest` アカウントを使用する必要がある場合は、最小限の権限を付与するようにしてください。  
  
 SQL Server のログイン、ユーザー、およびロールの詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|----------|--------|  
|SQL Server オンライン ブックの「[ID およびアクセス制御 \(データベース エンジン\)](http://msdn.microsoft.com/library/bb510418.aspx)」|プリンシパル、ロール、資格情報、セキュリティ保護可能なリソース、および権限について説明したトピックへのリンクが含まれています。|  
|[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] オンライン ブックの「[プリンシパル \(データベース エンジン\)](http://msdn.microsoft.com/library/ms181127.aspx)」|プリンシパルの説明のほか、サーバー ロールとデータベース ロールについて説明したトピックへのリンクが含まれています。|  
  
## 参照  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [SQL Server におけるアプリケーション セキュリティのシナリオ](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)   
 [認証](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)   
 [SQL Server における所有権とユーザーとスキーマの分離](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)   
 [SQL Server の承認とアクセス許可](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)