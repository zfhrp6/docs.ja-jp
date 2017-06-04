---
title: "&lt;defaultPorts&gt; の &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;defaultPorts&gt; の &lt;add&gt;
クライアント アプリケーションがリッスンする既定の通信エンドポイント。  
  
## 構文  
  
```  
  
<useRequestHeadersForMetadataAddress>  
   <defaultPorts>  
      <add port="Integer" scheme="String" />  
   </defaultPorts>  
</useRequestHeadersForMetadataAddress>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|ポート|既定の通信ポート番号を指定する整数。|  
|scheme|通信ポートに関連付けられているプロトコル設定のグループを示す文字列。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<defaultPorts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|クライアント アプリケーションがリッスンする既定の通信エンドポイントの一覧を表示する既定のポートのコレクション。|  
  
## 参照  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>