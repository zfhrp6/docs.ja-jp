---
title: "&lt;commonParameters&gt; の &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;commonParameters&gt; の &lt;add&gt;
複数のサービスでグローバルに使用されるパラメーターの名前と値のペアを指定します。  このパラメーターには通常、永続性サービスによって共有されるデータベース接続文字列が格納されます。  
  
## 構文  
  
```  
  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|name|サービスに対して指定されたパラメーターの名前。|  
|value|サービスに対して指定されたパラメーターの値。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<commonParameters\>](http://msdn.microsoft.com/ja-jp/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|サービスによって使用される共通パラメーターのコレクション。  このコレクションには通常、永続性サービスによって共有されるデータベース接続文字列が格納されます。|  
  
## 解説  
 最初の要素 `<commonParameters>` は、複数のサービスでグローバルに使用されるパラメーターを定義します \(たとえば <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> を使用する場合の `ConnectionString`\)。  
  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> や <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> など、作業バッチを永続的ストアにコミットするサービスでは、`EnableRetries` パラメーターを次の例のように使用することで、トランザクションの再試行を有効にできます。  
  
```  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 `EnableRetries` パラメーターは、*CommonParameters* セクションのようにグローバル レベルで設定したり、*Services* セクションのように `EnableRetries` をサポートするサービスごとに設定したりできます。  
  
 Windows Workflow Foundation ホスト アプリケーションの <xref:System.Workflow.Runtime.WorkflowRuntime> オブジェクトの動作を制御する構成ファイルの使い方の詳細については、「[Workflow Configuration Files](http://msdn.microsoft.com/ja-jp/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)」を参照してください。  
  
## 使用例  
  
```  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>   
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>   
 <xref:System.Workflow.Runtime.WorkflowRuntime>   
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>   
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>   
 [Workflow Configuration Files](http://msdn.microsoft.com/ja-jp/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)   
 [\<commonParameters\>](http://msdn.microsoft.com/ja-jp/d0e1e6fc-985a-4713-b7da-194e30dfab4c)