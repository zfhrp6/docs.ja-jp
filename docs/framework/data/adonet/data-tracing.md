---
title: "ADO.NET でのデータ トレース | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# ADO.NET でのデータ トレース
ADO.NET は、組み込みデータ トレース機能を特徴としています。この機能は、[!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]、Oracle、OLE DB、および ODBC 用の .NET データ プロバイダーと、ADO.NET <xref:System.Data.DataSet> および [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] ネットワーク プロトコルによりサポートされています。  
  
 データ アクセス API 呼び出しのトレースは、次の問題を診断する際に役立ちます。  
  
-   クライアント プログラムとデータベース間のスキーマの不一致  
  
-   データベースの使用不可またはネットワーク ライブラリの問題  
  
-   誤った SQL がアプリケーションによりハードコーディングまたは生成された  
  
-   プログラミング ロジックが不適切  
  
-   複数の ADO.NET コンポーネント間または ADO.NET と独自コンポーネント間の対話に起因する問題  
  
 トレースを拡張することにより異なるトレース技術をサポートできます。このため、開発者はアプリケーション スタックのあらゆるレベルで問題をトレースできます。  トレースは ADO.NET のみで使用できる機能ではありませんが、Microsoft プロバイダーでは、汎用トレース機能および instrumentation API を活用しています。  
  
 ADO.NET におけるマネージ トレースの設定と構成の詳細については、「[データ アクセスのトレース](http://msdn.microsoft.com/library/hh880086.aspx)」を参照してください。  
  
## 拡張イベント ログの診断情報へのアクセス  
 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダーでは、拡張イベント ログのサーバーの接続のリング バッファーやアプリケーションのパフォーマンス情報から、接続の障害などのクライアントのイベントを診断情報と関連付けることを容易にするため、データ アクセスのトレース \(「[データ アクセスのトレース](http://msdn.microsoft.com/library/hh880086.aspx)」\) が更新されました。  拡張イベント ログの読み取りの詳細については、「[イベント セッション データの表示](http://msdn.microsoft.com/library/hh710068\(SQL.110\).aspx)」を参照してください。  
  
 接続操作では、ADO.NET はクライアント接続 ID を送信します。  接続が失敗した場合、接続リング バッファー \(「[接続リング バッファーを使用して SQL Server 2008 の接続のトラブルシューティングを実行する](http://go.microsoft.com/fwlink/?LinkId=207752)」\) にアクセスし、`ClientConnectionID` フィールドを見つけて、接続エラーについての診断情報を取得できます。  クライアント接続 ID は、エラーが発生した場合にのみリング バッファーに記録されます。  \(接続がログイン前のパケットを送信する前に失敗すると、クライアント接続 ID は生成されません。\) クライアント接続 ID は 16 バイトの GUID です。  拡張イベント セッション内のイベントに `client_connection_id` アクションが追加された場合にも、拡張イベントのターゲット出力のクライアント接続 ID を見つけることができます。  それ以上にクライアントのドライバーの診断について支援が必要な場合は、データ アクセスのトレースを有効にし、接続コマンドを再実行して、データ アクセスのトレースの `ClientConnectionID` フィールドを確認することができます。  
  
 `SqlConnection.ClientConnectionID` プロパティを使用して、クライアント接続 ID をプログラムによって取得できます。  
  
 `ClientConnectionID` は、正常に接続を確立する <xref:System.Data.SqlClient.SqlConnection> オブジェクトで使用できます。  接続試行が失敗すると、`ClientConnectionID` は `SqlException.ToString` を通じて利用可能になることがあります。  
  
 ADO.NET は、スレッド固有のアクティビティ ID も送信します。  TRACK\_CAUSAILITY オプションが有効な状態でセッションが開始されると、アクティビティ ID は拡張イベントのセッションでキャプチャされます。  アクティブな接続のパフォーマンスの問題については、クライアントのデータ アクセスのトレース \(`ActivityID` フィールド\) からアクティビティ ID を取得した後、その拡張イベントの出力のアクティビティ ID を検索できます。  拡張イベントのアクティビティ ID は 16 バイトの GUID \(クライアント接続 ID の GUID と同じではありません\) であり、4 バイトのシーケンス番号が追加されています。  シーケンス番号は、スレッド内で要求の順序を表し、スレッドのバッチと RPC ステートメントの相対的順序を示します。  `ActivityID` は、現在、データ アクセスのトレースが有効な場合、データ アクセスのトレースの構成のワードの 18 番目のビットが有効にされると、オプションとして SQL のバッチ ステートメントと RPC の要求に送信されるようになっています。  
  
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
  
## 参照  
 [.NET Framework のネットワークのトレース](../../../../docs/framework/network-programming/network-tracing.md)   
 [Tracing and Instrumenting Applications](../../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)   
 [ADO.NET マネージ プロバイダーおよび DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)