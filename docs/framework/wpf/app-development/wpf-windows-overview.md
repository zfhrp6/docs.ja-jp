---
title: "WPF ウィンドウの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 594bb21983f51f3c0698c43d0f6ea39594b72705
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="wpf-windows-overview"></a><span data-ttu-id="d3e7a-102">WPF ウィンドウの概要</span><span class="sxs-lookup"><span data-stu-id="d3e7a-102">WPF Windows Overview</span></span>
<span data-ttu-id="d3e7a-103">ユーザーは、ウィンドウをとおして、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] スタンドアロン アプリケーションとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-103">Users interact with [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] standalone applications through windows.</span></span> <span data-ttu-id="d3e7a-104">ウィンドウの主な目的は、データを視覚化してユーザーがデータと対話できるコンテンツをホストすることです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-104">The primary purpose of a window is to host content that visualizes data and enables users to interact with data.</span></span> <span data-ttu-id="d3e7a-105">スタンドアロン[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションを使用して、独自の windows を提供する、<xref:System.Windows.Window>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-105">Standalone [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications provide their own windows by using the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="d3e7a-106">このトピックで紹介<xref:System.Windows.Window>を作成して、スタンドアロン アプリケーションで windows の管理の基礎を紹介します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-106">This topic introduces <xref:System.Windows.Window> before covering the fundamentals of creating and managing windows in standalone applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3e7a-107">ブラウザーによってホストされる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]など、アプリケーション[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]厳密でないと[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ページは、独自の windows で提供されません。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-107">Browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pages, don't provide their own windows.</span></span> <span data-ttu-id="d3e7a-108">代わりに、によって提供されるウィンドウでホストされている[!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-108">Instead, they are hosted in windows provided by [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)].</span></span> <span data-ttu-id="d3e7a-109">参照してください[WPF XAML ブラウザー アプリケーションの概要](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-109">See [WPF XAML Browser Applications Overview](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md).</span></span>  
  
  
<a name="TheWindowClass"></a>   
## <a name="the-window-class"></a><span data-ttu-id="d3e7a-110">ウィンドウ クラス</span><span class="sxs-lookup"><span data-stu-id="d3e7a-110">The Window Class</span></span>  
 <span data-ttu-id="d3e7a-111">次の図は、ウィンドウの構成パーツを示しています。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-111">The following figure illustrates the constituent parts of a window.</span></span>  
  
 <span data-ttu-id="d3e7a-112">![ウィンドウ要素](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")</span><span class="sxs-lookup"><span data-stu-id="d3e7a-112">![Window elements](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure1.PNG "WindowOverviewFigure1")</span></span>  
  
 <span data-ttu-id="d3e7a-113">ウィンドウは、非クライアント領域とクライアント領域の 2 つに分かれます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-113">A window is divided into two areas: the non-client area and client area.</span></span>  
  
 <span data-ttu-id="d3e7a-114">*非クライアント領域*ウィンドウのによって実装されて[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]と、次を含む、ほとんどの windows に共通のウィンドウの部分が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-114">The *non-client area* of a window is implemented by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and includes the parts of a window that are common to most windows, including the following:</span></span>  
  
-   <span data-ttu-id="d3e7a-115">境界線。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-115">A border.</span></span>  
  
-   <span data-ttu-id="d3e7a-116">タイトル バー。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-116">A title bar.</span></span>  
  
-   <span data-ttu-id="d3e7a-117">アイコン。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-117">An icon.</span></span>  
  
-   <span data-ttu-id="d3e7a-118">最小化ボタン、最大化ボタン、および元に戻すボタン。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-118">Minimize, Maximize, and Restore buttons.</span></span>  
  
-   <span data-ttu-id="d3e7a-119">閉じるボタン。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-119">A Close button.</span></span>  
  
-   <span data-ttu-id="d3e7a-120">ウィンドウを最小化、最大化、元のサイズに戻す、移動、サイズ変更、および閉じるためのメニュー項目を含むシステム メニュー。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-120">A System menu with menu items that allow users to minimize, maximize, restore, move, resize, and close a window.</span></span>  
  
 <span data-ttu-id="d3e7a-121">*クライアント領域*ウィンドウのウィンドウの非クライアント領域内の領域は、メニュー バー、ツール バー コントロールなどのアプリケーション固有のコンテンツを追加する開発者によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-121">The *client area* of a window is the area within a window's non-client area and is used by developers to add application-specific content, such as menu bars, tool bars, and controls.</span></span>  
  
 <span data-ttu-id="d3e7a-122">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、ウィンドウがによってカプセル化、<xref:System.Windows.Window>次の操作に使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a window is encapsulated by the <xref:System.Windows.Window> class that you use to do the following:</span></span>  
  
-   <span data-ttu-id="d3e7a-123">ウィンドウを表示する。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-123">Display a window.</span></span>  
  
-   <span data-ttu-id="d3e7a-124">ウィンドウのサイズ、位置、および外観を構成する。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-124">Configure the size, position, and appearance of a window.</span></span>  
  
-   <span data-ttu-id="d3e7a-125">アプリケーション固有のコンテンツをホストする。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-125">Host application-specific content.</span></span>  
  
-   <span data-ttu-id="d3e7a-126">ウィンドウの有効期間を管理する。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-126">Manage the lifetime of a window.</span></span>  
  
<a name="DefiningAWindow"></a>   
## <a name="implementing-a-window"></a><span data-ttu-id="d3e7a-127">ウィンドウの実装</span><span class="sxs-lookup"><span data-stu-id="d3e7a-127">Implementing a Window</span></span>  
 <span data-ttu-id="d3e7a-128">一般的なウィンドウの実装は、外観と動作の両方で構成されますここで*外観*をユーザーに、ウィンドウの外観を定義および*動作*ユーザー対話状態ウィンドウの機能方法を定義。関連付けします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-128">The implementation of a typical window comprises both appearance and behavior, where *appearance* defines how a window looks to users and *behavior* defines the way a window functions as users interact with it.</span></span> <span data-ttu-id="d3e7a-129">[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]外観を実装することができを使用してウィンドウの動作をコーディングするか、または[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-129">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], you can implement the appearance and behavior of a window using either code or [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 <span data-ttu-id="d3e7a-130">一般に、ただし、ウィンドウの外観は実装を使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ、およびその動作は実装されている分離コードを使用して次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-130">In general, however, the appearance of a window is implemented using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and its behavior is implemented using code-behind, as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 <span data-ttu-id="d3e7a-131">有効にする、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ ファイルと連携して動作する分離コード ファイルに、次は、必要な。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-131">To enable a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup file and code-behind file to work together, the following are required:</span></span>  
  
-   <span data-ttu-id="d3e7a-132">マークアップで、`Window`要素を含める必要があります、`x:Class`属性。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-132">In markup, the `Window` element must include the `x:Class` attribute.</span></span> <span data-ttu-id="d3e7a-133">アプリケーションのビルド時の存在`x:Class`マークアップ ファイルが原因となって[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]を作成する、`partial`から派生したクラス<xref:System.Windows.Window>によって指定される名前を持つ、`x:Class`属性。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-133">When the application is built, the existence of `x:Class` in the markup file causes [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] to create a `partial` class that derives from <xref:System.Windows.Window> and has the name that is specified by the `x:Class` attribute.</span></span> <span data-ttu-id="d3e7a-134">追加が必要です、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]の名前空間宣言、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]スキーマ ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` )。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-134">This requires the addition of an [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] namespace declaration for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).</span></span> <span data-ttu-id="d3e7a-135">生成された`partial`クラスが実装する、`InitializeComponent`メソッド、イベントを登録し、マークアップに実装されているプロパティを設定すると呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-135">The generated `partial` class implements the `InitializeComponent` method, which is called to register the events and set the properties that are implemented in markup.</span></span>  
  
-   <span data-ttu-id="d3e7a-136">分離コード クラスがある必要があります、`partial`によって指定される同じ名前のクラス、`x:Class`マークアップ、およびその属性がから派生する必要があります<xref:System.Windows.Window>です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-136">In code-behind, the class must be a `partial` class with the same name that is specified by the `x:Class` attribute in markup, and it must derive from <xref:System.Windows.Window>.</span></span> <span data-ttu-id="d3e7a-137">これにより、分離コード ファイルに関連付けられる、`partial`アプリケーションのビルド時に、マークアップ ファイルに対して生成されるクラス (を参照してください[WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md))。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-137">This allows the code-behind file to be associated with the `partial` class that is generated for the markup file when the application is built (see [Building a WPF Application](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).</span></span>  
  
-   <span data-ttu-id="d3e7a-138">分離コードで、<xref:System.Windows.Window>クラスは、呼び出すコンス トラクターを実装する必要があります、`InitializeComponent`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-138">In code-behind, the <xref:System.Windows.Window> class must implement a constructor that calls the `InitializeComponent` method.</span></span> <span data-ttu-id="d3e7a-139">`InitializeComponent`実装ファイルの生成されたマークアップで`partial`イベントを登録し、マークアップで定義されているプロパティを設定するクラス。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-139">`InitializeComponent` is implemented by the markup file's generated `partial` class to register events and set properties that are defined in markup.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3e7a-140">新しいを追加すると<xref:System.Windows.Window>を使用してプロジェクトに[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、<xref:System.Windows.Window>マークアップと分離コードの両方を使用して実装され、としてマークアップおよび分離コード ファイル間の関連付けを作成するために必要な構成が含まれていますここで説明します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-140">When you add a new <xref:System.Windows.Window> to your project by using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], the <xref:System.Windows.Window> is implemented using both markup and code-behind, and includes the necessary configuration to create the association between the markup and code-behind files as described here.</span></span>  
  
 <span data-ttu-id="d3e7a-141">この構成は、ウィンドウの外観を定義するのに集中できます[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップと分離コードでその動作を実装します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-141">With this configuration in place, you can focus on defining the appearance of the window in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and implementing its behavior in code-behind.</span></span> <span data-ttu-id="d3e7a-142">次の例とで実装された、ボタン、ウィンドウ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ、およびボタンのイベント ハンドラー<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント、分離コードで実装します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-142">The following example shows a window with a button, implemented in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup, and an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, implemented in code-behind.</span></span>  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>   
## <a name="configuring-a-window-definition-for-msbuild"></a><span data-ttu-id="d3e7a-143">MSBuild 用のウィンドウ定義の構成</span><span class="sxs-lookup"><span data-stu-id="d3e7a-143">Configuring a Window Definition for MSBuild</span></span>  
 <span data-ttu-id="d3e7a-144">構成方法、ウィンドウを実装する方法を決定[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-144">How you implement your window determines how it is configured for [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)].</span></span> <span data-ttu-id="d3e7a-145">両方を使用して定義されているウィンドウの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップと分離コード。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-145">For a window that is defined using both [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind:</span></span>  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <span data-ttu-id="d3e7a-146">として構成されているマークアップ ファイル[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-146">markup files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items.</span></span>  
  
-   <span data-ttu-id="d3e7a-147">分離コード ファイルとして構成されている[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile`項目。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-147">Code-behind files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Compile` items.</span></span>  
  
 <span data-ttu-id="d3e7a-148">これは、次に示すは[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]プロジェクト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-148">This is shown in the following [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] project file.</span></span>  
  
