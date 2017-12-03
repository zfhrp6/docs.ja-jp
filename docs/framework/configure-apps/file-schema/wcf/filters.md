---
title: "&lt;フィルター&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb8588f9699f44c584fa075e2d1e994c27f0c527
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltersgt"></a>&lt;フィルター&gt;

`filters` 要素は、ログに記録されるメッセージの種類の制御に使用される XPath フィルターのコレクションを保持します。

フィルターは、`logMessagesAtTransportLevel` を `true` に設定することによって指定されるトランスポート層でのみ適用されます。 サービス レベルおよび形式が正しくないメッセージ ログ記録は、フィルターの影響を受けません。

コレクションにフィルターを追加するには、`add` を使用します。 1 つ以上のフィルターを定義した場合は、少なくとも 1 つのフィルターと一致するメッセージだけが記録されます。 フィルターを定義しなかった場合は、すべてのメッセージが通過します。

フィルターは、完全な XPath 構文をサポートし、構成ファイルでの出現順に適用されます。 フィルターが構文的に正しくない場合は、構成例外が発生します。

SOAP ヘッダー セクションがあるメッセージだけを記録するフィルターの設定方法の例を次に示します。

```xml
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">  
  <filters>  
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
      /soap:Envelope/soap:Headers  
    </add>  
  </filters>  
</messageLogging>
```

## <a name="see-also"></a>関連項目

 <xref:System.ServiceModel.Configuration.DiagnosticSection><xref:System.ServiceModel.Diagnostics> <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> <xref:System.ServiceModel.Configuration.MessageLoggingElement> <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A> <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection> <xref:System.ServiceModel.Configuration.XPathMessageFilterElement> <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> [メッセージ ログの構成](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [\<メッセージ ログ >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
