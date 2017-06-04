---
title: "基本的なアクティビティの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 基本的なアクティビティの構成
このサンプルでは、カスタム アクティビティとシステム標準アクティビティを作成して、追加のカスタム アクティビティを構築する方法を示します。  
  
 Survey アクティビティを使用するこのワークフローでは、質問のリストと共に Survey をスケジュールし、受け取った回答を出力します。  
  
## サンプルの詳細  
 このサンプルでは、次の 3 つのカスタム アクティビティを使用します。`ReadLine` は、スケジュールされたときに <xref:System.Activities.Bookmark> を作成し、`Return`<xref:System.Activities.OutArgument%601> を <xref:System.Activities.Bookmark> を再開する値に設定する単純な <xref:System.Activities.NativeActivity>\<string\> です。`Prompt` は、`Text` という名前の <xref:System.Activities.InArgument%601>\<string\> を使用し、ユーザーの応答を `Result`<xref:System.Activities.OutArgument%601>\<string\> で返す <xref:System.Activities.Activity%601>\<string\> です。`Prompt` アクティビティは、.NET Framework に付属する <xref:System.Activities.Statements.Sequence> アクティビティと <xref:System.Activities.Statements.WriteLine> アクティビティを使用します。また、ユーザー入力を取得するためにカスタムの `ReadLine` アクティビティも組み込まれています。最後のカスタム アクティビティは `Survey` アクティビティです。これは <xref:System.Activities.Activity>\<ICollection\<string\>\> になります。このアクティビティは、`Questions` という名前の <xref:System.Activities.InArgument%601>\<IEnumerable\<string\>\> を受け取り、`Result` out 引数に回答を設定します。`Survey` アクティビティは、.NET Framework の <xref:System.Activities.Statements.ForEach>、<xref:System.Activities.Statements.Sequence>、および <xref:System.Activities.Statements.AddToCollection%601> を使用し、調査の質問をして回答を得るために `Prompt` アクティビティも使用します。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で **BasicActivityComposition.sln** サンプル ソリューションを開きます。  
  
2.  ソリューションをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`  
  
## 参照