```xml  
<Project ...  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 <span data-ttu-id="d3e7a-149">ビルドについて[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションを参照してください[WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-149">For information about building [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, see [Building a WPF Application](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).</span></span>  
  
<a name="WindowLifetime"></a>   
## <a name="window-lifetime"></a><span data-ttu-id="d3e7a-150">ウィンドウの有効期間</span><span class="sxs-lookup"><span data-stu-id="d3e7a-150">Window Lifetime</span></span>  
 <span data-ttu-id="d3e7a-151">クラスと同様に、ウィンドウにも有効期間があります。有効期間は、ウィンドウが開いて最初にインスタンス化されたときに開始し、アクティブ化と非アクティブ化を経て、最後に閉じられるまで継続します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-151">As with any class, a window has a lifetime that begins when it is first instantiated, after which it is opened, activated and deactivated, and eventually closed.</span></span>  
  
  
<a name="Opening_a_Window"></a>   
### <a name="opening-a-window"></a><span data-ttu-id="d3e7a-152">ウィンドウを開く</span><span class="sxs-lookup"><span data-stu-id="d3e7a-152">Opening a Window</span></span>  
 <span data-ttu-id="d3e7a-153">ウィンドウを開くには、次の例に示すように最初にインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-153">To open a window, you first create an instance of it, which is demonstrated in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 <span data-ttu-id="d3e7a-154">この例では、`MarkupAndCodeBehindWindow`が発生する、アプリケーションの起動時にインスタンス化されるときに、<xref:System.Windows.Application.Startup>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-154">In this example, the `MarkupAndCodeBehindWindow` is instantiated when the application starts, which occurs when the <xref:System.Windows.Application.Startup> event is raised.</span></span>  
  
 <span data-ttu-id="d3e7a-155">参照が自動的に追加で管理されている windows のリストにウィンドウをインスタンス化されるときに、<xref:System.Windows.Application>オブジェクト (を参照してください<xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-155">When a window is instantiated, a reference to it is automatically added to a list of windows that is managed by the <xref:System.Windows.Application> object (see <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType>).</span></span> <span data-ttu-id="d3e7a-156">さらに、最初のウィンドウがインスタンス化するのには、既定では、設定<xref:System.Windows.Application>アプリケーションのメイン ウィンドウとして (を参照してください<xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-156">Additionally, the first window to be instantiated is, by default, set by <xref:System.Windows.Application> as the main application window (see <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="d3e7a-157">呼び出して、ウィンドウが開かれた最後に、<xref:System.Windows.Window.Show%2A>メソッドです。 結果が次の図に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-157">The window is finally opened by calling the <xref:System.Windows.Window.Show%2A> method; the result is shown in the following figure.</span></span>  
  
 <span data-ttu-id="d3e7a-158">![Window.Show の呼び出しによって開いたウィンドウ](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")</span><span class="sxs-lookup"><span data-stu-id="d3e7a-158">![A Window Opened by Calling Window.Show](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure8.png "WindowOverviewFigure8")</span></span>  
  
 <span data-ttu-id="d3e7a-159">呼び出しによって開かれたウィンドウ<xref:System.Windows.Window.Show%2A>はモードレス ウィンドウは、アプリケーションはユーザーが、同じアプリケーション内の他のウィンドウをアクティブにできるモードで動作することを意味します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-159">A window that is opened by calling <xref:System.Windows.Window.Show%2A> is a modeless window, which means that the application operates in a mode that allows users to activate other windows in the same application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3e7a-160"><xref:System.Windows.Window.ShowDialog%2A>モーダル ダイアログ ボックスなどのウィンドウを開くと呼びます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-160"><xref:System.Windows.Window.ShowDialog%2A> is called to open windows such as dialog boxes modally.</span></span> <span data-ttu-id="d3e7a-161">参照してください[ダイアログ ボックスの概要](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-161">See [Dialog Boxes Overview](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md) for more information.</span></span>  
  
 <span data-ttu-id="d3e7a-162">ときに<xref:System.Windows.Window.Show%2A>が呼び出されると、ウィンドウの初期化作業をする前に実行ユーザー入力を受信することを許可するインフラストラクチャを確立するために表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-162">When <xref:System.Windows.Window.Show%2A> is called, a window performs initialization work before it is shown to establish infrastructure that allows it to receive user input.</span></span> <span data-ttu-id="d3e7a-163">ウィンドウが初期化されたときに、<xref:System.Windows.Window.SourceInitialized>イベントが発生し、ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-163">When the window is initialized, the <xref:System.Windows.Window.SourceInitialized> event is raised and the window is shown.</span></span>  
  
 <span data-ttu-id="d3e7a-164">簡単な方法として<xref:System.Windows.Application.StartupUri%2A>アプリケーションの起動時に自動的に開かれている最初のウィンドウを指定する設定できます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-164">As a shortcut, <xref:System.Windows.Application.StartupUri%2A> can be set to specify the first window that is opened automatically when an application starts.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 <span data-ttu-id="d3e7a-165">アプリケーションの開始時の値によって指定されたウィンドウ<xref:System.Windows.Application.StartupUri%2A>が開かれているを呼び出して、ウィンドウが開いたモードレス; 内部的には、その<xref:System.Windows.Window.Show%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-165">When the application starts, the window specified by the value of <xref:System.Windows.Application.StartupUri%2A> is opened modelessly; internally, the window is opened by calling its <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
<a name="Ownership"></a>   
#### <a name="window-ownership"></a><span data-ttu-id="d3e7a-166">ウィンドウの所有権</span><span class="sxs-lookup"><span data-stu-id="d3e7a-166">Window Ownership</span></span>  
 <span data-ttu-id="d3e7a-167">使用して開かれているウィンドウ、<xref:System.Windows.Window.Show%2A>メソッドには、暗黙的なリレーションシップを作成したウィンドウではありません。 ユーザーは、いずれかのウィンドウで、次を実行できることを意味とは無関係に、その他のいずれかのウィンドウと対話できます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-167">A window that is opened by using the <xref:System.Windows.Window.Show%2A> method does not have an implicit relationship with the window that created it; users can interact with either window independently of the other, which means that either window can do the following:</span></span>  
  
-   <span data-ttu-id="d3e7a-168">他の説明 (、windows のいずれかがあるない限り、<xref:System.Windows.Window.Topmost%2A>プロパティに設定`true`)。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-168">Cover the other (unless one of the windows has its <xref:System.Windows.Window.Topmost%2A> property set to `true`).</span></span>  
  
-   <span data-ttu-id="d3e7a-169">もう一方のウィンドウに影響を与えずに、最小化/最大化し、元のサイズに戻す。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-169">Be minimized, maximized, and restored without affecting the other.</span></span>  
  
 <span data-ttu-id="d3e7a-170">一部のウィンドウには、そのウィンドウを開いたウィンドウとの関係が必要です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-170">Some windows require a relationship with the window that opens them.</span></span> <span data-ttu-id="d3e7a-171">たとえば、[!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)]アプリケーションは、プロパティ ウィンドウやが通常の動作は、それを作成したウィンドウをカバーするツール ウィンドウを開くことがあります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-171">For example, an [!INCLUDE[TLA#tla_ide](../../../../includes/tlasharptla-ide-md.md)] application may open property windows and tool windows whose typical behavior is to cover the window that creates them.</span></span> <span data-ttu-id="d3e7a-172">また、そのようなウィンドウは、必ず作成元のウィンドウと一緒に閉じ、最小化/最大化し、元のサイズに戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-172">Furthermore, such windows should always close, minimize, maximize, and restore in concert with the window that created them.</span></span> <span data-ttu-id="d3e7a-173">このようなリレーションシップは 1 つのウィンドウを確立することができます*独自*別を設定して、実行されますが、<xref:System.Windows.Window.Owner%2A>のプロパティ、*ウィンドウの所有*への参照で、*所有者ウィンドウ*します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-173">Such a relationship can be established by making one window *own* another, and is achieved by setting the <xref:System.Windows.Window.Owner%2A> property of the *owned window* with a reference to the *owner window*.</span></span> <span data-ttu-id="d3e7a-174">これを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-174">This is shown in the following example.</span></span>  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 <span data-ttu-id="d3e7a-175">所有権が確立されると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-175">After ownership is established:</span></span>  
  
-   <span data-ttu-id="d3e7a-176">所有されているウィンドウの値を調べることによって、オーナー ウィンドウを参照することができます、<xref:System.Windows.Window.Owner%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-176">The owned window can reference its owner window by inspecting the value of its <xref:System.Windows.Window.Owner%2A> property.</span></span>  
  
-   <span data-ttu-id="d3e7a-177">値を調べることによって、所有するすべての windows を検出できるは、オーナー ウィンドウの<xref:System.Windows.Window.OwnedWindows%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-177">The owner window can discover all the windows it owns by inspecting the value of its <xref:System.Windows.Window.OwnedWindows%2A> property.</span></span>  
  
<a name="Preventing"></a>   
#### <a name="preventing-window-activation"></a><span data-ttu-id="d3e7a-178">ウィンドウのアクティブ化の防止</span><span class="sxs-lookup"><span data-stu-id="d3e7a-178">Preventing Window Activation</span></span>  
 <span data-ttu-id="d3e7a-179">ここで windows アクティブにしないインターネット messenger スタイル アプリケーションのメッセージ交換の windows または電子メール アプリケーションの通知ウィンドウなど、表示されるとシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-179">There are scenarios where windows should not be activated when shown, such as conversation windows of an Internet messenger-style application or notification windows of an email application.</span></span>  
  
 <span data-ttu-id="d3e7a-180">設定することができます、アプリケーションに表示されるとアクティブ化することはできません、ウィンドウがある場合は、その<xref:System.Windows.Window.ShowActivated%2A>プロパティを`false`呼び出す前に、<xref:System.Windows.Window.Show%2A>が最初にメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-180">If your application has a window that shouldn't be activated when shown, you can set its <xref:System.Windows.Window.ShowActivated%2A> property to `false` before calling the <xref:System.Windows.Window.Show%2A> method for the first time.</span></span> <span data-ttu-id="d3e7a-181">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-181">As a consequence:</span></span>  
  
-   <span data-ttu-id="d3e7a-182">ウィンドウはアクティブになりません。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-182">The window is not activated.</span></span>  
  
-   <span data-ttu-id="d3e7a-183">ウィンドウの<xref:System.Windows.Window.Activated>イベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-183">The window's <xref:System.Windows.Window.Activated> event is not raised.</span></span>  
  
-   <span data-ttu-id="d3e7a-184">現在アクティブなウィンドウは、アクティブのままです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-184">The currently activated window remains activated.</span></span>  
  
 <span data-ttu-id="d3e7a-185">ただし、ユーザーがクライアント領域または非クライアント領域をクリックすると、ウィンドウは直ちにアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-185">The window will become activated, however, as soon as the user activates it by clicking either the client or non-client area.</span></span> <span data-ttu-id="d3e7a-186">この場合、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-186">In this case:</span></span>  
  
-   <span data-ttu-id="d3e7a-187">ウィンドウはアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-187">The window is activated.</span></span>  
  
-   <span data-ttu-id="d3e7a-188">ウィンドウの<xref:System.Windows.Window.Activated>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-188">The window's <xref:System.Windows.Window.Activated> event is raised.</span></span>  
  
-   <span data-ttu-id="d3e7a-189">直前にアクティブだったウィンドウは非アクティブになります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-189">The previously activated window is deactivated.</span></span>  
  
-   <span data-ttu-id="d3e7a-190">ウィンドウの<xref:System.Windows.Window.Deactivated>と<xref:System.Windows.Window.Activated>イベント発生するか、後でユーザーの操作への応答で想定どおりにします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-190">The window's <xref:System.Windows.Window.Deactivated> and <xref:System.Windows.Window.Activated> events are subsequently raised as expected in response to user actions.</span></span>  
  
<a name="Window_Activation"></a>   
### <a name="window-activation"></a><span data-ttu-id="d3e7a-191">ウィンドウのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="d3e7a-191">Window Activation</span></span>  
 <span data-ttu-id="d3e7a-192">最初に、ウィンドウを開くと、アクティブなウィンドウになります (表示される場合を除き、 <xref:System.Windows.Window.ShowActivated%2A> 'éý' `false`)。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-192">When a window is first opened, it becomes the active window (unless it is shown with <xref:System.Windows.Window.ShowActivated%2A> set to `false`).</span></span> <span data-ttu-id="d3e7a-193">*アクティブなウィンドウ*ウィンドウは現在、キー ストロークやマウス クリックなどのユーザー入力をキャプチャしています。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-193">The *active window* is the window that is currently capturing user input, such as key strokes and mouse clicks.</span></span> <span data-ttu-id="d3e7a-194">ウィンドウがアクティブになったときに発生、<xref:System.Windows.Window.Activated>イベント。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-194">When a window becomes active, it raises the <xref:System.Windows.Window.Activated> event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3e7a-195">最初に、ウィンドウを開くと、<xref:System.Windows.FrameworkElement.Loaded>と<xref:System.Windows.Window.ContentRendered>イベントが発生した後に、<xref:System.Windows.Window.Activated>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-195">When a window is first opened, the <xref:System.Windows.FrameworkElement.Loaded> and <xref:System.Windows.Window.ContentRendered> events are raised only after the <xref:System.Windows.Window.Activated> event is raised.</span></span> <span data-ttu-id="d3e7a-196">これを踏まえて、ウィンドウ効果的に対象となるときに開かれた<xref:System.Windows.Window.ContentRendered>が発生します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-196">With this in mind, a window can effectively be considered opened when <xref:System.Windows.Window.ContentRendered> is raised.</span></span>  
  
 <span data-ttu-id="d3e7a-197">ウィンドウがアクティブになった後で、ユーザーは同じアプリケーションの別のウィンドウをアクティブ化したり、別のアプリケーションをアクティブ化したりできます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-197">After a window becomes active, a user can activate another window in the same application, or activate another application.</span></span> <span data-ttu-id="d3e7a-198">現在アクティブなウィンドウが非アクティブになりを発生させますが発生したときに、<xref:System.Windows.Window.Deactivated>イベント。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-198">When that happens, the currently active window becomes deactivated and raises the <xref:System.Windows.Window.Deactivated> event.</span></span> <span data-ttu-id="d3e7a-199">同様に、ユーザーは、現在非アクティブ化されたウィンドウを選択するときに、ウィンドウが再びアクティブと<xref:System.Windows.Window.Activated>が発生します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-199">Likewise, when the user selects a currently deactivated window, the window becomes active again and <xref:System.Windows.Window.Activated> is raised.</span></span>  
  
 <span data-ttu-id="d3e7a-200">処理する 1 つの一般的な理由<xref:System.Windows.Window.Activated>と<xref:System.Windows.Window.Deactivated>を有効にし、ウィンドウがアクティブなときにのみ実行可能な機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-200">One common reason to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> is to enable and disable functionality that can only run when a window is active.</span></span> <span data-ttu-id="d3e7a-201">たとえば、ゲームやビデオ プレーヤーなど、ユーザーの一定の入力や介入が必要な対話型コンテンツが表示されるウィンドウがあります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-201">For example, some windows display interactive content that requires constant user input or attention, including games and video players.</span></span> <span data-ttu-id="d3e7a-202">次の例は、処理する方法を示す簡略化されたビデオ プレーヤー<xref:System.Windows.Window.Activated>と<xref:System.Windows.Window.Deactivated>この動作を実装します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-202">The following example is a simplified video player that demonstrates how to handle <xref:System.Windows.Window.Activated> and <xref:System.Windows.Window.Deactivated> to implement this behavior.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 <span data-ttu-id="d3e7a-203">ウィンドウが非アクティブでも、バックグラウンドでコードを実行できる種類のアプリケーションもあります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-203">Other types of applications may still run code in the background when a window is deactivated.</span></span> <span data-ttu-id="d3e7a-204">たとえば、メール クライアントは、ユーザーが他のアプリケーションを使用している間もメール サーバーへのポーリングを続けています。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-204">For example, a mail client may continue polling the mail server while the user is using other applications.</span></span> <span data-ttu-id="d3e7a-205">このようなアプリケーションは、メイン ウィンドウが非アクティブのときにも、別の動作や追加の動作を頻繁に実行します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-205">Applications like these often provide different or additional behavior while the main window is deactivated.</span></span> <span data-ttu-id="d3e7a-206">メール プログラムでは、新しいメール アイテムを受信トレイに追加し、通知アイコンをシステム トレイに追加することがあります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-206">With respect to the mail program, this may mean both adding the new mail item to the inbox and adding a notification icon to the system tray.</span></span> <span data-ttu-id="d3e7a-207">[メール] ウィンドウがアクティブで、調べることによって確認できますがでない場合、通知アイコンを表示する必要があるのみ、<xref:System.Windows.Window.IsActive%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-207">A notification icon need only be displayed when the mail window isn't active, which can be determined by inspecting the <xref:System.Windows.Window.IsActive%2A> property.</span></span>  
  
 <span data-ttu-id="d3e7a-208">バック グラウンド タスクを完了すると場合、は、ウィンドウは呼び出すことによってより緊急ユーザーに通知する<xref:System.Windows.Window.Activate%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-208">If a background task completes, a window may want to notify the user more urgently by calling <xref:System.Windows.Window.Activate%2A> method.</span></span> <span data-ttu-id="d3e7a-209">別のアプリケーションがときにアクティブ化された場合は、ユーザーと対話<xref:System.Windows.Window.Activate%2A>が呼び出されると、ウィンドウのタスク バー ボタンが点滅します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-209">If the user is interacting with another application activated when <xref:System.Windows.Window.Activate%2A> is called, the window's taskbar button flashes.</span></span> <span data-ttu-id="d3e7a-210">ユーザーは、現在のアプリケーションと対話して場合、呼び出し元<xref:System.Windows.Window.Activate%2A>が前面に、ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-210">If a user is interacting with the current application, calling <xref:System.Windows.Window.Activate%2A> will bring the window to the foreground.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3e7a-211">アプリケーション スコープのアクティブ化を使用して処理することができます、<xref:System.Windows.Application.Activated?displayProperty=nameWithType>と<xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>イベント。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-211">You can handle application-scope activation using the <xref:System.Windows.Application.Activated?displayProperty=nameWithType> and <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> events.</span></span>  
  
<a name="Closing_a_Window"></a>   
### <a name="closing-a-window"></a><span data-ttu-id="d3e7a-212">ウィンドウを閉じる</span><span class="sxs-lookup"><span data-stu-id="d3e7a-212">Closing a Window</span></span>  
 <span data-ttu-id="d3e7a-213">ウィンドウの有効期間は、表示されたときに開始し、ユーザーが閉じたときに終了します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-213">The life of a window starts coming to an end when a user closes it.</span></span> <span data-ttu-id="d3e7a-214">ウィンドウを閉じるには、非クライアント領域の要素を使用します。これには、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-214">A window can be closed by using elements in the non-client area, including the following:</span></span>  
  
-   <span data-ttu-id="d3e7a-215">**閉じる**の項目、**システム**メニュー。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-215">The **Close** item of the **System** menu.</span></span>  
  
-   <span data-ttu-id="d3e7a-216">Alt キーを押しながら F4 キーを押す。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-216">Pressing ALT+F4.</span></span>  
  
-   <span data-ttu-id="d3e7a-217">キーを押して、**閉じる**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-217">Pressing the **Close** button.</span></span>  
  
 <span data-ttu-id="d3e7a-218">クライアント領域にさらに機構を追加してウィンドウを閉じることもできます。その一般的な例を、次に示します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-218">You can provide additional mechanisms to the client area to close a window, the more common of which include the following:</span></span>  
  
-   <span data-ttu-id="d3e7a-219">**終了**内の項目、**ファイル**メイン アプリケーションの windows の通常のメニュー。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-219">An **Exit** item in the **File** menu, typically for main application windows.</span></span>  
  
-   <span data-ttu-id="d3e7a-220">A**閉じる**内の項目、**ファイル**一般に、セカンダリのアプリケーション ウィンドウのメニュー。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-220">A **Close** item in the **File** menu, typically on a secondary application window.</span></span>  
  
-   <span data-ttu-id="d3e7a-221">A**キャンセル**一般に、モーダル ダイアログ ボックス、ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-221">A **Cancel** button, typically on a modal dialog box.</span></span>  
  
-   <span data-ttu-id="d3e7a-222">A**閉じる**一般に、モードレス ダイアログ ボックス、ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-222">A **Close** button, typically on a modeless dialog box.</span></span>  
  
 <span data-ttu-id="d3e7a-223">これらのカスタム メカニズムのいずれかへの応答でウィンドウを閉じるを呼び出す必要がある、<xref:System.Windows.Window.Close%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-223">To close a window in response to one of these custom mechanisms, you need to call the <xref:System.Windows.Window.Close%2A> method.</span></span> <span data-ttu-id="d3e7a-224">次の例を選択して、ウィンドウを閉じる機能を実装する、**終了**上、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-224">The following example implements the ability to close a window by choosing the **Exit** on the **File** menu.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 <span data-ttu-id="d3e7a-225">ウィンドウの終了時に 2 つのイベントを発生させます。<xref:System.Windows.Window.Closing>と<xref:System.Windows.Window.Closed>です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-225">When a window closes, it raises two events: <xref:System.Windows.Window.Closing> and <xref:System.Windows.Window.Closed>.</span></span>  
  
 <span data-ttu-id="d3e7a-226"><xref:System.Windows.Window.Closing>ウィンドウが閉じ、およびどのウィンドウによってクロージャを防止できますメカニズムを提供する前に発生します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-226"><xref:System.Windows.Window.Closing> is raised before the window closes, and it provides a mechanism by which window closure can be prevented.</span></span> <span data-ttu-id="d3e7a-227">ウィンドウが閉じるのを防ぐのは、一般的に、ウィンドウ コンテンツに変更したデータが含まれている場合です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-227">One common reason to prevent window closure is if window content contains modified data.</span></span> <span data-ttu-id="d3e7a-228">このような状況で、<xref:System.Windows.Window.Closing>イベントを処理する場合は、ユーザーにたずねる、ウィンドウを閉じると、データを保存しないで続行するか、またはウィンドウのクロージャをキャンセルするかどうか、およびデータがダーティかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-228">In this situation, the <xref:System.Windows.Window.Closing> event can be handled to determine whether data is dirty and, if so, to ask the user whether to either continue closing the window without saving the data or to cancel window closure.</span></span> <span data-ttu-id="d3e7a-229">次の例では、処理の重要な側面<xref:System.Windows.Window.Closing>です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-229">The following example shows the key aspects of handling <xref:System.Windows.Window.Closing>.</span></span>  
  
 [!code-csharp[WindowClosingSnippets](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  
 
  
 <span data-ttu-id="d3e7a-230"><xref:System.Windows.Window.Closing>渡されるイベント ハンドラー、<xref:System.ComponentModel.CancelEventArgs>を実装する、 `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>を設定できるプロパティ`true`ウィンドウが終了されないようにします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-230">The <xref:System.Windows.Window.Closing> event handler is passed a <xref:System.ComponentModel.CancelEventArgs>, which implements the `Boolean`<xref:System.ComponentModel.CancelEventArgs.Cancel%2A> property that you set to `true` to prevent a window from closing.</span></span>  
  
 <span data-ttu-id="d3e7a-231">場合<xref:System.Windows.Window.Closing>が処理されない、ウィンドウが閉じ、または処理しますが、取り消されないことができます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-231">If <xref:System.Windows.Window.Closing> is not handled, or it is handled but not canceled, the window will close.</span></span> <span data-ttu-id="d3e7a-232">ウィンドウが実際に閉じられる直前に<xref:System.Windows.Window.Closed>が発生します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-232">Just before a window actually closes, <xref:System.Windows.Window.Closed> is raised.</span></span> <span data-ttu-id="d3e7a-233">この時点で、ウィンドウが閉じるのを防ぐことはできません。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-233">At this point, a window cannot be prevented from closing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3e7a-234">アプリケーションは、自動的にアプリケーションのメイン ウィンドウが閉じたときにシャット ダウンするように構成できます (を参照してください<xref:System.Windows.Application.MainWindow%2A>) または最後のウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-234">An application can be configured to shut down automatically when either the main application window closes (see <xref:System.Windows.Application.MainWindow%2A>) or the last window closes.</span></span> <span data-ttu-id="d3e7a-235">詳細については、「<xref:System.Windows.Application.ShutdownMode%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-235">For details, see <xref:System.Windows.Application.ShutdownMode%2A>.</span></span>  
  
 <span data-ttu-id="d3e7a-236">ウィンドウは、非クライアント領域とクライアント領域で提供されるメカニズムを通じて明示的に閉じることができます、中にウィンドウ終了することも暗黙的に、アプリケーションの他の部分での動作の結果として、または[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]次を含みます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-236">While a window can be explicitly closed through mechanisms provided in the non-client and client areas, a window can also be implicitly closed as a result of behavior in other parts of the application or [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], including the following:</span></span>  
  
