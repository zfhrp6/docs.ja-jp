---
title: "安全なデータ アクセス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 安全なデータ アクセス
セキュリティで保護された ADO.NET コードを作成するには、基になるデータ ストア、つまりデータベースで利用可能なセキュリティ機構を理解しておく必要があります。  さらに、アプリケーションに含まれる他の機能またはコンポーネントのセキュリティへの影響も考慮する必要があります。  
  
## 認証、承認、および権限  
 Microsoft SQL Server に接続する場合は、Windows 認証 \(統合セキュリティ\) を使用できます。Windows 認証では、ユーザー ID とパスワードを渡さずに、現在のアクティブな Windows ユーザーの ID を使用します。  ユーザー資格情報が接続文字列内で公開されないため、Windows 認証を使用することを強くお勧めします。  SQL Server への接続に Windows 認証を使用できない場合は、<xref:System.Data.SqlClient.SqlConnectionStringBuilder> を使用して、接続文字列を実行時に作成することを検討してください。  
  
 認証に使用する資格情報は、アプリケーションのタイプに基づいて、それぞれ個別に処理する必要があります。  たとえば、Windows フォーム アプリケーションでは、ユーザーに認証情報の入力を求めたり、ユーザーの Windows 資格情報を使用できます。  Web アプリケーションでは、ユーザーではなくアプリケーションより提供された資格情報を使用してデータにアクセスする場合がよくあります。  
  
 いったん認証されたユーザーは、与えられた権限に基づく範囲で操作を実行できます。  常に最小特権の原則に従い、どうしても必要な権限以外は付与しないようにしてください。  
  
 詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|----------|--------|  
