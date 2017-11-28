---
title: "デザイナーのホスト変更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 888282d10be9840817274e0fed36b3cb1cf6da32
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="designer-rehosting"></a><span data-ttu-id="206fa-102">デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="206fa-102">Designer ReHosting</span></span>
<span data-ttu-id="206fa-103">デザイナーのホスト変更は、カスタム アプリケーション内でワークフロー デザイン キャンバスをホストすることを示す一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="206fa-103">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="206fa-104">多くのユーザーにとって、使い慣れたホスト アプリケーションは Visual Studio ですが、アプリケーションでワークフロー デザイナーを表示すると役立つ場合があるシナリオも数多くあります。</span><span class="sxs-lookup"><span data-stu-id="206fa-104">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
-   <span data-ttu-id="206fa-105">監視アプリケーション (エンド ユーザーがプロセス、およびプロセスに関するランタイム データ (現在アクティブな状態、実行時間の集計データ、ワークフローのインスタンスに関するその他の情報など) を表示できるようにします)。</span><span class="sxs-lookup"><span data-stu-id="206fa-105">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
-   <span data-ttu-id="206fa-106">ユーザーが限られたアクティビティ セットを使用してプロセスをカスタマイズできるようにするアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="206fa-106">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="206fa-107">このような種類のアプリケーションをサポートするために、ワークフロー デザイナーが .NET Framework に付属しており、WPF アプリケーション内でホストするか、適切な WPF ホスト コードを使用して WinForms アプリケーション内でホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="206fa-107">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="206fa-108">このサンプルでは、次の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="206fa-108">This sample demonstrates:</span></span>  
  
-   <span data-ttu-id="206fa-109">WF デザイナーのホスト変更方法。</span><span class="sxs-lookup"><span data-stu-id="206fa-109">Rehosting the WF designer.</span></span>  
  
-   <span data-ttu-id="206fa-110">再ホストされたツールボックスおよびプロパティ グリッドの使用方法。</span><span class="sxs-lookup"><span data-stu-id="206fa-110">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="206fa-111">デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="206fa-111">Rehosting the designer</span></span>  
 <span data-ttu-id="206fa-112">このサンプルでは、次のグリッド レイアウトのような、デザイナーを含む WPF レイアウトを作成する方法を示します (スペースを考慮してツールボックス コードは省略しています)。</span><span class="sxs-lookup"><span data-stu-id="206fa-112">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="206fa-113">デザイナーおよびプロパティ グリッドを含む罫線の名前に注意してください。</span><span class="sxs-lookup"><span data-stu-id="206fa-113">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 <span data-ttu-id="206fa-114">次に、このサンプルではデザイナーを作成し、そのプライマリ <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> および <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> をユーザー インターフェイスの適切なコンテナーに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="206fa-114">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="206fa-115">次の例に示すいくつかのコード行について説明します。</span><span class="sxs-lookup"><span data-stu-id="206fa-115">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="206fa-116"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> 呼び出しは、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] に付属しているアクティビティの既定のアクティビティ デザイナーを関連付けるために必要です。</span><span class="sxs-lookup"><span data-stu-id="206fa-116">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="206fa-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> は、編集する WF 項目を渡すために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="206fa-117"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="206fa-118">最後に、<xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (プライマリ キャンバス) および <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (プロパティ グリッド) がユーザー インターフェイス画面に配置されます。</span><span class="sxs-lookup"><span data-stu-id="206fa-118">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="206fa-119">再ホストされたツールボックスの使用</span><span class="sxs-lookup"><span data-stu-id="206fa-119">Using the rehosted toolbox</span></span>  
 <span data-ttu-id="206fa-120">このサンプルでは、XAML で宣言によって再ホストされたツールボックス コントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="206fa-120">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="206fa-121">コードで型を <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> コンストラクターに渡すことができることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="206fa-121">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a><span data-ttu-id="206fa-122">サンプルの使用</span><span class="sxs-lookup"><span data-stu-id="206fa-122">Using the sample</span></span>  
  
1.  <span data-ttu-id="206fa-123">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で DesignerRehosting.sln ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="206fa-123">Open the DesignerRehosting.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="206fa-124">F5 キーを押してアプリケーションをコンパイルし、実行します。</span><span class="sxs-lookup"><span data-stu-id="206fa-124">Press F5 to compile and run the application.</span></span>  
  
3.  <span data-ttu-id="206fa-125">WPF アプリケーションが再ホストされたデザイナーと共に起動します。</span><span class="sxs-lookup"><span data-stu-id="206fa-125">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="206fa-126">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="206fa-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="206fa-127">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="206fa-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="206fa-128">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="206fa-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="206fa-129">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="206fa-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`  
  
## <a name="see-also"></a><span data-ttu-id="206fa-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="206fa-130">See Also</span></span>
