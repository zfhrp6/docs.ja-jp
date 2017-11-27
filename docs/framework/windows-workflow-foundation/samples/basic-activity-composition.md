---
title: "基本的なアクティビティの構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f1c94a276cf2e76d595a22c5c930614818bbf2b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="basic-activity-composition"></a>基本的なアクティビティの構成
このサンプルでは、カスタム アクティビティとシステム標準アクティビティを作成して、追加のカスタム アクティビティを構築する方法を示します。  
  
 Survey アクティビティを使用するこのワークフローでは、質問のリストと共に Survey をスケジュールし、受け取った回答を出力します。  
  
## <a name="sample-details"></a>サンプルの詳細  
 このサンプルでは、次の 3 つのカスタム アクティビティを使用します。 `ReadLine`単純な<xref:System.Activities.NativeActivity>\<文字列 > を作成する、<xref:System.Activities.Bookmark>スケジュールし、設定時に、 `Return` <xref:System.Activities.OutArgument%601>するための値を<xref:System.Activities.Bookmark>が再開します。 `Prompt`<xref:System.Activities.Activity%601>\<文字列 > を受け取る、 <xref:System.Activities.InArgument%601>< 文字列\>という`Text`し、ユーザーの応答を返します、 `Result` <xref:System.Activities.OutArgument%601>\<文字列 >。 `Prompt` アクティビティは、.NET Framework に付属する <xref:System.Activities.Statements.Sequence> アクティビティと <xref:System.Activities.Statements.WriteLine> アクティビティを使用します。また、ユーザー入力を取得するためにカスタムの `ReadLine` アクティビティも組み込まれています。 最後のカスタム アクティビティは `Survey` アクティビティです。 <xref:System.Activities.Activity>< ICollection\<文字列 >> です。  このアクティビティは、 <xref:System.Activities.InArgument%601>< IEnumerable < 文字列\>> という名前`Questions`取り込んで、 `Result` out 引数に回答します。 `Survey` アクティビティは、.NET Framework の <xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.Sequence>、および <xref:System.Activities.Statements.AddToCollection%601> を使用し、調査の質問をして回答を得るために `Prompt` アクティビティも使用します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  開く、 **BasicActivityComposition.sln**サンプルのソリューション[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]です。  
  
2.  ソリューションをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`  
  
## <a name="see-also"></a>関連項目