|[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)|保護構成を使用して接続文字列を暗号化する方法など、セキュリティのベスト プラクティスと接続情報を保護する手法について説明します。|  
|[Recommendations for Data Access Strategies](http://msdn.microsoft.com/ja-jp/72411f32-d12a-4de8-b961-e54fca7faaf5)|データへのアクセスおよびデータベース操作の実行に関連した推奨事項について説明します。|  
|[接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)|実行時にユーザー入力から接続文字列を構築する方法について説明します。|  
|[SQL Server セキュリティの概要](../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)|SQL Server のセキュリティ アーキテクチャについて説明します。|  
  
## パラメーター化コマンドと SQL インジェクション  
 パラメーター化コマンドは SQL インジェクション攻撃への対策として利用できます。SQL インジェクション攻撃は、SQL ステートメントに、サーバーのセキュリティを侵害するコマンドを "注入" することによって行われます。  パラメーター化コマンドを使用した場合、外部ソースから受け取る値が必ず値として渡され、Transact\-SQL ステートメントの一部になることはないため、SQL インジェクション攻撃を防ぐことができます。  Transact\-SQL コマンドが値に挿入されたとしても、データ ソースに対して実行されることはありません。  これらのコマンドは、単なるパラメーター値として処理されます。  セキュリティ面の利点に加え、パラメーター化コマンドには、Transact\-SQL ステートメントで渡される値やストアド プロシージャに渡される値を簡単に扱うことができるという利点もあります。  
  
 パラメーター化コマンドの使い方の詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|----------|--------|  
|[DataAdapter パラメーター](../../../../docs/framework/data/adonet/dataadapter-parameters.md)|`DataAdapter` でパラメーターを使用する方法について説明します。|  
|[ストアド プロシージャでのデータの変更](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)|パラメーターの指定方法および戻り値の取得方法について説明します。|  
|[SQL Server でのストアド プロシージャを使用したアクセス許可の管理](../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)|SQL Server のストアド プロシージャを使用してデータ アクセスをカプセル化する方法を説明します。|  
  
## スクリプト攻略  
 Web ページに悪意のある文字を挿入することによって行われるスクリプト攻略もインジェクション型の攻撃に属します。  挿入された文字はブラウザーによって検証されることなく、ページの一部として処理されます。  
  
 詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|----------|--------|  
|[Script Exploits Overview](../Topic/Script%20Exploits%20Overview.md)|スクリプトによる攻略および SQL ステートメントによる攻略から保護する方法について説明します。|  
  
## プローブ攻撃  
 攻撃者は、システムを攻撃するときに、サーバー、データベース、テーブルなどの名前を例外情報から取得して使用することがよくあります。  例外には、アプリケーションやデータ ソースに関する具体的な情報が含まれている場合があるので、アプリケーションとデータ ソースの保護を強化するには、クライアント側に不可欠な情報だけを公開するようにします。  
  
 詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|----------|--------|  
|[例外処理の基本事項](../../../../docs/standard/exceptions/exception-handling-fundamentals.md)|try\/catch\/finally 構造化例外処理の基本的な形式について説明します。|  
|[例外の推奨事項](../../../../docs/standard/exceptions/best-practices-for-exceptions.md)|例外処理のベスト プラクティスについて説明します。|  
  
## Microsoft Access および Excel データ ソースの保護  
 セキュリティ要件が最小限の場合、またはセキュリティ要件がまったく存在しない場合は、Microsoft Access や Microsoft Excel を ADO.NET アプリケーションのデータ ストアとして利用できます。  セキュリティ面では、"関係者以外には触らせないようにする" とった程度であれば十分な抑止効果がありますが、それ以上のセキュリティを求めることはできません。  Access および Excel の物理データ ファイルはファイル システム上に存在するため、原則的にすべてのユーザーがアクセスできます。  ファイルは容易にコピーしたり改変したりできるため、データの盗難や損失といった攻撃には決して強くありません。  堅牢なセキュリティが必要な場合は、SQL Server など、物理データ ファイルをファイル システムから読み取ることのできないサーバー ベースのデータベースを使用してください。  
  
 Access データおよび Excel データの保護の詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|----------|--------|  
|[Access 2007 のセキュリティに関する考慮事項とガイダンス](http://go.microsoft.com/fwlink/?LinkId=98354)|Access 2007 のセキュリティ手法 \(ファイルの暗号化、パスワードの管理、新しい ACCDB 形式および ACCDE 形式へのデータベースの変換、他のセキュリティ オプションの使用など\) について説明します。|  
|[ユーザーレベルのセキュリティによる Access データベースの保護 \(MDB\)](http://go.microsoft.com/fwlink/?LinkId=47697)|Access 2003 を対象としたトピックです。  Access 2003 でユーザー レベルのセキュリティ機能を実装し、データを保護する方法について説明します。|  
|[Access セキュリティにおけるワークグループ情報ファイルの役割について](http://support.microsoft.com/kb/305542)|Access 2003 のセキュリティの作業グループ情報ファイルのロールおよびリレーションシップについて説明します。|  
|[Microsoft Access バージョン 2.0 から 2000 までの Microsoft Access セキュリティに関するよくある質問](http://go.microsoft.com/fwlink/?LinkId=47698)|ダウンロード可能なバージョンの Microsoft Access セキュリティ FAQ です。|  
|[セキュリティと保護のトラブルシューティング](http://go.microsoft.com/fwlink/?LinkId=47703)|Excel 2003 のセキュリティに関する一般的な問題の解決方法が掲載されています。|  
  
## Enterprise Services  
 COM\+ は、Windows NT アカウントおよびプロセスやスレッドの偽装に基づく独自のセキュリティ モデルを備えています。  <xref:System.EnterpriseServices> 名前空間は、.NET アプリケーションが、<xref:System.EnterpriseServices.ServicedComponent> クラスを使用して、マネージ コードと COM\+ セキュリティ サービスを統合できるようにするラッパーを提供します。  
  
 詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|----------|--------|  
|[COM\+ Role\-Based Security and the .NET Framework](http://msdn.microsoft.com/ja-jp/02ab22ef-e5e2-4d29-b33a-6e03d94c4981)|マネージ コードを COM\+ セキュリティ サービスに統合する方法について説明します。|  
  
## アンマネージ コードとの相互運用  
 .NET Framework は、COM コンポーネント、COM\+ サービス、外部のタイプ ライブラリ、各種のオペレーティング システム サービスなど、アンマネージ コードとの相互運用性をサポートします。  アンマネージ コードを使用することは、マネージ コードのセキュリティ境界の外に出ることを意味します。  作成するコード、およびそれを呼び出すコードのどちらにも、アンマネージ コード権限 \(<xref:System.Security.Permissions.SecurityPermissionFlag> フラグが指定された <xref:System.Security.Permissions.SecurityPermission>\) が必要です。  アンマネージ コードは、意図しないセキュリティ上の脆弱性をアプリケーションにもたらす可能性があります。  どうしても必要な場合を除き、アンマネージ コードとの相互運用は避けてください。  
  
 詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|----------|--------|  
|[アンマネージ コードとの相互運用](../../../../docs/framework/interop/index.md)|COM コンポーネントを .NET Framework に公開する方法、および .NET Framework コンポーネントを COM に公開する方法について説明します。|  
|[Advanced COM Interoperability](http://msdn.microsoft.com/ja-jp/3ada36e5-2390-4d70-b490-6ad8de92f2fb)|プライマリ相互運用機能アセンブリ、スレッド処理、カスタム マーシャリングなど高度なトピックが含まれています。|  
  
## 参照  
 [ADO.NET アプリケーションのセキュリティ保護](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [SQL Server のセキュリティ](../../../../docs/framework/data/adonet/sql/sql-server-security.md)   
 [Recommendations for Data Access Strategies](http://msdn.microsoft.com/ja-jp/72411f32-d12a-4de8-b961-e54fca7faaf5)   
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)   
 [接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)