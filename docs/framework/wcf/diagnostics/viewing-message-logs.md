---
title: メッセージ ログを参照する
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: 4fa205b52e3d19d2421d93297b5689422775f719
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33802978"
---
# <a name="viewing-message-logs"></a>メッセージ ログを参照する
ここでは、メッセージ ログの表示方法について説明します。  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>サービス トレース ビューアーでのメッセージ ログの表示  
 メッセージは、WCF によって処理されるように変換されます。 そのため、ログ記録されたメッセージは、ログ記録された時点でのメッセージの内容を反映しているにすぎず、ネットワーク上での内容ではありません。  
  
 メッセージ ログの出力はメッセージの転送形式とは関係がないため、メッセージ ログは常にデコードされたメッセージを出力します。 メッセージ ログが適切に設定されていれば、すべてのログ メッセージはプレーンテキストになります。 たとえば、ログ メッセージの形式 (プレーンテキスト) は、バイナリ メッセージ エンコーダーの使用には影響されません。  
  
 XmlWriterTraceListener の出力は、一連の XML フラグメントを含んだファイルです。 このファイルは有効な XML ファイルではないことに注意してください。 使用することをお勧め、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)メッセージのログ ファイルを表示します。 このツールを使用する方法の詳細については、次を参照してください。[相関トレースの表示とトラブルシューティング サービス トレース ビューアーを使用して](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)です。  
  
 サービス トレース ビューアー内でメッセージが表示、**メッセージ**タブです。操作エラーの原因となった、または操作エラーに関連するメッセージは、エラーの重大度に応じて、黄色 (警告レベル) または赤色 (エラー レベル) で強調表示されます。 メッセージをダブルクリックすると、要求の処理のコンテキストに従ってメッセージ トレースが表示されます。  
  
> [!NOTE]
>  メッセージにヘッダーがない場合は、`<header/>` タグがログに記録されません。  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>クライアント、中継、およびサービスによって記録されたメッセージの表示  
 環境には、クライアント、クライアントからメッセージが送信される中継、中継からさらにメッセージが転送されるサービスが含まれることがあります。 すべての 3 つの場所でメッセージのログ記録が有効になっているし、で 3 つすべてのメッセージ ログを表示[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)同時に、ログのメッセージ交換は正しく表示されません。 これは、メッセージ ヘッダーの `CorrelationId` と `ActivityId` が、すべての送受信ペアで一意にならなくなるためです。  
  
 この問題を解決するには、次のいずれかの方法に従います。  
  
-   2 つの 3 つのメッセージ ログの表示のみ、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)いつでもできます。  
  
-   内のすべての 3 つのログを表示する必要がある場合、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)新しいを作成して、リレー サービスを変更する、同時に<xref:System.ServiceModel.Channels.Message>インスタンス。 このインスタンスは、受信メッセージの本文のコピーであり、また、`ActivityId` ヘッダーおよび `Action` ヘッダーを除くすべてのヘッダーのコピーであることが必要です。 これを実行する方法を次のコード例に示します。  
  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>メッセージ ログ内容が不正確になる例外的なケース  
 次の条件では、ログ記録されたメッセージがネットワーク上にあるオクテット ストリームの正確な表現とはならない場合があります。  
  
-   BasicHttpBinding の場合、エンベロープ ヘッダーは /addressing/none 名前空間の受信メッセージについてログ記録されます。  
  
-   空白に不一致が生じる場合があります。  
  
-   受信メッセージの場合、空の要素が異なる表現になる場合があります。 たとえば、\<タグ >\</tag > の代わりに\<タグ/>  
  
-   既知の PII ログ記録が、既定または enableLoggingKnownPii="true" という明示的な設定で、無効になっている場合。  
  
-   UTF-8 へ変換するためのエンコードが有効な場合。  
  
## <a name="see-also"></a>関連項目  
 [サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [メッセージ ログ](../../../../docs/framework/wcf/diagnostics/message-logging.md)
