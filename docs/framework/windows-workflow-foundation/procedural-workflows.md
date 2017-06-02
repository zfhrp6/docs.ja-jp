---
title: "手続き型ワークフロー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# 手続き型ワークフロー
手続き型ワークフローでは、手続き型言語と似たフロー制御方法を使用します。これらの構造には `While` と `If` が含まれます。これらのワークフローは、<xref:System.Activities.Statements.Flowchart> や <xref:System.Activities.Statements.Sequence> など、他のフロー制御アクティビティを使用して自由に構成できます。  
  
## 実行フローの制御  
 ワークフロー アクティビティ ライブラリには、手続き型言語で使用されるほとんどのフロー制御方法をモデル化するアクティビティがあります。これには次のものが含まれます。  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 フロー制御アクティビティを使用するには、**\[アクティビティ\]** ツールボックスからデザイナー ウィンドウ内の複合アクティビティにドラッグ アンド ドロップします。  
  
> [!NOTE]
>  [!INCLUDE[dublin](../../../includes/dublin-md.md)] を使用して Web ファーム上のワークフローをホストする場合、AppFabric は異なる AppFabric サーバー間でインスタンスを移動します。これには、リソースがすべてのノード間で共有される必要があります。既定の NET 4 ワークフロー アクティビティには、ローカル リソースにアクセスする操作が含まれていません。AppFabric はワークフローを普遍としてマークするメカニズムを提供しないため、開発者はワークフローが移動されると失敗するカスタム アクティビティを作成する必要があります。  
  
## 参照  
 [Flowchart のワークフロー](../../../docs/framework/windows-workflow-foundation//flowchart-workflows.md)