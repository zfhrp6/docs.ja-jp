---
title: 実行プロパティ
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 201fe222de1cb2029696a1694ae97815db5f913d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`