-   <span data-ttu-id="d3e7a-237">ユーザーがログオフまたはシャット ダウン[!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-237">A user logs off or shuts down [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)].</span></span>  
  
-   <span data-ttu-id="d3e7a-238">ウィンドウの所有者を閉じます (を参照してください<xref:System.Windows.Window.Owner%2A>)。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-238">A window's owner closes (see <xref:System.Windows.Window.Owner%2A>).</span></span>  
  
-   <span data-ttu-id="d3e7a-239">アプリケーションのメイン ウィンドウが閉じられると<xref:System.Windows.Application.ShutdownMode%2A>は<xref:System.Windows.ShutdownMode.OnMainWindowClose>します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-239">The main application window is closed and <xref:System.Windows.Application.ShutdownMode%2A> is <xref:System.Windows.ShutdownMode.OnMainWindowClose>.</span></span>  
  
-   <span data-ttu-id="d3e7a-240"><xref:System.Windows.Application.Shutdown%2A> が呼ばれたとき。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-240"><xref:System.Windows.Application.Shutdown%2A> is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3e7a-241">ウィンドウを閉じると、再度開くことはできません。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-241">A window cannot be reopened after it is closed.</span></span>  
  
<a name="Window_Lifetime_Events"></a>   
### <a name="window-lifetime-events"></a><span data-ttu-id="d3e7a-242">ウィンドウの有効期間イベント</span><span class="sxs-lookup"><span data-stu-id="d3e7a-242">Window Lifetime Events</span></span>  
 <span data-ttu-id="d3e7a-243">次の図は、ウィンドウの有効期間内における主要なイベントのシーケンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-243">The following illustration shows the sequence of the principal events in the lifetime of a window.</span></span>  
  
 <span data-ttu-id="d3e7a-244">![ウィンドウの有効期間](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")</span><span class="sxs-lookup"><span data-stu-id="d3e7a-244">![Window Lifetime](../../../../docs/framework/wpf/app-development/media/windowlifetimeevents.png "WindowLifetimeEvents")</span></span>  
  
 <span data-ttu-id="d3e7a-245">次の図は、ライセンス認証を行わずに表示されるウィンドウの有効期間の主要なイベントのシーケンスを示します (<xref:System.Windows.Window.ShowActivated%2A>に設定されている`false`ウィンドウが表示される前に)。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-245">The following illustration shows the sequence of the principal events in the lifetime of a window that is shown without activation (<xref:System.Windows.Window.ShowActivated%2A> is set to `false` before the window is shown).</span></span>  
  
 <span data-ttu-id="d3e7a-246">![ウィンドウの有効期間 &#40;Window.ShowActivated &#61; False&#41;](../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")</span><span class="sxs-lookup"><span data-stu-id="d3e7a-246">![Window Lifetime &#40;Window.ShowActivated &#61; False&#41;](../../../../docs/framework/wpf/app-development/media/windowlifetimenoact.png "WindowLifetimeNoAct")</span></span>  
  
<a name="WindowLocation"></a>   
## <a name="window-location"></a><span data-ttu-id="d3e7a-247">ウィンドウの位置</span><span class="sxs-lookup"><span data-stu-id="d3e7a-247">Window Location</span></span>  
 <span data-ttu-id="d3e7a-248">ウィンドウが開いているとき、ウィンドウはデスクトップに対して相対的な x ディメンションと y ディメンションの位置にあります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-248">While a window is open, it has a location in the x and y dimensions relative to the desktop.</span></span> <span data-ttu-id="d3e7a-249">この場所を調べることで決定できます、<xref:System.Windows.Window.Left%2A>と<xref:System.Windows.Window.Top%2A>プロパティ、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-249">This location can be determined by inspecting the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties, respectively.</span></span> <span data-ttu-id="d3e7a-250">これらのプロパティを設定して、ウィンドウの位置を変更できます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-250">You can set these properties to change the location of the window.</span></span>  
  
 <span data-ttu-id="d3e7a-251">最初の場所を指定することも、<xref:System.Windows.Window>ときに最初に表示される設定、 <xref:System.Windows.Window.WindowStartupLocation%2A> 、次のいずれかのプロパティ<xref:System.Windows.WindowStartupLocation>列挙値。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-251">You can also specify the initial location of a <xref:System.Windows.Window> when it first appears by setting the <xref:System.Windows.Window.WindowStartupLocation%2A> property with one of the following <xref:System.Windows.WindowStartupLocation> enumeration values:</span></span>  
  
-   <span data-ttu-id="d3e7a-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (既定値)</span><span class="sxs-lookup"><span data-stu-id="d3e7a-252"><xref:System.Windows.WindowStartupLocation.CenterOwner> (default)</span></span>  
  
-   <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
-   <xref:System.Windows.WindowStartupLocation.Manual>  
  
 <span data-ttu-id="d3e7a-253">として、起動の場所が指定されている場合<xref:System.Windows.WindowStartupLocation.Manual>、および<xref:System.Windows.Window.Left%2A>と<xref:System.Windows.Window.Top%2A>プロパティが設定されていない、<xref:System.Windows.Window>入力が求められます[!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)]に表示される場所です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-253">If the startup location is specified as <xref:System.Windows.WindowStartupLocation.Manual>, and the <xref:System.Windows.Window.Left%2A> and <xref:System.Windows.Window.Top%2A> properties have not been set, <xref:System.Windows.Window> will ask [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] for a location to appear in.</span></span>  
  
<a name="Topmost_Windows_and_Z_Order"></a>   
### <a name="topmost-windows-and-z-order"></a><span data-ttu-id="d3e7a-254">最上位ウィンドウと Z オーダー</span><span class="sxs-lookup"><span data-stu-id="d3e7a-254">Topmost Windows and Z-Order</span></span>  
 <span data-ttu-id="d3e7a-255">ウィンドウには、x 位置と y 位置に加えて、他のウィンドウを基準にして垂直位置を決定する z ディメンションの位置もあります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-255">Besides having an x and y location, a window also has a location in the z dimension, which determines its vertical position with respect to other windows.</span></span> <span data-ttu-id="d3e7a-256">これはウィンドウの z オーダーともいい、標準 z オーダーと最上位 z オーダーの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-256">This is known as the window's z-order, and there are two types: normal z-order and topmost z-order.</span></span> <span data-ttu-id="d3e7a-257">ウィンドウの場所、*標準 z オーダー*が現在アクティブかどうかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-257">The location of a window in the *normal z-order* is determined by whether it is currently active or not.</span></span> <span data-ttu-id="d3e7a-258">既定では、ウィンドウは標準 z オーダーにあります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-258">By default, a window is located in the normal z-order.</span></span> <span data-ttu-id="d3e7a-259">ウィンドウの場所、 *z オーダーの最上位*が現在アクティブかどうかどうかによっても決定されます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-259">The location of a window in the *topmost z-order* is also determined by whether it is currently active or not.</span></span> <span data-ttu-id="d3e7a-260">また、最上位 z オーダーにあるウィンドウは、常に、標準 z オーダーにあるウィンドウの上に位置します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-260">Furthermore, windows in the topmost z-order are always located above windows in the normal z-order.</span></span> <span data-ttu-id="d3e7a-261">ウィンドウ内にある最上位の z オーダーを設定してその<xref:System.Windows.Window.Topmost%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-261">A window is located in the topmost z-order by setting its <xref:System.Windows.Window.Topmost%2A> property to `true`.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup2)]  
  
 <span data-ttu-id="d3e7a-262">各 z オーダー内では、現在アクティブなウィンドウは、同じ z オーダーにある他のすべてのウィンドウの上に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-262">Within each z-order, the currently active window appears above all other windows in the same z-order.</span></span>  
  
<a name="WindowSize"></a>   
## <a name="window-size"></a><span data-ttu-id="d3e7a-263">ウィンドウ サイズ</span><span class="sxs-lookup"><span data-stu-id="d3e7a-263">Window Size</span></span>  
 <span data-ttu-id="d3e7a-264">デスクトップの場所を持つだけでなく、ウィンドウ サイズが使用されて、さまざまな幅と高さのプロパティを含む、いくつかのプロパティによって決定されると<xref:System.Windows.Window.SizeToContent%2A>です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-264">Besides having a desktop location, a window has a size that is determined by several properties, including the various width and height properties and <xref:System.Windows.Window.SizeToContent%2A>.</span></span>  
  
 <span data-ttu-id="d3e7a-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、および<xref:System.Windows.FrameworkElement.MaxWidth%2A>ウィンドウを選択して、その有効期間中にすることができますが、次の例で示すように構成されている幅の範囲の管理に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-265"><xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.MaxWidth%2A> are used to manage the range of widths that a window can have during its lifetime, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup2)]  
  
 <span data-ttu-id="d3e7a-266">ウィンドウの高さはによって管理<xref:System.Windows.FrameworkElement.MinHeight%2A>、 <xref:System.Windows.FrameworkElement.Height%2A>、および<xref:System.Windows.FrameworkElement.MaxHeight%2A>、し、次の例に示すように構成されます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-266">Window height is managed by <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and are configured as shown in the following example.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup2)]  
  
 <span data-ttu-id="d3e7a-267">さまざまな幅の値と高さの値はそれぞれ範囲を指定しているため、サイズを変更できるウィンドウの幅と高さは、それぞれの寸法に指定された範囲内のいずれかの値を取ります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-267">Because the various width values and height values each specify a range, it is possible for the width and height of a resizable window to be anywhere within the specified range for the respective dimension.</span></span> <span data-ttu-id="d3e7a-268">現在の幅と高さを検出するには、検査<xref:System.Windows.FrameworkElement.ActualWidth%2A>と<xref:System.Windows.FrameworkElement.ActualHeight%2A>、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-268">To detect its current width and height, inspect <xref:System.Windows.FrameworkElement.ActualWidth%2A> and <xref:System.Windows.FrameworkElement.ActualHeight%2A>, respectively.</span></span>  
  
 <span data-ttu-id="d3e7a-269">ウィンドウのサイズに合わせたサイズには、コンテンツの場合は、ウィンドウの高さと幅は、使用できます、<xref:System.Windows.Window.SizeToContent%2A>を次の値を持つプロパティ。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-269">If you'd like the width and height of your window to have a size that fits to the size of the window's content, you can use the <xref:System.Windows.Window.SizeToContent%2A> property, which has the following values:</span></span>  
  
