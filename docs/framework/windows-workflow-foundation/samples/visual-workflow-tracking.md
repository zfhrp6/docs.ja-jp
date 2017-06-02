---
title: "ビジュアル ワークフロー追跡 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0143448f-2044-40a0-8a3d-941f6d12468b
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# ビジュアル ワークフロー追跡
このサンプルでは、[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] のデバッグ機能を使用してビジュアル ワークフロー追跡アプリケーションを作成する方法を示します。  
  
## サンプルの詳細  
 このアプリケーションは、Workflow.xaml に定義されている単純なフローチャート ワークフローを実行し、ワークフロー デザイナーを再ホストして現在実行中のワークフローを表示します。ワークフローが実行されると、現在実行中のアクティビティが黄色の枠とデバッグ矢印で示されます。さらに、ワークフローによって生成された追跡レコードもアプリケーション ウィンドウに表示されます。ワークフロー追跡機能[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、[ワークフロー追跡とトレース](../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)を参照してください。[!INCLUDE[crabout](../../../../includes/crabout-md.md)] ワークフロー デザイナーのホスト変更は、[ワークフロー デザイナーのホスト変更](../../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md) を参照してください。  
  
 このワークフロー シミュレーターは、2 つのディクショナリを保持することによって機能します。一方のディクショナリには、現在実行中のアクティビティ オブジェクトと、そのアクティビティがインスタンス化された XAML の行番号とのマッピングが含まれています。もう一方のディクショナリには、アクティビティ インスタンス ID とアクティビティ オブジェクトとのマッピングが含まれています。カスタム追跡プロファイルを使用して追跡レコードが出力されるときには、現在実行中のアクティビティのインスタンス ID が特定されて、そのアクティビティをインスタンス化した XAML ファイルにマップされます。その後、再ホストされたワークフロー デザイナーで、ワークフロー デバッガーと同じ方法を使用してそのアクティビティがデザイナー画面で強調表示されます \(アクティビティが黄色の枠で囲まれ、デザイナーの左端に黄色の矢印が表示されます\)。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のサンプル ディレクトリにある WorkflowSimulator.sln ファイルを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  Ctrl キーを押しながら F5 キーを押してサンプルを実行します。再ホストされたワークフロー デザイナーのウィンドウに Workflow.xaml ファイルが表示されます。  
  
4.  **\[ファイル\]** メニューの **\[ワークフローの実行...\]** をクリックします。  
  
5.  現在実行中のアクティビティが上述のように強調表示され、アプリケーション ウィンドウの右側に追跡レコードが表示されます。  
  
6.  ワークフローが完了したら、任意の追跡レコードをクリックして、どのアクティビティに対応しているのかを調べることができます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\VisualWorkflowTracking`  
  
## 参照