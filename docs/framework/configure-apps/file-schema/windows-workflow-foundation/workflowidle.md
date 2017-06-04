---
title: "&lt;workflowIdle&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;workflowIdle&gt;
アイドル状態のワークフロー インスタンスのアンロードおよび永続化のタイミングを制御するサービス動作。  
  
## 構文  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <workflowIdle timeToPersist=”TimeSpan”  
          timeToUnload=”TimeSpan” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|timeToPersist|ワークフローがアイドル状態から永続化されるまでの継続時間を指定する Timespan 値。  既定値は TimeSpan.MaxValue です。<br /><br /> 継続時間は、ワークフロー インスタンスがアイドル状態になった時点から開始します。  この属性は、ワークフロー インスタンスを、可能な限り長くメモリに保持しながら、積極的に永続化しようとする場合に役立ちます。  この属性は、値が **timeToUnload** 属性の値未満の場合にのみ有効です。  それより大きい場合は無視されます。  この属性が、**timeToUnload** 属性によって指定された値より先に経過する場合は、ワークフローをアンロードする前に永続化を終了する必要があります。  これは、ワークフローを永続化するまでアンロード操作に遅延が生じる場合があることを意味します。  永続化レイヤーは一時的なエラーの再試行処理は行いますが、回復不可能なエラーに対しては例外をスローするだけです。  したがって、永続化中にスローされる例外は致命的な例外として処理され、ワークフロー インスタンスが中止されます。|  
|timeToUnload|ワークフローがアイドル状態からアンロードされるまでの継続時間を指定する Timespan 値。  既定値は 1 分です。<br /><br /> ワークフローをアンロードすることは、同時に、永続化することも意味します。  この属性をゼロに設定した場合は、ワークフローがアイドル状態になった直後に、ワークフロー インスタンスが永続化され、アンロードされます。  この属性を TimeSpan.MaxValue に設定すると、アンロード操作を事実上、無効にします。  アイドル状態になったワークフロー インスタンスはアンロードされません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<serviceBehaviors\> の \<behavior\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|動作の要素を指定します。|  
  
## 参照  
 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>