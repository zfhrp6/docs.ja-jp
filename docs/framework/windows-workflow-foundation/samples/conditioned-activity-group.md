---
title: "条件付きアクティビティ グループ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 条件付きアクティビティ グループ
このサンプルは、旅行の予約アプリケーションです。<xref:System.Workflow.Activities.ConditionedActivityGroup> \(CAG\) には、コード アクティビティである Car アクティビティと Airline アクティビティの 2 つがあります。`SimpleCAGWorkflow` コンストラクタ内の ArrayList オブジェクト "travelNeedType" には、必要とされる旅行の予約の種類が設定されています。`travelNeeds.Add` ステートメントの 1 つまたは両方をコメント化することで、CAG の動作を変更できます。Car アクティビティと Airline アクティビティには、<xref:System.Workflow.Activities.CodeCondition> の設定された <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> 条件がそれぞれ含まれています。Car アクティビティは、`travelNeeds` コレクションに `TravelNeeds.Car` エントリがある場合にだけ実行され、Airline アクティビティは、`travelNeeds` コレクションに `TravelNeeds.Airline` エントリがある場合にだけ実行されます。  
  
 各アクティビティが実行されると、コレクションから対応するエントリが削除されます。既定の条件 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> では、実行中または実行する準備の整った子がない場合に \(それぞれの <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> 条件による\)、CAG が終了するように指定されています。このサンプルでは、CAG は `travelNeeds` コレクションが空になったときに終了します。  
  
### サンプルをビルドするには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  Ctrl キーを押しながら F5 キーを押して、ソリューションをデバッグなしで実行します。  
  
### サンプルを実行するには  
  
-   \[SDK コマンド プロンプト\] ウィンドウで、SimpleCAG\\bin\\debug フォルダ \(Visual Basic バージョンのサンプルの場合は SimpleCAG\\bin フォルダ\) にある .exe ファイルを実行します。このフォルダは、サンプルのメイン フォルダの下にあります。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## 参照  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>   
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>   
 <xref:System.Workflow.Activities.CodeCondition>   
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>