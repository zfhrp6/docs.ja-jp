---
title: "トランザクション アプリケーションの診断"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0826881bac88f2bfa933ae71b798186dafc55303
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="diagnosing-transactional-applications"></a>トランザクション アプリケーションの診断
このトピックでは、トランザクションのアプリケーションをトラブルシューティングするために、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に用意されている管理機能および診断機能の使用方法について説明します。  
  
## <a name="performance-counters"></a>パフォーマンス カウンター  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、トランザクション アプリケーションのパフォーマンスを測定するための、標準のパフォーマンス カウンターが用意されています。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][パフォーマンス カウンター](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)です。  
  
 パフォーマンス カウンターには次の表に示すように、サービス、エンドポイント、操作の 3 つのレベルがあります。  
  
### <a name="service-performance-counters"></a>サービス パフォーマンス カウンター  
  
|パフォーマンス カウンター|説明|  
|-------------------------|-----------------|  
|トランザクション フロー|このサービスで操作に対して実行されたトランザクションの数です。 このカウンターは、サービスに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
|1 秒あたりのトランザクション フロー|このサービスの操作に対して実行された 1 秒あたりのトランザクションの数です。 このカウンターは、サービスに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
|コミットされたトランザクション操作|このサービスで、結果がコミットされた状態で完了したトランザクション操作の数です。 そのような操作中に実行された作業は完全にコミットされました。 リソースは、操作で実行された作業に応じて更新されます。|  
|1 秒あたりのコミットされたトランザクション操作|このサービスで、結果がコミットされた状態で完了したトランザクション操作の 1 秒あたりの数です。 そのような操作中に実行された作業は完全にコミットされました。 リソースは、操作で実行された作業に応じて更新されます。|  
|中止されたトランザクション操作|このサービスで、結果が中止された状態で完了したトランザクション操作の数です。 そのような操作中に実行された作業はロールバックされました。 リソースは、それぞれの直前の状態に復元されました。|  
|1 秒あたりの中止されたトランザクション操作|このサービスで、結果が中止された状態で完了したトランザクション操作の 1 秒あたりの数です。 そのような操作中に実行された作業はロールバックされました。 リソースは、それぞれの直前の状態に復元されました。|  
|不明なトランザクション操作|このサービスで、結果が不明な状態で完了したトランザクション操作の数です。 結果が不明な作業は中間状態になります。 リソースは、保留中となります。|  
|1 秒あたりの不明なトランザクション操作|このサービスで、結果が不明な状態で完了したトランザクション操作の 1 秒あたりの数です。 結果が不明な作業は中間状態になります。 リソースは、保留中となります。|  
  
### <a name="endpoint-performance-counters"></a>エンドポイントのパフォーマンス カウンター  
  
|パフォーマンス カウンター|説明|  
|-------------------------|-----------------|  
|トランザクション フロー|このエンドポイントでの操作に対して実行されたトランザクションの数。 このカウンターは、エンドポイントに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
|1 秒あたりのトランザクション フロー|毎秒ごとにこのエンドポイントでの操作に対して実行されたトランザクションの数。 このカウンターは、エンドポイントに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
  
### <a name="operation-performance-counters"></a>操作パフォーマンス カウンター  
  
|パフォーマンス カウンター|説明|  
|-------------------------|-----------------|  
|トランザクション フロー|このエンドポイントでの操作に対して実行されたトランザクションの数。 このカウンターは、エンドポイントに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
|1 秒あたりのトランザクション フロー|毎秒ごとにこのエンドポイントでの操作に対して実行されたトランザクションの数。 このカウンターは、エンドポイントに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
  
## <a name="windows-management-instrumentation"></a>WMI (Windows Management Instrumentation)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WMI (Windows Management Instrumentation) プロバイダーを介して実行時のサービスの検査データを公開します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]WMI データにアクセスするを参照してください[診断の Windows Management Instrumentation を使用して](../../../../docs/framework/wcf/diagnostics/wmi/index.md)です。  
  
 WMI プロパティには、サービスに適用されるトランザクション設定を示す読み取り専用のプロパティが多数あります。 次の表にこれらの設定をすべて示します。  
  
 サービスの `ServiceBehaviorAttribute` には、次のプロパティがあります。  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|ブール型|現在のトランザクションの完了時に、サービス オブジェクトをリサイクルするかどうかを指定します。|  
|TransactionAutoCompleteOnSessionClose|ブール型|現在のセッションの終了時に、保留中のトランザクションを完了するかどうかを指定します。|  
|TransactionIsolationLevel|<xref:System.Transactions.IsolationLevel> 列挙体の有効な値を含む文字列。|このサービスがサポートするトランザクションの分離レベルを指定します。|  
|TransactionTimeout|<xref:System.DateTime>|トランザクションを完了しなければならない期間を指定します。|  
  
 `ServiceTimeoutsBehavior` には、次のプロパティがあります。  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|トランザクションを完了しなければならない期間を指定します。|  
  
 バインディングの `TransactionFlowBindingElement` には、次のプロパティがあります。  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|TransactionProtocol|<xref:System.ServiceModel.TransactionProtocol> 型の有効な値を含む文字列。|トランザクションをフローさせるために使用するトランザクション プロトコルを指定します。|  
|TransactionFlow|ブール型|受信トランザクション フローを有効にするかどうかを指定します。|  
  
 操作の `OperationBehaviorAttribute` には、次のプロパティがあります。  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|TransactionAutoComplete|ブール型|未処理の例外が発生しなかった場合に、現在のトランザクションを自動的にコミットするかどうかを指定します。|  
|TransactionScopeRequired|ブール型|操作がトランザクションを必要とするかどうかを指定します。|  
  
 操作の `TransactionFlowAttribute` には、次のプロパティがあります。  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowOption> 列挙体の有効な値を含む文字列。|トランザクション フローが要求される範囲を指定します。|  
  
## <a name="tracing"></a>トレース  
 トレースを使用すると、トランザクション アプリケーションにおけるエラーを監視および分析できます。 トレースは次の方法を使用して有効にできます。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の標準トレース  
  
     このトレースは、通常の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションのトレースと同じものです。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][トレースの構成](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)です。  
  
-   WS-AtomicTransaction トレース  
  
     Ws-atomictransaction トレースを使用して有効にすることができます、 [Ws-atomictransaction 構成ユーティリティ (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)です。 このトレースでは、トランザクションの状態とシステム内の参加要素を把握できます。 内部のサービス モデル トレースも有効にするには、`HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` レジストリ キーを <xref:System.Diagnostics.SourceLevels> 列挙体の有効な値に設定します。 メッセージ ログは、他の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションと同じ方法で有効にできます。  
  
-   `System.Transactions` トレース  
  
     OleTransactions プロトコルを使用する場合、プロトコル メッセージはトレースできません。 <xref:System.Transactions> インフラストラクチャではトレースがサポートされるため (OleTransactions を使用)、ユーザーはトランザクションで発生したイベントを確認できます。 <xref:System.Transactions> アプリケーションのトレースを有効にするには、`App.config` 構成ファイルに次のコードを含めます。  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でも使用されるので、このコードにより、<xref:System.Transactions> のトレースも有効になります。  
  
## <a name="see-also"></a>参照  
 [管理と診断](../../../../docs/framework/wcf/diagnostics/index.md)  
 [トレースの構成](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