-   <span data-ttu-id="d3e7a-270"><xref:System.Windows.SizeToContent.Manual>。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-270"><xref:System.Windows.SizeToContent.Manual>.</span></span> <span data-ttu-id="d3e7a-271">効果 (既定値)。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-271">No effect (default).</span></span>  
  
-   <span data-ttu-id="d3e7a-272"><xref:System.Windows.SizeToContent.Width>。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-272"><xref:System.Windows.SizeToContent.Width>.</span></span> <span data-ttu-id="d3e7a-273">両方の設定と同じ効果を持つコンテンツの幅に合わせる<xref:System.Windows.FrameworkElement.MinWidth%2A>と<xref:System.Windows.FrameworkElement.MaxWidth%2A>コンテンツの幅にします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-273">Fit to content width, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
-   <span data-ttu-id="d3e7a-274"><xref:System.Windows.SizeToContent.Height>。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-274"><xref:System.Windows.SizeToContent.Height>.</span></span> <span data-ttu-id="d3e7a-275">両方の設定と同じ効果を持つコンテンツの高さに合わせて<xref:System.Windows.FrameworkElement.MinHeight%2A>と<xref:System.Windows.FrameworkElement.MaxHeight%2A>コンテンツの高さにします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-275">Fit to content height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content.</span></span>  
  
