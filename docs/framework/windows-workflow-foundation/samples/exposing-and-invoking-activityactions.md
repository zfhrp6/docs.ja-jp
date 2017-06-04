---
title: "ActivityAction の公開と呼び出し | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97ce4797-426e-463d-9cc4-1261afad6df4
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# ActivityAction の公開と呼び出し
このサンプルでは、<xref:System.Activities.ActivityAction> を含むカスタム アクティビティを開発する方法を示します。また、<xref:System.Activities.ActivityAction> の実装を提供して、このアクティビティを使用する方法も示します。  
  
 <xref:System.Activities.ActivityAction> を使用すると、アクティビティ作成者がカスタムの動作をプラグインできる、特定の署名を持つ "差し込み口" を公開できます。たとえば、<xref:System.Activities.Statements.ForEach> アクティビティ \(項目のコレクションで動作します\) の <xref:System.Activities.ActivityAction> では、アクティビティ ユーザーは現在の反復処理項目で機能する動作をプラグインできます。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で **ActivityAction.sln** サンプル ソリューションを開きます。  
  
2.  ソリューションをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ActivityAction`  
  
## 参照