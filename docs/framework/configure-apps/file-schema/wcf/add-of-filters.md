---
title: "&lt;filters&gt; の &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;filters&gt; の &lt;add&gt;
ログに記録するメッセージの種類を指定する XPath フィルター。  
  
## 構文  
  
```  
  
<filters>  
   <add filter="String"/>  
</filters>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|フィルター|XPath 1.0 の式によって定義される、XML ドキュメントのクエリを指定する文字列。  詳細については、「<xref:System.ServiceModel.Dispatcher.XPathMessageFilter>」を参照してください。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<filters\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|ログに記録されるメッセージの種類を制御する XPath フィルターのコレクションを格納します。|  
  
## 解説  
 フィルターは、`logMessagesAtTransportLevel` を `true` に設定することによって指定されるトランスポート層でのみ適用されます。  サービス レベルおよび形式が正しくないメッセージ ログ記録は、フィルターの影響を受けません。  
  
 コレクションにフィルターを追加するには、`add` を使用します。  1 つ以上のフィルターを定義した場合は、少なくとも 1 つのフィルターと一致するメッセージだけが記録されます。  フィルターを定義しなかった場合は、すべてのメッセージが通過します。  
  
 フィルターは、完全な XPath 構文をサポートし、構成ファイルでの出現順に適用されます。  フィルターが構文的に正しくない場合は、構成例外が発生します。  
  
 SOAP ヘッダー セクションがあるメッセージだけを記録するフィルターの設定方法の例を次に示します。  
  
## 使用例  
 SOAP ヘッダー セクションがあるメッセージだけを記録するフィルターの設定方法の例を次に示します。  
  
```  
<messageLogging logEntireMessage="true"  
     logMalformedMessages="true" logMessagesAtServiceLevel="true"  
     logMessagesAtTransportLevel="true" maxMessagesToLog="420”>  
     <filters>  
        <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                        /soap:Envelope/soap:Headers  
        </add>  
     </filters>  
</messageLogging>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>   
 <xref:System.ServiceModel.Diagnostics>   
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>   
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>   
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>   
 <xref:System.ServiceModel.Configuration.XpathMessageFilterElement>   
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>   
 [メッセージ ログの構成](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)   
 [メッセージ ログの構成](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)   
 [\<messageLogging\>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)