-   <span data-ttu-id="d3e7a-276"><xref:System.Windows.SizeToContent.WidthAndHeight>。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-276"><xref:System.Windows.SizeToContent.WidthAndHeight>.</span></span> <span data-ttu-id="d3e7a-277">コンテンツの幅と高さで、両方を設定すると同じ効果<xref:System.Windows.FrameworkElement.MinHeight%2A>と<xref:System.Windows.FrameworkElement.MaxHeight%2A>、コンテンツと設定の両方の高さに<xref:System.Windows.FrameworkElement.MinWidth%2A>と<xref:System.Windows.FrameworkElement.MaxWidth%2A>コンテンツの幅にします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-277">Fit to content width and height, which has the same effect as setting both <xref:System.Windows.FrameworkElement.MinHeight%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> to the height of the content, and setting both <xref:System.Windows.FrameworkElement.MinWidth%2A> and <xref:System.Windows.FrameworkElement.MaxWidth%2A> to the width of the content.</span></span>  
  
 <span data-ttu-id="d3e7a-278">次の例では、ウィンドウを最初に表示するときに、そのコンテンツに合わせて垂直方向と水平方向の両方のサイズを自動的に変更するウィンドウを示しています。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-278">The following example shows a window that automatically sizes to fit its content, both vertically and horizontally, when first shown.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup2)]  
  
 <span data-ttu-id="d3e7a-279">次の例は、設定する方法を示します、<xref:System.Windows.Window.SizeToContent%2A>コンテンツに合わせてウィンドウのサイズを変更する方法を指定するコード内のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-279">The following example shows how to set the <xref:System.Windows.Window.SizeToContent%2A> property in code to specify how a window resizes to fit its content    .</span></span>
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>   
## <a name="order-of-precedence-for-sizing-properties"></a><span data-ttu-id="d3e7a-280">サイズ変更プロパティの優先順位</span><span class="sxs-lookup"><span data-stu-id="d3e7a-280">Order of Precedence for Sizing Properties</span></span>  
 <span data-ttu-id="d3e7a-281">基本的に、ウィンドウのさまざまなサイズのプロパティを組み合わせて、サイズを変更できるウィンドウの幅と高さの範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-281">Essentially, the various sizes properties of a window combine to define the range of width and height for a resizable window.</span></span> <span data-ttu-id="d3e7a-282">有効な範囲を維持すると、ように<xref:System.Windows.Window>優先順位の次の注文を使用して、サイズ プロパティの値を評価します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-282">To ensure a valid range is maintained, <xref:System.Windows.Window> evaluates the values of the size properties using the following orders of precedence.</span></span>  
  
 <span data-ttu-id="d3e7a-283">**高さのプロパティ:**</span><span class="sxs-lookup"><span data-stu-id="d3e7a-283">**For Height Properties:**</span></span>  
  
