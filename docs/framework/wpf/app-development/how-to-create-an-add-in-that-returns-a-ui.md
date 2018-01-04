---
title: "方法 : UI を返すアドインを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 361983c4e2b392cdf8410fdb1193a56f6d26d067
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a><span data-ttu-id="9f5b9-102">方法 : UI を返すアドインを作成する</span><span class="sxs-lookup"><span data-stu-id="9f5b9-102">How to: Create an Add-In That Returns a UI</span></span>
<span data-ttu-id="9f5b9-103">この例は、アドインを表すオブジェクトを作成する方法を示しています、 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]ホストに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]スタンドアロン アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-103">This example shows how to create an add-in that returns a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)][!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to a host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application.</span></span>  
  
 <span data-ttu-id="9f5b9-104">アドインを返します、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]されている、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ユーザー コントロールです。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-104">The add-in returns a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that is a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] user control.</span></span> <span data-ttu-id="9f5b9-105">ユーザー コントロールの中身は 1 つのボタンであり、クリックすると、メッセージ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-105">The content of the user control is a single button that, when clicked, displays a message box.</span></span> <span data-ttu-id="9f5b9-106">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]スタンドアロン アプリケーションがアドインをホストし、アプリケーションのメイン ウィンドウの内容として (アドインによって返される) ユーザー コントロールを表示します。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-106">The [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] standalone application hosts the add-in and displays the user control (returned by the add-in) as the content of the main application window.</span></span>  
  
 <span data-ttu-id="9f5b9-107">**必須コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="9f5b9-107">**Prerequisites**</span></span>  
  
 <span data-ttu-id="9f5b9-108">この例を強調表示、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]拡張機能を[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドインでは、このシナリオを有効にし、モデルを次を前提としています。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-108">This example highlights the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model that enable this scenario, and assumes the following:</span></span>  
  
-   <span data-ttu-id="9f5b9-109">ナレッジ、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドインなど、モデル パイプライン、アドインでは、ホストの開発。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-109">Knowledge of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, including pipeline, add-in, and host development.</span></span> <span data-ttu-id="9f5b9-110">これらの概念に慣れていない場合は、次を参照してください。[アドインおよび拡張](../../../../docs/framework/add-ins/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-110">If you are unfamiliar with these concepts, see [Add-ins and Extensibility](../../../../docs/framework/add-ins/index.md).</span></span> <span data-ttu-id="9f5b9-111">パイプライン、アドイン、およびホスト アプリケーションの実装を示すチュートリアルでは、次を参照してください。[チュートリアル: 拡張性のあるアプリケーションを作成する](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-111">For a tutorial that demonstrates the implementation of a pipeline, an add-in, and a host application, see [Walkthrough: Creating an Extensible Application](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).</span></span>  
  
-   <span data-ttu-id="9f5b9-112">ナレッジ、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]拡張機能を[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドインでは、モデルをご覧ください: [WPF のアドインの概要](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-112">Knowledge of the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] extensions to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model, which can be found here: [WPF Add-Ins Overview](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f5b9-113">例</span><span class="sxs-lookup"><span data-stu-id="9f5b9-113">Example</span></span>  
 <span data-ttu-id="9f5b9-114">アドインを表すオブジェクトを作成する、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]パイプラインの各セグメント、アドイン、およびホスト アプリケーションの特定のコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-114">To create an add-in that returns a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] requires specific code for each pipeline segment, the add-in, and the host application.</span></span>  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a><span data-ttu-id="9f5b9-115">コントラクト パイプライン セグメントの実装</span><span class="sxs-lookup"><span data-stu-id="9f5b9-115">Implementing the Contract Pipeline Segment</span></span>  
 <span data-ttu-id="9f5b9-116">メソッドを返すためのコントラクトを定義する必要があります、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、その戻り値型でなければなりませんと<xref:System.AddIn.Contract.INativeHandleContract>です。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-116">A method must be defined by the contract for returning a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and its return value must be of type <xref:System.AddIn.Contract.INativeHandleContract>.</span></span> <span data-ttu-id="9f5b9-117">示されるこれは、`GetAddInUI`のメソッド、`IWPFAddInContract`次のコード コントラクトします。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-117">This is demonstrated by the `GetAddInUI` method of the `IWPFAddInContract` contract in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a><span data-ttu-id="9f5b9-118">アドイン ビュー パイプライン セグメントの実装</span><span class="sxs-lookup"><span data-stu-id="9f5b9-118">Implementing the Add-In View Pipeline Segment</span></span>  
 <span data-ttu-id="9f5b9-119">アドインが実装されているため、[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]のサブクラスとして提供<xref:System.Windows.FrameworkElement>に対応する追加のビューのメソッドは、`IWPFAddInView.GetAddInUI`型の値を返す必要があります<xref:System.Windows.FrameworkElement>です。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-119">Because the add-in implements the [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] it provides as subclasses of <xref:System.Windows.FrameworkElement>, the method on the add-in view that correlates to `IWPFAddInView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="9f5b9-120">次のコードは、コントラクトのアドイン ビューがインターフェイスとして実装されることを示しています。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-120">The following code shows the add-in view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a><span data-ttu-id="9f5b9-121">アドイン側アダプター パイプライン セグメントの実装</span><span class="sxs-lookup"><span data-stu-id="9f5b9-121">Implementing the Add-In-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="9f5b9-122">コントラクト メソッドを返します、 <xref:System.AddIn.Contract.INativeHandleContract>、アドインを返しますが、 <xref:System.Windows.FrameworkElement> (指定に従って、追加のビュー)。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-122">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the add-in returns a <xref:System.Windows.FrameworkElement> (as specified by the add-in view).</span></span> <span data-ttu-id="9f5b9-123">その結果、<xref:System.Windows.FrameworkElement>に変換する必要があります、<xref:System.AddIn.Contract.INativeHandleContract>分離境界を横断する前にします。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-123">Consequently, the <xref:System.Windows.FrameworkElement> must be converted to an <xref:System.AddIn.Contract.INativeHandleContract> before crossing the isolation boundary.</span></span> <span data-ttu-id="9f5b9-124">呼び出して追加側アダプターでこの作業を行う<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-124">This work is performed by the add-in-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a><span data-ttu-id="9f5b9-125">ホスト ビュー パイプライン セグメントの実装</span><span class="sxs-lookup"><span data-stu-id="9f5b9-125">Implementing the Host View Pipeline Segment</span></span>  
 <span data-ttu-id="9f5b9-126">ホスト アプリケーションが表示されるため、<xref:System.Windows.FrameworkElement>に対応するホスト ビューのメソッドは、`IWPFAddInHostView.GetAddInUI`型の値を返す必要があります<xref:System.Windows.FrameworkElement>です。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-126">Because the host application will display a <xref:System.Windows.FrameworkElement>, the method on the host view that correlates to `IWPFAddInHostView.GetAddInUI` must return a value of type <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="9f5b9-127">次のコードは、コントラクトのホスト ビューがインターフェイスとして実装されることを示しています。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-127">The following code shows the host view of the contract, implemented as an interface.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a><span data-ttu-id="9f5b9-128">ホスト側アダプター パイプライン セグメントの実装</span><span class="sxs-lookup"><span data-stu-id="9f5b9-128">Implementing the Host-Side Adapter Pipeline Segment</span></span>  
 <span data-ttu-id="9f5b9-129">コントラクト メソッドを返します、 <xref:System.AddIn.Contract.INativeHandleContract>、ホスト アプリケーションが必要ですが、 <xref:System.Windows.FrameworkElement> (ホスト ビューで、指定した)。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-129">The contract method returns an <xref:System.AddIn.Contract.INativeHandleContract>, but the host application expects a <xref:System.Windows.FrameworkElement> (as specified by the host view).</span></span> <span data-ttu-id="9f5b9-130">その結果、<xref:System.AddIn.Contract.INativeHandleContract>に変換する必要があります、<xref:System.Windows.FrameworkElement>後、分離境界を越えます。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-130">Consequently, the <xref:System.AddIn.Contract.INativeHandleContract> must be converted to a <xref:System.Windows.FrameworkElement> after crossing the isolation boundary.</span></span> <span data-ttu-id="9f5b9-131">呼び出すことによって、ホスト側アダプターでこの作業を行う<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-131">This work is performed by the host-side adapter by calling <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, as shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a><span data-ttu-id="9f5b9-132">アドインの実装</span><span class="sxs-lookup"><span data-stu-id="9f5b9-132">Implementing the Add-In</span></span>  
 <span data-ttu-id="9f5b9-133">アドイン側アダプターとアドインのビューが作成されると、アドイン (`WPFAddIn1.AddIn`) を実装する必要があります、`IWPFAddInView.GetAddInUI`を返すメソッドを<xref:System.Windows.FrameworkElement>オブジェクト (、<xref:System.Windows.Controls.UserControl>この例では)。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-133">With the add-in-side adapter and add-in view created, the add-in (`WPFAddIn1.AddIn`) must implement the `IWPFAddInView.GetAddInUI` method to return a <xref:System.Windows.FrameworkElement> object (a <xref:System.Windows.Controls.UserControl> in this example).</span></span> <span data-ttu-id="9f5b9-134">実装、 <xref:System.Windows.Controls.UserControl>、 `AddInUI`、次のコードで表示されます。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-134">The implementation of the <xref:System.Windows.Controls.UserControl>, `AddInUI`, is shown by the following code.</span></span>  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 <span data-ttu-id="9f5b9-135">実装、 `IWPFAddInView.GetAddInUI` 、アドインで必要があるだけの新しいインスタンスを返す`AddInUI`、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-135">The implementation of the `IWPFAddInView.GetAddInUI` by the add-in simply needs to return a new instance of `AddInUI`, as shown by the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a><span data-ttu-id="9f5b9-136">ホスト アプリケーションの実装</span><span class="sxs-lookup"><span data-stu-id="9f5b9-136">Implementing the Host Application</span></span>  
 <span data-ttu-id="9f5b9-137">ホスト側アダプターと作成されたホスト ビューでは、ホスト アプリケーションを使用して、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドイン モデルをパイプラインを開き、アドイン、および呼び出しのホスト ビューの取得、`IWPFAddInHostView.GetAddInUI`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-137">With the host-side adapter and host view created, the host application can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] add-in model to open the pipeline, acquire a host view of the add-in, and call the `IWPFAddInHostView.GetAddInUI` method.</span></span> <span data-ttu-id="9f5b9-138">これらの手順を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="9f5b9-138">These steps are shown in the following code.</span></span>  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a><span data-ttu-id="9f5b9-139">参照</span><span class="sxs-lookup"><span data-stu-id="9f5b9-139">See Also</span></span>  
 [<span data-ttu-id="9f5b9-140">アドインおよび拡張機能</span><span class="sxs-lookup"><span data-stu-id="9f5b9-140">Add-ins and Extensibility</span></span>](../../../../docs/framework/add-ins/index.md)  
 [<span data-ttu-id="9f5b9-141">WPF のアドインの概要</span><span class="sxs-lookup"><span data-stu-id="9f5b9-141">WPF Add-Ins Overview</span></span>](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
