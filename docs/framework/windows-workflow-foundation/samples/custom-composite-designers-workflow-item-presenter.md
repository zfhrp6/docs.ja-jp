---
title: "カスタム複合デザイナー - Workflow Item Presenter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b529d1c150f686fb4a39f968001c9ac03c7c1dc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>カスタム複合デザイナー - Workflow Item Presenter
<xref:System.Activities.Presentation.WorkflowItemPresenter>任意のアクティビティを配置できる「ドロップ ゾーン」を作成するため、WF デザイナー プログラミング モデル内の主要な型です。 このサンプルでは、そのこのような「ドロップ ゾーン」を表示しますアクティビティ デザイナーの構築  
  
 このサンプルでは、次の方法を示します。  
  
## <a name="demonstrates"></a>使用例  
  
-   <xref:System.Activities.Presentation.WorkflowItemPresenter> を使用したカスタム アクティビティ デザイナーの作成  
  
-   メタデータ ストアを使用したカスタム デザイナーの登録。  
  
-   宣言および命令による再ホストされたツールボックスのプログラミング。  
  
## <a name="sample-details"></a>サンプルの詳細  
 このサンプルのコードを次に示します。  
  
-   カスタム アクティビティ デザイナーは `SimpleNativeActivity` クラス用に作成されます。  
  
-   <xref:System.Activities.Presentation.WorkflowItemPresenter> を使用してカスタム アクティビティ デザイナーを作成します。  
  
```xaml  
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
    <sap:ActivityDesigner.Resources>  
        <DataTemplate x:Key="Collapsed">  
            <StackPanel>  
                <TextBlock>This is the collapsed view</TextBlock>  
            </StackPanel>  
        </DataTemplate>  
        <DataTemplate x:Key="Expanded">  
            <StackPanel>  
                <TextBlock>Custom Text</TextBlock>  
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
                                        HintText="Please drop an activity here" />  
            </StackPanel>  
        </DataTemplate>  
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
            <Style.Triggers>  
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">  
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
                </DataTrigger>  
            </Style.Triggers>  
        </Style>  
    </sap:ActivityDesigner.Resources>  
    <Grid>  
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />  
    </Grid>  
</sap:ActivityDesigner>  
```  
  
 `ModelItem.Body` にバインドする WPF のデータ バインドの使用に注意してください。 `ModelItem`プロパティは、<xref:System.Activities.Presentation.ActivityDesigner>デザイナーはされているため、ここでは、基になるオブジェクトを参照する**SimpleNativeActivity**です。  
  
#### <a name="to-setup-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。  
  
2.  F5 キーを押してアプリケーションをコンパイルし、実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>参照  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [ワークフロー デザイナーを使用したアプリケーションの開発](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