1.  <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="d3e7a-284">**幅のプロパティ:**</span><span class="sxs-lookup"><span data-stu-id="d3e7a-284">**For Width Properties:**</span></span>  
  
1.  <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType> >  
  
2.  <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType> >  
  
3.  <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType> >  
  
4.  <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="d3e7a-285">優先順位の順序も特定できます、ウィンドウのサイズが最大化で管理されているときに、<xref:System.Windows.Window.WindowState%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-285">The order of precedence can also determine the size of a window when it is maximized, which is managed with the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="WindowState"></a>   
## <a name="window-state"></a><span data-ttu-id="d3e7a-286">ウィンドウの状態</span><span class="sxs-lookup"><span data-stu-id="d3e7a-286">Window State</span></span>  
 <span data-ttu-id="d3e7a-287">サイズを変更できるウィンドウには、有効期間中、通常、最小化、最大化の 3 つの状態があります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-287">During the lifetime of a resizable window, it can have three states: normal, minimized, and maximized.</span></span> <span data-ttu-id="d3e7a-288">持つ、ウィンドウ、*通常*状態は、ウィンドウの既定の状態。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-288">A window with a *normal* state is the default state of a window.</span></span> <span data-ttu-id="d3e7a-289">この状態のウィンドウは、サイズ変更グリップ、またはサイズ変更可能な場合は境界線を使用して、ユーザーが移動したりサイズ変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-289">A window with this state allows a user to move and resize it by using a resize grip or the border, if it is resizable.</span></span>  
  
 <span data-ttu-id="d3e7a-290">含むウィンドウ、*最小限に抑える*場合、タスク バー ボタンの状態が折りたたまれます<xref:System.Windows.Window.ShowInTaskbar%2A>に設定されている`true`、それ以外の可能な最小サイズと設定できますが、デスクトップの左下隅に自動的に再配置することが折りたたまれます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-290">A window with a *minimized* state collapses to its task bar button if <xref:System.Windows.Window.ShowInTaskbar%2A> is set to `true`; otherwise, it collapses to the smallest possible size it can be and relocates itself to the bottom-left corner of the desktop.</span></span> <span data-ttu-id="d3e7a-291">最小化されたウィンドウはいずれの種類も、境界線またはサイズ変更グリップを使用してサイズ変更できません。ただし、タスク バーに表示されていない最小化されたウィンドウはデスクトップの任意の場所にドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-291">Neither type of minimized window can be resized using a border or resize grip, although a minimized window that isn't shown in the task bar can be dragged around the desktop.</span></span>  
  
 <span data-ttu-id="d3e7a-292">含むウィンドウ、*を最大表示*状態は、最大のサイズにできる限り大きくなりますが展開され、 <xref:System.Windows.FrameworkElement.MaxWidth%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>と<xref:System.Windows.Window.SizeToContent%2A>プロパティ ディクテーションします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-292">A window with a *maximized* state expands to the maximum size it can be, which will only be as large as its <xref:System.Windows.FrameworkElement.MaxWidth%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.Window.SizeToContent%2A> properties dictate.</span></span> <span data-ttu-id="d3e7a-293">最小化されたウィンドウと同様、最大化されたウィンドウは、サイズ変更グリップを使用したり、境界線をドラッグしたりすることによってサイズ変更できません。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-293">Like a minimized window, a maximized window cannot be resized by using a resize grip or by dragging the border.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3e7a-294">値、 <xref:System.Windows.Window.Top%2A>、 <xref:System.Windows.Window.Left%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、および<xref:System.Windows.FrameworkElement.Height%2A>ウィンドウのプロパティは、ウィンドウが現在最大化または最小限に抑える場合でも常に通常の状態の値を表します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-294">The values of the <xref:System.Windows.Window.Top%2A>, <xref:System.Windows.Window.Left%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, and <xref:System.Windows.FrameworkElement.Height%2A> properties of a window always represent the values for the normal state, even when the window is currently maximized or minimized.</span></span>  
  
 <span data-ttu-id="d3e7a-295">ウィンドウの状態を設定して構成できますその<xref:System.Windows.Window.WindowState%2A>プロパティで、次のいずれかの<xref:System.Windows.WindowState>列挙値。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-295">The state of a window can be configured by setting its <xref:System.Windows.Window.WindowState%2A> property, which can have one of the following <xref:System.Windows.WindowState> enumeration values:</span></span>  
  
