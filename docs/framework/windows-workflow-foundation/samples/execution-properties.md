---
title: "実行プロパティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab7c81f051e6e65509d232479fd9f4ebe00ac99d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="execution-properties"></a>実行プロパティ
このサンプルでは、カスタム アクティビティで実行プロパティを定義および使用する方法を示します。 この例では、実行プロパティによってコンソールの前景色が決定されます。 例のワークフローでは、実行のさまざまな論理パス (<xref:System.Activities.Statements.Parallel> アクティビティの分岐) が、アクティビティの逐次的実行にもかかわらず、<xref:System.Activities.Statements.Parallel> アクティビティの分岐全体にわたってさまざまなコンソール色をどのように保持するかを示します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ExecutionProperties.sln サンプル ソリューションを開きます。  
  
    > [!NOTE]
    >  使用されるカスタム アクティビティはソリューションと同時にビルドする必要があるため、ソリューションをビルドする前に ThreeColors.xaml を表示するとエラーが表示されます。  
  
2.  ソリューションをビルドして実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`