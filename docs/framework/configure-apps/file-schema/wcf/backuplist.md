---
title: "&lt;backupList&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 1
---
# &lt;backupList&gt;
プライマリ エンドポイントに接続できないときにルーティング サービスで使用するエンドポイント セットを列挙したバックアップ リストを定義するための構成セクションを表します。リストの最初のエンドポイントがダウンしていると、ルーティング サービスは自動的にリスト内で次にあるエンドポイントにフェールオーバーします。これにより、クライアント アプリケーションに複雑なパターンの処理方法やサービスの配置場所を示すことなく、アプリケーションの信頼性を高めることができます。  
  
## 構文  
  
```vb  
  
<routing>  
  <backupLists>  
    <backupList name="String">  
      <add endpointName="String" />  
    </backupList>    
  </backupLists>  
</routing>  
  
```  
  
```csharp  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|name|このエンドポイント リストを指定するために使用される名前を指定する文字列。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<routing\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|バックアップ エンドポイントの一覧。|  
  
## 解説  
 このセクションには、プライマリ エンドポイントへの送信時に通信例外が発生した場合にメッセージが送信されるエンドポイントの、順序付けられたコレクションが含まれます。  
  
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) の `endpointName` 属性に一覧表示されたプライマリ エンドポイントへの送信が通信例外によって失敗した場合、ルーティング サービスはこのセクションに格納された最初のエンドポイントにメッセージを送信しようとします。  これも通信例外によって失敗した場合、ルーティング サービスは、送信に成功するか、通信例外以外のエラーを返すか、コレクション内のすべてのエンドポイントがエラーを返すまで、このセクションに格納された次のエンドポイントにメッセージを送信しようとします。  
  
 次の例では、"Destination" という名前のプライマリ エンドポイントへの送信で通信例外が返された場合、サービスは "alternateServiceQueue" にメッセージを送信しようとします。  この試行でも通信例外が返された場合、ルーティング サービスはコレクション内の次のエンドポイントにメッセージを送信しようとします。  
  
```  
  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
## 参照  
 [System.ServiceModel.Routing.Configuration.BackupEndpointCollection](assetId:///System.ServiceModel.Routing.Configuration.BackupEndpointCollection?qualifyHint=False&amp;autoUpgrade=True)