-   <span data-ttu-id="d3e7a-296"><xref:System.Windows.WindowState.Normal> (既定値)</span><span class="sxs-lookup"><span data-stu-id="d3e7a-296"><xref:System.Windows.WindowState.Normal> (default)</span></span>  
  
-   <xref:System.Windows.WindowState.Maximized>  
  
-   <xref:System.Windows.WindowState.Minimized>  
  
 <span data-ttu-id="d3e7a-297">開くときに最大化されて表示されるウィンドウを作成する方法を、次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-297">The following example shows how to create a window that is shown as maximized when it opens.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup2)]  
  
 <span data-ttu-id="d3e7a-298">一般に、設定する必要があります<xref:System.Windows.Window.WindowState%2A>ウィンドウの初期状態を構成します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-298">In general, you should set <xref:System.Windows.Window.WindowState%2A> to configure the initial state of a window.</span></span> <span data-ttu-id="d3e7a-299">サイズ変更可能なウィンドウが表示されると、ユーザーはウィンドウのタイトル バーにある最小化ボタン、最大化ボタン、および元に戻すボタンを使用して、ウィンドウの状態を変更できます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-299">Once a resizable window is shown, users can press the minimize, maximize, and restore buttons on the window's title bar to change the window state.</span></span>  
  
<a name="WindowAppearance"></a>   
## <a name="window-appearance"></a><span data-ttu-id="d3e7a-300">ウィンドウの外観</span><span class="sxs-lookup"><span data-stu-id="d3e7a-300">Window Appearance</span></span>  
 <span data-ttu-id="d3e7a-301">ウィンドウのクライアント領域の外観を変更するために、ボタン、ラベル、テキスト ボックスなど、ウィンドウ固有のコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-301">You change the appearance of the client area of a window by adding window-specific content to it, such as buttons, labels, and text boxes.</span></span> <span data-ttu-id="d3e7a-302">非クライアント領域を構成する<xref:System.Windows.Window>など、いくつかのプロパティを提供<xref:System.Windows.Window.Icon%2A>ウィンドウのアイコンを設定して<xref:System.Windows.Window.Title%2A>そのタイトルを設定します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-302">To configure the non-client area, <xref:System.Windows.Window> provides several properties, which include <xref:System.Windows.Window.Icon%2A> to set a window's icon and <xref:System.Windows.Window.Title%2A> to set its title.</span></span>  
  
 <span data-ttu-id="d3e7a-303">また、ウィンドウのサイズ変更モード、ウィンドウ スタイル、デスクトップのタスク バーにボタンとして表示するかどうかを構成して、非クライアント領域の境界線の外観と動作も変更できます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-303">You can also change the appearance and behavior of non-client area border by configuring a window's resize mode, window style, and whether it appears as a button in the desktop task bar.</span></span>  
  
  
<a name="Resize_Mode"></a>   
### <a name="resize-mode"></a><span data-ttu-id="d3e7a-304">サイズ変更モード</span><span class="sxs-lookup"><span data-stu-id="d3e7a-304">Resize Mode</span></span>  
 <span data-ttu-id="d3e7a-305">によって、<xref:System.Windows.Window.WindowStyle%2A>プロパティを制御できる方法 (および場合) ユーザーがウィンドウのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-305">Depending on the <xref:System.Windows.Window.WindowStyle%2A> property, you can control how (and if) users can resize the window.</span></span> <span data-ttu-id="d3e7a-306">ウィンドウ スタイルの選択に影響を与えるかどうかにマウスを使用して境界線をドラッグして、ユーザーが、ウィンドウのサイズかどうか、**最小化**、**最大化**、および**サイズを変更する**ボタン非クライアント領域に表示されると、表示される場合は、有効にするかどうか。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-306">The choice of window style affects whether a user can resize the window by dragging its border with the mouse, whether the **Minimize**, **Maximize**, and **Resize** buttons appear on the non-client area, and, if they do appear, whether they are enabled.</span></span>  
  
 <span data-ttu-id="d3e7a-307">どのウィンドウ サイズを変更する設定を構成することができます、<xref:System.Windows.Window.ResizeMode%2A>プロパティで、次のいずれかの<xref:System.Windows.ResizeMode>列挙値。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-307">You can configure how a window resizes by setting its <xref:System.Windows.Window.ResizeMode%2A> property, which can be one of the following <xref:System.Windows.ResizeMode> enumeration values:</span></span>  
  
-   <xref:System.Windows.ResizeMode.NoResize>  
  
-   <xref:System.Windows.ResizeMode.CanMinimize>  
  
-   <span data-ttu-id="d3e7a-308"><xref:System.Windows.ResizeMode.CanResize> (既定値)</span><span class="sxs-lookup"><span data-stu-id="d3e7a-308"><xref:System.Windows.ResizeMode.CanResize> (default)</span></span>  
  
