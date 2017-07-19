---
title: "&lt;workflowRuntime&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;workflowRuntime&gt;
ワークフロー ベースの [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスをホストする <xref:System.Workflow.Runtime.WorkflowRuntime> のインスタンスの設定を指定します。  
  
## 構文  
  
```  
  
<workflowRuntime cachedInstanceExpiration="TimeSpan"  
                                  enablePerformanceCounters="Boolean"  
                                  name="String"  
                                  validateOnCreate="Boolean">  
                 <commonParameters>  
                    <add name="String" value="String" />  
                 </commonParameters>  
                 <services>  
                    <add type="String"/>  
                 </services>  
</workflowRuntime>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|cachedInstanceExpiration|ワークフロー インスタンスが強制的にアンロードまたは中止される前に、アイドル状態でメモリに残ることができる最大期間を指定する、省略可能な <xref:System.Timespan> 値。  unloadOnIdle を実行する `PersistenceService` が workflowruntime に設定されている場合、この属性は無視されます。|  
|enablePerformanceCounters|パフォーマンス カウンターが有効であるかどうかを指定する省略可能なブール値。  パフォーマンス カウンターは、ワークフローに関連したさまざまな統計情報を提供します。ただしそのために、ワークフロー ランタイム エンジンが起動してワークフロー インスタンスが実行されている間は、パフォーマンスが低下します。  既定値は `true` です。|  
|name|ワークフロー ランタイム エンジンの名前を含む文字列。  名前は出力で使用され、このランタイムを、システムで実行されている他のランタイム \(パフォーマンス カウンターなど\) と区別するために使用されます。<br /><br /> 既定値は空の文字列です。|  
|validateOnCreate|WorkflowServiceHost を開いたときにワークフロー定義の検証を行うかどうかを指定する省略可能なブール値。  この属性が `true` に設定されているときは、`WorkflowServiceHost.Open` が呼び出されるたびにワークフローの検証が実行されます。  検証エラーが見つかった場合は、<xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> エラーがスローされます。<br /><br /> このプロパティが `false` に設定されている場合、ワークフロー定義の検証は行われません。<br /><br /> このプロパティの既定値は `true` です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|commonParameters|サービスによって使用される共通パラメーターのコレクション。  このコレクションには通常、永続性サービスによって共有されるデータベース接続文字列が格納されます。|  
|サービス|<xref:System.Workflow.Runtime.WorkflowRuntime> エンジンに追加されるサービスのコレクション。  要素は、<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> 型です。  コレクションで指定されたサービスはワークフロー ランタイム エンジンによって初期化され、適切な <xref:System.Workflow.Runtime.WorkflowRuntime> コンストラクターが呼び出されるとワークフロー ランタイム エンジンのサービスに追加されます。  したがって、コレクションで指定されたサービスは、そのコンストラクターのシグネチャに関して一定の規則に従う必要があります。  詳細については、「<xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>」を参照してください。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## 解説  
 Windows Workflow Foundation ホスト アプリケーションの <xref:System.Workflow.Runtime.WorkflowRuntime> オブジェクトの動作を制御する構成ファイルの使い方の詳細については、「[Workflow Configuration Files](http://msdn.microsoft.com/ja-jp/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)」を参照してください。  
  
## 使用例  
  
```  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
         <commonParameters>  
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
            <add name="EnableRetries" value="True" />  
         </commonParameters>  
         <services>  
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>  
         </services>  
      </workflowRuntime>  
   </behavior>  
</serviceBehaviors>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>   
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>   
 <xref:System.Workflow.Runtime.WorkflowRuntime>   
 [Workflow Configuration Files](http://msdn.microsoft.com/ja-jp/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)