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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3fa40a7a864ae65d15d787f5dec58a8da7b8e9a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="d7b01-102">カスタム複合デザイナー - Workflow Item Presenter</span><span class="sxs-lookup"><span data-stu-id="d7b01-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="d7b01-103"><xref:System.Activities.Presentation.WorkflowItemPresenter>任意のアクティビティを配置できる「ドロップ ゾーン」を作成するため、WF デザイナー プログラミング モデル内の主要な型です。</span><span class="sxs-lookup"><span data-stu-id="d7b01-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="d7b01-104">このサンプルでは、そのこのような「ドロップ ゾーン」を表示しますアクティビティ デザイナーの構築</span><span class="sxs-lookup"><span data-stu-id="d7b01-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>  
  
 <span data-ttu-id="d7b01-105">このサンプルでは、次の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d7b01-105">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d7b01-106">使用例</span><span class="sxs-lookup"><span data-stu-id="d7b01-106">Demonstrates</span></span>  
  
-   <span data-ttu-id="d7b01-107"><xref:System.Activities.Presentation.WorkflowItemPresenter> を使用したカスタム アクティビティ デザイナーの作成</span><span class="sxs-lookup"><span data-stu-id="d7b01-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
-   <span data-ttu-id="d7b01-108">メタデータ ストアを使用したカスタム デザイナーの登録。</span><span class="sxs-lookup"><span data-stu-id="d7b01-108">Registering the custom designer using the metadata store.</span></span>  
  
-   <span data-ttu-id="d7b01-109">宣言および命令による再ホストされたツールボックスのプログラミング。</span><span class="sxs-lookup"><span data-stu-id="d7b01-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d7b01-110">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="d7b01-110">Sample Details</span></span>  
 <span data-ttu-id="d7b01-111">このサンプルのコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d7b01-111">The code for this sample shows:</span></span>  
  
-   <span data-ttu-id="d7b01-112">カスタム アクティビティ デザイナーは `SimpleNativeActivity` クラス用に作成されます。</span><span class="sxs-lookup"><span data-stu-id="d7b01-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>  
  
-   <span data-ttu-id="d7b01-113"><xref:System.Activities.Presentation.WorkflowItemPresenter> を使用してカスタム アクティビティ デザイナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d7b01-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
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
  
 <span data-ttu-id="d7b01-114">`ModelItem.Body` にバインドする WPF のデータ バインドの使用に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d7b01-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="d7b01-115">`ModelItem`プロパティは、<xref:System.Activities.Presentation.ActivityDesigner>デザイナーはされているため、ここでは、基になるオブジェクトを参照する**SimpleNativeActivity**です。</span><span class="sxs-lookup"><span data-stu-id="d7b01-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>  
  
#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="d7b01-116">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="d7b01-116">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d7b01-117">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で、ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="d7b01-117">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d7b01-118">F5 キーを押してアプリケーションをコンパイルし、実行します。</span><span class="sxs-lookup"><span data-stu-id="d7b01-118">Press F5 to compile and run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d7b01-119">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d7b01-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d7b01-120">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d7b01-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d7b01-121">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="d7b01-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d7b01-122">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d7b01-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="d7b01-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7b01-123">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [<span data-ttu-id="d7b01-124">ワークフロー デザイナーを使用したアプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="d7b01-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
