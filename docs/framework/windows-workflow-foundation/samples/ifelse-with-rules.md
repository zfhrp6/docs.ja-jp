---
title: "ルール付き IfElse | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ルール付き IfElse
このサンプルでは、ルール条件を <xref:System.Workflow.Activities.IfElseActivity> アクティビティで使用する方法を示します。  
  
 このサンプルでは、ホストから `OrderValue` パラメータが渡されます。このパラメータの値は、<xref:System.Workflow.Activities.IfElseActivity> アクティビティの最初の分岐のルール条件で使用されます。値が 10,000 未満の場合は最初の分岐が実行され、最初の分岐内の <xref:System.Workflow.Activities.CodeActivity> アクティビティによってコンソールに **Get Manager Approval** が出力されます。値が 10,000 より大きい場合は、2 番目の分岐内の <xref:System.Workflow.Activities.CodeActivity> アクティビティが実行され、コンソールに **Get VP Approval** が出力されます。  
  
### サンプルをビルドするには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  Ctrl キーを押しながら F5 キーを押して、ソリューションをデバッグなしで実行します。  
  
### サンプルを実行するには  
  
-   \[SDK コマンド プロンプト\] ウィンドウで、IfElseWithRules\\bin\\debug フォルダー \(Visual Basic バージョンのサンプルの場合は IfElseWithRules\\bin フォルダー\) にある .exe ファイルを実行します。このフォルダーは、サンプルのメイン フォルダーの下に作成されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## 参照  
 <xref:System.Workflow.Activities.Rules>   
 <xref:System.Workflow.Activities.IfElseActivity>   
 <xref:System.Workflow.Activities.CodeActivity>   
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>