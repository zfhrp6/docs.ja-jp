---
title: "メッセージ ログを参照する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# メッセージ ログを参照する
ここでは、メッセージ ログの表示方法について説明します。  
  
## サービス トレース ビューアーでのメッセージ ログの表示  
 メッセージは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で処理されるときに変換されます。そのため、ログ記録されたメッセージは、ログ記録された時点でのメッセージの内容を反映しているにすぎず、ネットワーク上での内容ではありません。  
  
 メッセージ ログの出力はメッセージの転送形式とは関係がないため、メッセージ ログは常にデコードされたメッセージを出力します。メッセージ ログが適切に設定されていれば、すべてのログ メッセージはプレーンテキストになります。たとえば、ログ メッセージの形式 \(プレーンテキスト\) は、バイナリ メッセージ エンコーダーの使用には影響されません。  
  
 XmlWriterTraceListener の出力は、一連の XML フラグメントを含んだファイルです。このファイルは有効な XML ファイルではないことに注意してください。[サービス トレース ビューアー ツール \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) を使用してメッセージ ログ ファイルを表示することをお勧めします。このツールの使用方法の詳細については、「[サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)」を参照してください。  
  
 サービス トレース ビューアーでは、メッセージは **\[Message\]** タブに表示されます。操作エラーの原因となった、または操作エラーに関連するメッセージは、エラーの重大度に応じて、黄色 \(警告レベル\) または赤色 \(エラー レベル\) で強調表示されます。メッセージをダブルクリックすると、要求の処理のコンテキストに従ってメッセージ トレースが表示されます。  
  
> [!NOTE]
>  メッセージにヘッダーがない場合は、`<header/>` タグがログに記録されません。  
  
## クライアント、中継、およびサービスによって記録されたメッセージの表示  
 環境には、クライアント、クライアントからメッセージが送信される中継、中継からさらにメッセージが転送されるサービスが含まれることがあります。これら 3 つの場所すべてでメッセージのログ記録が有効になっており、3 つのメッセージ ログをすべて同時に[サービス トレース ビューアー ツール \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) に表示した場合、メッセージ ログ交換は正しく表示されません。これは、メッセージ ヘッダーの `CorrelationId` と `ActivityId` が、すべての送受信ペアで一意にならなくなるためです。  
  
 この問題を解決するには、次のいずれかの方法に従います。  
  
-   [サービス トレース ビューアー ツール \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) では、常に 3 つのメッセージ ログのうち 2 つだけを表示します。  
  
-   3 つのログすべてを[サービス トレース ビューアー ツール \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) で同時に表示する必要がある場合は、新規の <xref:System.ServiceModel.Channels.Message> インスタンスを作成して中継サービスを変更できます。このインスタンスは、受信メッセージの本文のコピーであり、また、`ActivityId` ヘッダーおよび `Action` ヘッダーを除くすべてのヘッダーのコピーであることが必要です。これを実行する方法を次のコード例に示します。  
  
```  
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## メッセージ ログ内容が不正確になる例外的なケース  
 次の条件では、ログ記録されたメッセージがネットワーク上にあるオクテット ストリームの正確な表現とはならない場合があります。  
  
-   BasicHttpBinding の場合、エンベロープ ヘッダーは \/addressing\/none 名前空間の受信メッセージについてログ記録されます。  
  
-   空白に不一致が生じる場合があります。  
  
-   受信メッセージの場合、空の要素が異なる表現になる場合があります。たとえば、\<tag\/\> ではなく \<tag\>\<\/tag\> となることがあります。  
  
-   既知の PII ログ記録が、既定または enableLoggingKnownPii\="true" という明示的な設定で、無効になっている場合。  
  
-   UTF\-8 へ変換するためのエンコードが有効な場合。  
  
## 参照  
 [サービス トレース ビューアー ツール \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)   
 [サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)   
 [メッセージ ログ](../../../../docs/framework/wcf/diagnostics/message-logging.md)