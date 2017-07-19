---
title: "&lt;protocolMapping&gt; の &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;protocolMapping&gt; の &lt;add&gt;
トランスポート プロトコル スキーム \(http、net.tcp、net.pipe など\) と [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] バインディング間の既定のプロトコル マッピングを表します。  実行時に既定のエンドポイントを作成するときに、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は構成されたマッピングを確認し、特定のベース アドレスに使用するバインディングを決定します。  
  
## 構文  
  
```vb  
  
<protocolMapping>  
    <add binding="String”  
         bindingConfiguration="String”  
         scheme="http/net.msmq/net.pipe/net.tcp"/>  
</protocolMapping>  
  
```  
  
```csharp  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|要素|説明|  
|--------|--------|  
|バインド|既定のエンドポイントを作成するときにエンドポイントに使用されるバインディングの種類を指定する文字列。|  
|bindingConfiguration|参照されるバインディング構成セクションの名前を指定する文字列。|  
|scheme|既定のエンドポイントに使用されるトランスポート プロトコル スキーム。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<protocolMapping\>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|トランスポート プロトコル スキーム \(http、net.tcp、net.pipe など\) と [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] バインディング間の既定のプロトコル マッピングを定義する構成セクションを表します。|  
  
## 使用例  
 次の構成例は、machine.config ファイル内の既定のプロトコル マッピングを示しています。  machine.config ファイルを変更することで、既定のマッピングをコンピューター レベルでオーバーライドできます。  または、アプリケーションのスコープ内だけでオーバーライドする場合は、アプリケーション構成ファイルのこのセクションをオーバーライドし、各プロトコル スキームのマッピングを変更できます。  
  
```  
  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
  
```  
  
## 参照  
 [System.ServiceModel.Configuration.ProtocolMappingSection](assetId:///System.ServiceModel.Configuration.ProtocolMappingSection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.ServiceModel.Configuration.ProtocolMappingElement](assetId:///System.ServiceModel.Configuration.ProtocolMappingElement?qualifyHint=False&amp;autoUpgrade=True)