-   <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 <span data-ttu-id="d3e7a-309">同様に<xref:System.Windows.Window.WindowStyle%2A>、ウィンドウのサイズ変更モードを設定することがほとんどの場合から、その有効期間中に変更される可能性は[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-309">As with <xref:System.Windows.Window.WindowStyle%2A>, the resize mode of a window is unlikely to change during its lifetime, which means that you'll most likely set it from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup2)]  
  
 <span data-ttu-id="d3e7a-310">ウィンドウが最大化されているかどうかを検出することが最小化、またはを調べることによって復元、<xref:System.Windows.Window.WindowState%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-310">Note that you can detect whether a window is maximized, minimized, or restored by inspecting the <xref:System.Windows.Window.WindowState%2A> property.</span></span>  
  
<a name="Window_Style"></a>   
### <a name="window-style"></a><span data-ttu-id="d3e7a-311">ウィンドウ スタイル</span><span class="sxs-lookup"><span data-stu-id="d3e7a-311">Window Style</span></span>  
 <span data-ttu-id="d3e7a-312">ウィンドウの非クライアント領域から公開される境界線は、多くのアプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-312">The border that is exposed from the non-client area of a window is suitable for most applications.</span></span> <span data-ttu-id="d3e7a-313">ただし、ウィンドウの種類によって、異なる種類の境界線が必要な状況や、境界線がまったく必要ない状況があります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-313">However, there are circumstances where different types of borders are needed, or no borders are needed at all, depending on the type of window.</span></span>  
  
 <span data-ttu-id="d3e7a-314">ウィンドウの境界線の種類を制御する取得、設定したその<xref:System.Windows.Window.WindowStyle%2A>プロパティの値は次のいずれかで、<xref:System.Windows.WindowStyle>列挙。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-314">To control what type of border a window gets, you set its <xref:System.Windows.Window.WindowStyle%2A> property with one of the following values of the <xref:System.Windows.WindowStyle> enumeration:</span></span>  
  
-   <xref:System.Windows.WindowStyle.None>  
  
-   <span data-ttu-id="d3e7a-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (既定値)</span><span class="sxs-lookup"><span data-stu-id="d3e7a-315"><xref:System.Windows.WindowStyle.SingleBorderWindow> (default)</span></span>  
  
-   <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
-   <xref:System.Windows.WindowStyle.ToolWindow>  
  
 <span data-ttu-id="d3e7a-316">これらのウィンドウ スタイルの効果については、次の図で説明します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-316">The effect of these window styles are illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="d3e7a-317">![ウィンドウ スタイル](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.PNG "WindowOverviewFigure6")</span><span class="sxs-lookup"><span data-stu-id="d3e7a-317">![Window styles](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure6.PNG "WindowOverviewFigure6")</span></span>  
  
 <span data-ttu-id="d3e7a-318">設定することができます<xref:System.Windows.Window.WindowStyle%2A>いずれかを使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップやコードです。 そうでないウィンドウの有効期間中に変更される可能性があるため、ほとんどの場合を構成するを使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-318">You can set <xref:System.Windows.Window.WindowStyle%2A> using either [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup or code; because it is unlikely to change during the lifetime of a window, you will most likely configure it using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup2)]  
  
#### <a name="non-rectangular-window-style"></a><span data-ttu-id="d3e7a-319">四角形以外のウィンドウ スタイル</span><span class="sxs-lookup"><span data-stu-id="d3e7a-319">Non-Rectangular Window Style</span></span>  
 <span data-ttu-id="d3e7a-320">ここで、罫線のスタイルを状況もあります<xref:System.Windows.Window.WindowStyle%2A>によりが不十分です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-320">There are also situations where the border styles that <xref:System.Windows.Window.WindowStyle%2A> allows you to have are not sufficient.</span></span> <span data-ttu-id="d3e7a-321">同様に四角形以外の境界線を持つアプリケーションを作成したいなど[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-321">For example, you may want to create an application with a non-rectangular border, like [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] uses.</span></span>  
  
 <span data-ttu-id="d3e7a-322">たとえば、次の図に示す吹き出しウィンドウを想定します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-322">For example, consider the speech bubble window shown in the following figure.</span></span>  
  
 <span data-ttu-id="d3e7a-323">![四角形以外のウィンドウ](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")</span><span class="sxs-lookup"><span data-stu-id="d3e7a-323">![Nonrectangular window](../../../../docs/framework/wpf/app-development/media/nonrectangularwindowfigure.PNG "NonRectangularWindowFigure")</span></span>  
  
 <span data-ttu-id="d3e7a-324">設定してこの種類のウィンドウを作成することができます、<xref:System.Windows.Window.WindowStyle%2A>プロパティを<xref:System.Windows.WindowStyle.None>、および特殊なを使用してサポートを<xref:System.Windows.Window>透過性がします。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-324">This type of window can be created by setting the <xref:System.Windows.Window.WindowStyle%2A> property to <xref:System.Windows.WindowStyle.None>, and by using special support that <xref:System.Windows.Window> has for transparency.</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup2)]  
  
 <span data-ttu-id="d3e7a-325">値をこの組み合わせで使用し、ウィンドウが完全に透明にレンダリングされるように設定します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-325">This combination of values instructs the window to render completely transparent.</span></span> <span data-ttu-id="d3e7a-326">この状態では、ウィンドウの非クライアント領域の表示要素 (閉じるメニュー、最小化ボタン、最大化ボタン、元に戻すボタンなど) は使用できません。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-326">In this state, the window's non-client area adornments (the Close menu, Minimize, Maximize, and Restore buttons, and so on) cannot be used.</span></span> <span data-ttu-id="d3e7a-327">したがって、独自の表示要素を用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-327">Consequently, you need to provide your own.</span></span>  
  
<a name="Task_Bar_Presence"></a>   
### <a name="task-bar-presence"></a><span data-ttu-id="d3e7a-328">タスク バーのプレゼンス</span><span class="sxs-lookup"><span data-stu-id="d3e7a-328">Task Bar Presence</span></span>  
 <span data-ttu-id="d3e7a-329">ウィンドウの既定の外観には、次の図に示すような、タスク バー ボタンも含まれます。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-329">The default appearance of a window includes a task bar button, like the one shown in the following figure.</span></span>  
  
 <span data-ttu-id="d3e7a-330">![タスク バー ボタンがあるウィンドウ](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.PNG "WindowOverviewFigure7")</span><span class="sxs-lookup"><span data-stu-id="d3e7a-330">![Window with a task bar button](../../../../docs/framework/wpf/app-development/media/windowoverviewfigure7.PNG "WindowOverviewFigure7")</span></span>  
  
 <span data-ttu-id="d3e7a-331">Windows の種類によってはメッセージ ボックスおよびダイアログ ボックスなどのタスク バー ボタンがない (を参照してください[ダイアログ ボックスの概要](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-331">Some types of windows don't have a task bar button, such as message boxes and dialog boxes (see [Dialog Boxes Overview](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)).</span></span> <span data-ttu-id="d3e7a-332">設定して、ウィンドウのタスク バー ボタンが表示されるかどうかを制御することができます、<xref:System.Windows.Window.ShowInTaskbar%2A>プロパティ (`true`既定)。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-332">You can control whether the task bar button for a window is shown by setting the <xref:System.Windows.Window.ShowInTaskbar%2A> property (`true` by default).</span></span>  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
[!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup2)]  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations"></a><span data-ttu-id="d3e7a-333">セキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="d3e7a-333">Security Considerations</span></span>  
 <span data-ttu-id="d3e7a-334"><xref:System.Windows.Window>必要があります`UnmanagedCode`インスタンス化するセキュリティのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-334"><xref:System.Windows.Window> requires `UnmanagedCode` security permission to be instantiated.</span></span> <span data-ttu-id="d3e7a-335">ローカル コンピューターにインストールされ、ローカル コンピューターから起動されるアプリケーションの場合は、アプリケーションに付与されるアクセス許可セットの範囲内になります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-335">For applications installed on and launched from the local machine, this falls within the set of permissions that are granted to the application.</span></span>  
  
 <span data-ttu-id="d3e7a-336">ただし、これは、インターネットまたはローカル イントラネット ゾーンを使用してから起動されるアプリケーションに付与された権限のセットの範囲外[!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-336">However, this falls outside the set of permissions granted to applications that are launched from the Internet or Local intranet zone using [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)].</span></span> <span data-ttu-id="d3e7a-337">その結果、ユーザーが表示されます、[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]セキュリティの警告を完全な信頼アプリケーションの権限セットを昇格する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-337">Consequently, users will receive a [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] security warning and will need to elevate the permission set for the application to full trust.</span></span>  
  
 <span data-ttu-id="d3e7a-338">さらに、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]既定でウィンドウまたはダイアログ ボックスを表示することはできません。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-338">Additionally, [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] cannot show windows or dialog boxes by default.</span></span> <span data-ttu-id="d3e7a-339">スタンドアロン アプリケーションのセキュリティに関する考慮事項の詳細については、次を参照してください。 [WPF のセキュリティ方針 - プラットフォーム セキュリティ](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-339">For a discussion on standalone application security considerations, see [WPF Security Strategy - Platform Security](../../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).</span></span>  
  
<a name="Other_Types_of_Windows"></a>   
## <a name="other-types-of-windows"></a><span data-ttu-id="d3e7a-340">その他の種類のウィンドウ</span><span class="sxs-lookup"><span data-stu-id="d3e7a-340">Other Types of Windows</span></span>  
 <span data-ttu-id="d3e7a-341"><xref:System.Windows.Navigation.NavigationWindow>ナビゲート可能なコンテンツをホストするように設計されたウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-341"><xref:System.Windows.Navigation.NavigationWindow> is a window that is designed to host navigable content.</span></span> <span data-ttu-id="d3e7a-342">詳細については、次を参照してください。[ナビゲーション概要](../../../../docs/framework/wpf/app-development/navigation-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-342">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md)).</span></span>  
  
 <span data-ttu-id="d3e7a-343">ダイアログ ボックスは、ユーザーから情報を収集して機能を完了するためによく使用されるウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-343">Dialog boxes are windows that are often used to gather information from a user to complete a function.</span></span> <span data-ttu-id="d3e7a-344">たとえば、ユーザーがするときにファイルを開き、**ファイルを開く** ダイアログ ボックスは通常、ユーザーからファイル名を取得するアプリケーションで表示します。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-344">For example, when a user wants to open a file, the **Open File** dialog box is usually displayed by an application to get the file name from the user.</span></span> <span data-ttu-id="d3e7a-345">詳細については、「[ダイアログ ボックスの概要](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3e7a-345">For more information, see [Dialog Boxes Overview](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e7a-346">参照</span><span class="sxs-lookup"><span data-stu-id="d3e7a-346">See Also</span></span>  
 <xref:System.Windows.Window>  
 <xref:System.Windows.MessageBox>  
 <xref:System.Windows.Navigation.NavigationWindow>  
 <xref:System.Windows.Application>  
 [<span data-ttu-id="d3e7a-347">ダイアログ ボックスの概要</span><span class="sxs-lookup"><span data-stu-id="d3e7a-347">Dialog Boxes Overview</span></span>](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)  
 [<span data-ttu-id="d3e7a-348">WPF アプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="d3e7a-348">Building a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
