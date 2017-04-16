---
title: "&lt;commonParameters&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;commonParameters&gt;
複数のサービスでグローバルに使用されるパラメーターのコレクションを表します。  このコレクションには通常、永続性サービスによって共有されるデータベース接続文字列が格納されます。  
  
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
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|サービスによって使用される共通パラメーターの名前と値のペアをコレクションに追加します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<workflowRuntime\>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|ワークフロー ベースの [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスをホストする <xref:System.Workflow.Runtime.WorkflowRuntime> のインスタンスの設定を指定します。|  
  
## 解説  
 最初の要素 `<commonParameters>` は、複数のサービスでグローバルに使用されるパラメーターを定義します \(たとえば <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> を使用する場合の `ConnectionString`\)。  
  
> [!NOTE]
>  SQL 追跡サービスでは、`<commonParameters>` セクションに `ConnectionString` 値を指定しても、その値が常に使用されるとは限りません。  `StateMachineWorkflowInstance.StateHistory` プロパティの取得のように、操作によっては失敗する場合があります。  これを回避するには、次の例に示すように、追跡プロバイダーの構成セクションで `ConnectionString` 属性を指定します。  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
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
  
 共通パラメーターをプログラムによって変更する方法を次のコード例に示します。  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 構成ファイルを使用して Windows Workflow Foundation ホスト アプリケーションの <xref:System.Workflow.Runtime.WorkflowRuntime> オブジェクトの動作を制御する方法の詳細については、「[Workflow Configuration Files](http://msdn.microsoft.com/ja-jp/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)」を参照してください。  
  
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
 [\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)