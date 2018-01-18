---
title: "ADO.NET のデータ追跡"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: df958982739c7ab2fd7aba42918b919c25d86829
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="data-tracing-in-adonet"></a>ADO.NET のデータ追跡
ADO.NET は、組み込みデータ トレース機能を特徴としています。この機能は、[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]、Oracle、OLE DB、および ODBC 用の .NET データ プロバイダーと、ADO.NET <xref:System.Data.DataSet> および [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] ネットワーク プロトコルによりサポートされています。  
  
 データ アクセス API 呼び出しのトレースは、次の問題を診断する際に役立ちます。  
  
-   クライアント プログラムとデータベース間のスキーマの不一致  
  
-   データベースの使用不可またはネットワーク ライブラリの問題  
  
-   誤った SQL がアプリケーションによりハードコーディングまたは生成された  
  
-   プログラミング ロジックが不適切  
  
-   複数の ADO.NET コンポーネント間または ADO.NET と独自コンポーネント間の対話に起因する問題  
  
 トレースを拡張することにより異なるトレース技術をサポートできます。このため、開発者はアプリケーション スタックのあらゆるレベルで問題をトレースできます。 トレースは ADO.NET のみで使用できる機能ではありませんが、Microsoft プロバイダーでは、汎用トレース機能および instrumentation API を活用しています。  
  
 設定して、ADO.NET におけるマネージ トレースの構成に関する詳細については、次を参照してください。[データ アクセスのトレース](http://msdn.microsoft.com/library/hh880086.aspx)です。  
  
## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>拡張イベント ログの診断情報へのアクセス  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]、データ アクセスのトレース ([データ アクセスのトレース](http://msdn.microsoft.com/library/hh880086.aspx)) が容易にできるように、接続エラーなどの診断情報とクライアントのイベントを関連付けるために簡単に更新されましたサーバーの接続リング バッファーやアプリケーション パフォーマンス情報から、拡張イベント ログにします。 拡張イベント ログの読み取り方法の詳細については、次を参照してください。[イベント セッション データの表示](http://msdn.microsoft.com/library/hh710068\(SQL.110\).aspx)です。  
  
 接続操作では、ADO.NET はクライアント接続 ID を送信します。 接続が失敗した場合、接続リング バッファーにアクセスできます ([、接続リング バッファーによる SQL Server 2008 の接続のトラブルシューティング](http://go.microsoft.com/fwlink/?LinkId=207752)) を見つけて、`ClientConnectionID`フィールドで診断情報を取得し、接続に失敗しました。 クライアント接続 ID は、エラーが発生した場合にのみリング バッファーに記録されます。 (接続がログイン前のパケットを送信する前に失敗すると、クライアント接続 ID は生成されません。)クライアント接続 ID は 16 バイトの GUID です。 拡張イベント セッション内のイベントに `client_connection_id` アクションが追加された場合にも、拡張イベントのターゲット出力のクライアント接続 ID を見つけることができます。 それ以上にクライアントのドライバーの診断について支援が必要な場合は、データ アクセスのトレースを有効にし、接続コマンドを再実行して、データ アクセスのトレースの `ClientConnectionID` フィールドを確認することができます。  
  
 `SqlConnection.ClientConnectionID` プロパティを使用して、クライアント接続 ID をプログラムによって取得できます。  
  
 `ClientConnectionID` は、正常に接続を確立する <xref:System.Data.SqlClient.SqlConnection> オブジェクトで使用できます。 接続試行が失敗すると、`ClientConnectionID` は `SqlException.ToString` を通じて利用可能になることがあります。  
  
 ADO.NET は、スレッド固有のアクティビティ ID も送信します。 TRACK_CAUSAILITY オプションが有効な状態でセッションが開始されると、アクティビティ ID は拡張イベントのセッションでキャプチャされます。 アクティブな接続のパフォーマンスの問題については、クライアントのデータ アクセスのトレース (`ActivityID` フィールド) からアクティビティ ID を取得した後、その拡張イベントの出力のアクティビティ ID を検索できます。 拡張イベントのアクティビティ ID は 16 バイトの GUID (クライアント接続 ID の GUID と同じではありません) であり、4 バイトのシーケンス番号が追加されています。 シーケンス番号は、スレッド内で要求の順序を表し、スレッドのバッチと RPC ステートメントの相対的順序を示します。 `ActivityID` は、現在、データ アクセスのトレースが有効な場合、データ アクセスのトレースの構成のワードの 18 番目のビットが有効にされると、オプションとして SQL のバッチ ステートメントと RPC の要求に送信されるようになっています。  
  
 次は、リング バッファーに格納され、RPC とバッチ操作でクライアントから送信されるアクティビティ ID を記録する拡張イベントのセッションを開始するために [!INCLUDE[tsql](../../../../includes/tsql-md.md)] を使用するサンプルです。  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
```  
  
## <a name="see-also"></a>参照  
 [.NET Framework のネットワークのトレース](../../../../docs/framework/network-programming/network-tracing.md)  
 [アプリケーションのトレースとインストルメント](../../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
