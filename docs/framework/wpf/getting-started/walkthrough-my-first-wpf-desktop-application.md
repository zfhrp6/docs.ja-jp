---
title: "チュートリアル: 最初 WPF デスクトップ アプリケーション"
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
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9818231a68f5c2ac2a6852f27e4876baa9728e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="6bb39-102">チュートリアル: 最初 WPF デスクトップ アプリケーション</span><span class="sxs-lookup"><span data-stu-id="6bb39-102">Walkthrough: My first WPF desktop application</span></span>
<span data-ttu-id="6bb39-103">このチュートリアルでは、開発の概要については、[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]多くに共通要素を含むアプリケーション[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーション:[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]マークアップ、分離コード、アプリケーション定義、コントロール、レイアウト、データ バインディング、およびスタイル。</span><span class="sxs-lookup"><span data-stu-id="6bb39-103">This walkthrough provides an introduction to the development of a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application that includes the elements that are common to most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> 
  
 <span data-ttu-id="6bb39-104">このチュートリアルで説明する、簡単な開発[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションは、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-104">This walkthrough guides you through the development of a simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application using the following steps.</span></span> 
  
-   <span data-ttu-id="6bb39-105">定義する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、アプリケーションの外観をデザインする[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-105">Defining [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to design the appearance of the application's [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="6bb39-106">アプリケーションの動作を構築するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-106">Writing code to build the application's behavior.</span></span> 
  
-   <span data-ttu-id="6bb39-107">アプリケーションを管理するためのアプリケーション定義を作成します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-107">Creating an application definition to manage the application.</span></span> 
  
-   <span data-ttu-id="6bb39-108">コントロールを追加して、アプリケーションを作成するレイアウトを作成する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-108">Adding controls and creating the layout to compose the application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="6bb39-109">アプリケーションの全体で一貫した外観を作成するスタイルを作成する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-109">Creating styles to create a consistent appearance throughout an application's [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="6bb39-110">バインディング、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]両方にデータを設定、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]データとデータを維持するからと[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]同期します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-110">Binding the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to data to both populate the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] from data and keep the data and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronized.</span></span> 
  
 <span data-ttu-id="6bb39-111">スタンドアロンのチュートリアルの目的は、構築した[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]アプリケーションを選択したユーザーの経費報告書を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-111">By the end of the walkthrough, you will have built a standalone [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="6bb39-112">アプリケーションは、いくつかの構成は[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ブラウザー スタイルのウィンドウでホストされているページ。</span><span class="sxs-lookup"><span data-stu-id="6bb39-112">The application will be composed of several [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pages that are hosted in a browser-style window.</span></span> 
  
 <span data-ttu-id="6bb39-113">このチュートリアルの構築に使用するサンプル コードは両方の使用可能な[!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]と[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]で[Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-113">The sample code that is used to build this walkthrough is available for both [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] and [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] at  [Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008).</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="6bb39-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6bb39-114">Prerequisites</span></span>  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="6bb39-115"> 以降</span><span class="sxs-lookup"><span data-stu-id="6bb39-115"> or later</span></span>

<span data-ttu-id="6bb39-116">Visual Studio の最新バージョンのインストールに関する詳細については、次を参照してください。 [Visual Studio インストール](/visualstudio/install/install-visual-studio)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>
  
## <a name="creating-the-application-project"></a><span data-ttu-id="6bb39-117">アプリケーション プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="6bb39-117">Creating the application project</span></span>  
 <span data-ttu-id="6bb39-118">このセクションでは、アプリケーション定義、2 つのページ、および 1 つのイメージが含まれる、アプリケーション インフラストラクチャを作成します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-118">In this section, you create the application infrastructure, which includes an application definition, two pages, and an image.</span></span> 
  
1. <span data-ttu-id="6bb39-119">Visual Basic または Visual c# のという名前の新しい WPF アプリケーション プロジェクトを作成する`ExpenseIt`です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-119">Create a new WPF Application project in Visual Basic or Visual C# named `ExpenseIt`.</span></span> <span data-ttu-id="6bb39-120">詳細については、次を参照してください。[する方法: 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-120">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="6bb39-121">このチュートリアルでは、 <xref:System.Windows.Controls.DataGrid> .NET Framework 4 で使用可能なコントロールです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-121">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4.</span></span> <span data-ttu-id="6bb39-122">プロジェクトの対象 .NET Framework 4 であることを確認して以降であります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-122">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="6bb39-123">詳細については、次を参照してください。[する方法: .NET Framework のバージョンを対象に](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-123">For more information, see[How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
2. <span data-ttu-id="6bb39-124">Application.xaml (Visual Basic) または App.xaml (C#) を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-124">Open Application.xaml (Visual Basic) or App.xaml (C#).</span></span> 
  
     <span data-ttu-id="6bb39-125">これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルを定義、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションとアプリケーション リソース。</span><span class="sxs-lookup"><span data-stu-id="6bb39-125">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file defines a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application and any application resources.</span></span> <span data-ttu-id="6bb39-126">使用することもこのファイルを指定する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]表示は、アプリケーションの起動時に自動的にこの場合、MainWindow.xaml です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-126">You also use this file to specify the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that automatically shows when the application starts; in this case, MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="6bb39-127">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic では次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-127">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     <span data-ttu-id="6bb39-128">C# では、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-128">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. <span data-ttu-id="6bb39-129">MainWindow.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-129">Open MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="6bb39-130">これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルは、アプリケーションのメイン ウィンドウと、ページで作成されたコンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-130">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="6bb39-131"><xref:System.Windows.Window>クラスなど、そのタイトル、サイズ、または、アイコン、ウィンドウのプロパティを定義し、閉じるか、非表示にするなどのイベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-131">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span> 
  
4. <span data-ttu-id="6bb39-132">変更、<xref:System.Windows.Window>要素を<xref:System.Windows.Navigation.NavigationWindow>です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-132">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="6bb39-133">このアプリケーションでは、ユーザー操作に応じて画面がさまざまなコンテンツに移動します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-133">This application will navigate to different content depending on the user interaction.</span></span> <span data-ttu-id="6bb39-134">そのため、メイン<xref:System.Windows.Window>に変更する必要があります、<xref:System.Windows.Navigation.NavigationWindow>です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-134">Therefore, the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="6bb39-135"><xref:System.Windows.Navigation.NavigationWindow>すべてのプロパティを継承<xref:System.Windows.Window>です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-135"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="6bb39-136"><xref:System.Windows.Navigation.NavigationWindow> XAML ファイル内の要素のインスタンスを作成する、<xref:System.Windows.Navigation.NavigationWindow>クラスです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-136">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="6bb39-137">詳細については、「[ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bb39-137">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span> 
  
5. <span data-ttu-id="6bb39-138">次のプロパティを変更、<xref:System.Windows.Navigation.NavigationWindow>要素。</span><span class="sxs-lookup"><span data-stu-id="6bb39-138">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>  
  
    -   <span data-ttu-id="6bb39-139">設定、<xref:System.Windows.Window.Title%2A>プロパティを"ExpenseIt"です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-139">Set the <xref:System.Windows.Window.Title%2A> property to "ExpenseIt".</span></span> 
  
    -   <span data-ttu-id="6bb39-140">設定、<xref:System.Windows.FrameworkElement.Width%2A>プロパティを 500 ピクセルです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-140">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span> 
  
    -   <span data-ttu-id="6bb39-141">設定、 <xref:System.Windows.FrameworkElement.Height%2A> 350 ピクセル プロパティです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-141">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span> 
  
    -   <span data-ttu-id="6bb39-142">削除、<xref:System.Windows.Controls.Grid>の間に要素、<xref:System.Windows.Navigation.NavigationWindow>タグ。</span><span class="sxs-lookup"><span data-stu-id="6bb39-142">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span> 
  
     <span data-ttu-id="6bb39-143">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic では次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-143">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     <span data-ttu-id="6bb39-144">C# では、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-144">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. <span data-ttu-id="6bb39-145">MainWindow.xaml.vb または MainWindow.xaml.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-145">Open MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span> 
  
     <span data-ttu-id="6bb39-146">このファイルは、MainWindow.xaml で宣言されたイベントを処理するコードを含んだ、分離コード ファイルです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-146">This file is a code-behind file that contains code to handle the events declared in MainWindow.xaml.</span></span> <span data-ttu-id="6bb39-147">このファイルには、XAML で定義されたウィンドウの部分クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6bb39-147">This file contains a partial class for the window defined in XAML.</span></span> 
  
7. <span data-ttu-id="6bb39-148">C# を使用している場合は、変更、`MainWindow`から派生するクラス<xref:System.Windows.Navigation.NavigationWindow>です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-148">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="6bb39-149">Visual Basic では、XAML でウィンドウを変更すると自動的にこの処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-149">In Visual Basic, this happens automatically when you change the window in XAML.</span></span> 
  
     <span data-ttu-id="6bb39-150">コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-150">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a><span data-ttu-id="6bb39-151">ファイルをアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-151">Adding files to the application</span></span>  
 <span data-ttu-id="6bb39-152">このセクションでは、アプリケーションに 2 つのページと 1 つのイメージを追加します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-152">In this section, you add two pages and an image to the application.</span></span> 
  
1. <span data-ttu-id="6bb39-153">という名前のプロジェクトに新しいページ (WPF) を追加`ExpenseItHome.xaml`です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-153">Add a new Page (WPF) to the project named `ExpenseItHome.xaml`.</span></span> <span data-ttu-id="6bb39-154">詳細については、次を参照してください。[する方法: WPF プロジェクトに新しい項目の追加](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-154">For more information, see [How to: Add New Items to a WPF Project](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span></span> 
  
     <span data-ttu-id="6bb39-155">このページが、アプリケーションの起動時に表示される最初のページになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-155">This page is the first page that is displayed when the application is launched.</span></span> <span data-ttu-id="6bb39-156">ここに個人の一覧が表示され、ユーザーは経費報告書の表示対象となる個人を選択できます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-156">It will show a list of people from which a user can select a person to show an expense report for.</span></span> 
  
2. <span data-ttu-id="6bb39-157">ExpenseItHome.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-157">Open ExpenseItHome.xaml.</span></span> 
  
3. <span data-ttu-id="6bb39-158">設定、 <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - ホーム"にします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-158">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - Home".</span></span> 
  
     <span data-ttu-id="6bb39-159">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic では次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-159">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     <span data-ttu-id="6bb39-160">C# では、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-160">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. <span data-ttu-id="6bb39-161">MainWindow.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-161">Open MainWindow.xaml.</span></span> 
  
5. <span data-ttu-id="6bb39-162">設定、<xref:System.Windows.Navigation.NavigationWindow.Source%2A>プロパティを<xref:System.Windows.Navigation.NavigationWindow>"ExpenseItHome.xaml"にします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-162">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "ExpenseItHome.xaml".</span></span> 
  
     <span data-ttu-id="6bb39-163">これにより、ExpenseItHome.xaml が、アプリケーションの起動時に最初に開くページになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-163">This sets ExpenseItHome.xaml to be the first page opened when the application starts.</span></span> <span data-ttu-id="6bb39-164">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic では次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-164">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     <span data-ttu-id="6bb39-165">C# では、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-165">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. <span data-ttu-id="6bb39-166">という名前のプロジェクトに新しいページ (WPF) を追加`ExpenseReportPage.xaml`です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-166">Add a new Page (WPF) to the project named `ExpenseReportPage.xaml`.</span></span> 
  
     <span data-ttu-id="6bb39-167">このページには、ExpenseItHome.xaml で選択されたユーザーの経費明細書が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-167">This page will show the expense report for the person that is selected on ExpenseItHome.xaml.</span></span> 
  
7. <span data-ttu-id="6bb39-168">ExpenseReportPage.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-168">Open ExpenseReportPage.xaml.</span></span> 
  
8. <span data-ttu-id="6bb39-169">設定、 <xref:System.Windows.Controls.Page.Title%2A> "ExpenseIt - 経費の表示"にします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-169">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - View Expense".</span></span> 
  
     <span data-ttu-id="6bb39-170">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Visual Basic では次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-170">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     <span data-ttu-id="6bb39-171">C# では、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-171">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. <span data-ttu-id="6bb39-172">ExpenseItHome.xaml.vb と ExpenseReportPage.xaml.vb を開くか、または ExpenseItHome.xaml.cs と ExpenseReportPage.xaml.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-172">Open ExpenseItHome.xaml.vb and ExpenseReportPage.xaml.vb, or ExpenseItHome.xaml.cs and ExpenseReportPage.xaml.cs.</span></span> 
  
     <span data-ttu-id="6bb39-173">新しいページ ファイルを作成すると、Visual Studio によって分離コード ファイルが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-173">When you create a new Page file, Visual Studio automatically creates a code behind file.</span></span> <span data-ttu-id="6bb39-174">これらの分離コード ファイルでは、ユーザー入力に対応するためのロジックを処理します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-174">These code-behind files handle the logic for responding to user input.</span></span> 
  
     <span data-ttu-id="6bb39-175">コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-175">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. <span data-ttu-id="6bb39-176">watermark.png という名前のイメージをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-176">Add an image named watermark.png to the project.</span></span> <span data-ttu-id="6bb39-177">独自のイメージを作成することも、サンプル コードからファイルをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-177">You can either create your own image, or copy the file from the sample code.</span></span> <span data-ttu-id="6bb39-178">詳細については、次を参照してください。 [NIB: 方法: 既存の項目をプロジェクトに追加](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-178">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span> 

## <a name="building-and-running-the-application"></a><span data-ttu-id="6bb39-179">ビルドおよびアプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="6bb39-179">Building and running the application</span></span>  
 <span data-ttu-id="6bb39-180">このセクションでは、アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-180">In this section, you build and run the application.</span></span> 
  
1. <span data-ttu-id="6bb39-181">ビルドおよびキーを押して、f5 キーまたは選択して、アプリケーションを実行する**デバッグの開始**から、**デバッグ**メニュー。</span><span class="sxs-lookup"><span data-stu-id="6bb39-181">Build and run the application by pressing F5 or select **Start Debugging** from the **Debug** menu.</span></span> 
  
     <span data-ttu-id="6bb39-182">次の図は、アプリケーションに、<xref:System.Windows.Navigation.NavigationWindow>ボタン。</span><span class="sxs-lookup"><span data-stu-id="6bb39-182">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons.</span></span> 
  
     <span data-ttu-id="6bb39-183">![ExpenseIt のサンプルのスクリーン ショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span><span class="sxs-lookup"><span data-stu-id="6bb39-183">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span></span>  
  
2. <span data-ttu-id="6bb39-184">戻るには、アプリケーションを閉じて[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-184">Close the application to return to [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span> 
  
## <a name="creating-the-layout"></a><span data-ttu-id="6bb39-185">レイアウトの作成</span><span class="sxs-lookup"><span data-stu-id="6bb39-185">Creating the layout</span></span>  
 <span data-ttu-id="6bb39-186">レイアウトが順序付けられたを配置する方法を提供[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素、およびそれらの要素の位置とサイズをまた管理ときに、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-186">Layout provides an ordered way to place [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements, and also manages the size and position of those elements when a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is resized.</span></span> <span data-ttu-id="6bb39-187">通常、レイアウトを作成するには、次のいずれかのレイアウト コントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-187">You typically create a layout with one of the following layout controls:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="6bb39-188">これらの各レイアウト コントロールは、その子要素に対する特別な種類のレイアウトをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6bb39-188">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="6bb39-189">ExpenseIt のページはサイズの変更が可能で、各ページの要素は縦にも横にも他の要素と揃えられます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-189">ExpenseIt pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="6bb39-190">その結果、<xref:System.Windows.Controls.Grid>アプリケーションに最適なレイアウト要素です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-190">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="6bb39-191">詳細については<xref:System.Windows.Controls.Panel>要素を参照してください[パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-191">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="6bb39-192">レイアウトの詳細については、次を参照してください。[レイアウト](../../../../docs/framework/wpf/advanced/layout.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-192">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span> 
  
 <span data-ttu-id="6bb39-193">セクションで、テーブルを作成する、単一列 3 つの行と 10 ピクセルの余白を含む列と行の定義を追加することによって、 <xref:System.Windows.Controls.Grid> ExpenseItHome.xaml にします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-193">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in ExpenseItHome.xaml.</span></span> 
  
1. <span data-ttu-id="6bb39-194">ExpenseItHome.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-194">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="6bb39-195">設定、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティを<xref:System.Windows.Controls.Grid>「10,0,10,10」左、上、右および下余白に対応する要素。</span><span class="sxs-lookup"><span data-stu-id="6bb39-195">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10" which corresponds to left, top, right and bottom margins.</span></span> 
  
3. <span data-ttu-id="6bb39-196">次の追加[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]間、<xref:System.Windows.Controls.Grid>行と列の定義を作成するタグです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-196">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions.</span></span> 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <span data-ttu-id="6bb39-197"><xref:System.Windows.Controls.RowDefinition.Height%2A> 2 つの行に設定されている<xref:System.Windows.GridLength.Auto%2A>行の内容は、基に、行がサイズ調整することを意味します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-197">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A> which means that the rows will be sized base on the content in the rows.</span></span> <span data-ttu-id="6bb39-198">既定値<xref:System.Windows.Controls.RowDefinition.Height%2A>は<xref:System.Windows.GridUnitType.Star>サイズ変更は、行が使用可能な領域の加重比率になることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-198">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row will be a weighted proportion of the available space.</span></span> <span data-ttu-id="6bb39-199">たとえば、2 つの行それぞれの高さが "*" の場合、各行の高さは、使用可能なスペースの半分になります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-199">For example if two rows each have a height of "*", they will each have a height that is half of the available space.</span></span>  
  
     <span data-ttu-id="6bb39-200"><xref:System.Windows.Controls.Grid>は次の XAML のようになります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-200">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a><span data-ttu-id="6bb39-201">コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-201">Adding controls</span></span>  
 <span data-ttu-id="6bb39-202">このセクションでは、ホーム ページの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]が更新されことから選択できる、選択された人物の経費報告書を表示するユーザーの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-202">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated to show a list of people that users can select from to show the expense report for a selected person.</span></span> <span data-ttu-id="6bb39-203">コントロールとは、ユーザーがアプリケーションと対話できるようにする UI オブジェクトのことです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-203">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="6bb39-204">詳しくは、「 [コントロール](../../../../docs/framework/wpf/controls/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6bb39-204">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span> 
  
 <span data-ttu-id="6bb39-205">これを作成する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ExpenseItHome.xaml に、次の要素が追加されます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-205">To create this [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], the following elements are added to ExpenseItHome.xaml:</span></span>  
  
-   <span data-ttu-id="6bb39-206"><xref:System.Windows.Controls.ListBox>(用、ユーザーの一覧)。</span><span class="sxs-lookup"><span data-stu-id="6bb39-206"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span> 
  
-   <span data-ttu-id="6bb39-207"><xref:System.Windows.Controls.Label>(リストのヘッダーとして)。</span><span class="sxs-lookup"><span data-stu-id="6bb39-207"><xref:System.Windows.Controls.Label> (for the list header).</span></span> 
  
-   <span data-ttu-id="6bb39-208"><xref:System.Windows.Controls.Button>(をクリックして、一覧で選択されているユーザーの経費報告書を表示する)。</span><span class="sxs-lookup"><span data-stu-id="6bb39-208"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span> 
  
 <span data-ttu-id="6bb39-209">行内の各コントロールが配置される、<xref:System.Windows.Controls.Grid>を設定して、<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>添付プロパティ。</span><span class="sxs-lookup"><span data-stu-id="6bb39-209">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="6bb39-210">添付プロパティの詳細については、次を参照してください。[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-210">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span> 
  
1. <span data-ttu-id="6bb39-211">ExpenseItHome.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-211">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="6bb39-212">次の追加[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]間、<xref:System.Windows.Controls.Grid>タグ。</span><span class="sxs-lookup"><span data-stu-id="6bb39-212">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. <span data-ttu-id="6bb39-213">アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-213">Build and run the application.</span></span> 
  
 <span data-ttu-id="6bb39-214">次の図は、このセクションの XAML で作成されたコントロールを示しています。</span><span class="sxs-lookup"><span data-stu-id="6bb39-214">The following illustration shows the controls that are created by the XAML in this section.</span></span> 
  
 <span data-ttu-id="6bb39-215">![ExpenseIt のサンプルのスクリーン ショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span><span class="sxs-lookup"><span data-stu-id="6bb39-215">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span></span>  
  
## <a name="adding-an-image-and-a-title"></a><span data-ttu-id="6bb39-216">イメージとタイトルを追加します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-216">Adding an image and a title</span></span>  
 <span data-ttu-id="6bb39-217">このセクションでは、ホーム ページの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]イメージとページ タイトルで更新されます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-217">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated with an image and a page title.</span></span> 
  
1. <span data-ttu-id="6bb39-218">ExpenseItHome.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-218">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="6bb39-219">別の列を追加、<xref:System.Windows.Controls.Grid.ColumnDefinitions%2A>固定の<xref:System.Windows.Controls.ColumnDefinition.Width%2A>230 ピクセルのです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-219">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels.</span></span> 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. <span data-ttu-id="6bb39-220">別の行を追加、<xref:System.Windows.Controls.Grid.RowDefinitions%2A>です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-220">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span></span> 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. <span data-ttu-id="6bb39-221">2 番目の列に設定して、コントロールを移動<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>を 1 にします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-221">Move the controls to the second column by setting <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> to 1.</span></span> <span data-ttu-id="6bb39-222">下の行を増やすことで各コントロールを移動する、<xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType>を 1 つです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-222">Move each control down a row, by increasing the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> by 1.</span></span> 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. <span data-ttu-id="6bb39-223">設定、<xref:System.Windows.Controls.Panel.Background%2A>の<xref:System.Windows.Controls.Grid>watermark.png イメージ ファイルであることにします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-223">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the watermark.png image file.</span></span> 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. <span data-ttu-id="6bb39-224">前に、 <xref:System.Windows.Controls.Border>、追加、<xref:System.Windows.Controls.Label>経費レポートの表示 ページのタイトルになるコンテンツを使用します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-224">Before the <xref:System.Windows.Controls.Border>, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report" to be the title of the page.</span></span> 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. <span data-ttu-id="6bb39-225">アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-225">Build and run the application.</span></span> 
  
 <span data-ttu-id="6bb39-226">次の図は、このセクションの結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="6bb39-226">The following illustration shows the results of this section.</span></span> 
  
 <span data-ttu-id="6bb39-227">![ExpenseIt のサンプルのスクリーン ショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span><span class="sxs-lookup"><span data-stu-id="6bb39-227">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span></span>  
  
## <a name="adding-code-to-handle-events"></a><span data-ttu-id="6bb39-228">イベントを処理するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-228">Adding code to handle events</span></span>  
  
1. <span data-ttu-id="6bb39-229">ExpenseItHome.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-229">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="6bb39-230">追加、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント ハンドラーを<xref:System.Windows.Controls.Button>要素。</span><span class="sxs-lookup"><span data-stu-id="6bb39-230">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="6bb39-231">詳細については、次を参照してください。[する方法: 単純なイベント ハンドラーを作成する](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-231">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span></span> 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. <span data-ttu-id="6bb39-232">ExpenseItHome.xaml.vb または ExpenseItHome.xaml.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-232">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="6bb39-233">次のコードを追加、 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 、によって ExpenseReportPage.xaml ファイルに移動するウィンドウのイベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="6bb39-233">Add the following code to the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler, which causes the window to navigate to the ExpenseReportPage.xaml file.</span></span> 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a><span data-ttu-id="6bb39-234">ExpenseReportPage の UI の作成</span><span class="sxs-lookup"><span data-stu-id="6bb39-234">Creating the UI for ExpenseReportPage</span></span>  
 <span data-ttu-id="6bb39-235">ExpenseReportPage.xaml には、ExpenseItHome.xaml で選択した個人の経費報告書が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-235">ExpenseReportPage.xaml displays the expense report for the person that was selected on the ExpenseItHome.xaml.</span></span> <span data-ttu-id="6bb39-236">このセクションでは、コントロールを追加し、作成、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ExpenseReportPage.xaml 用です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-236">This section adds controls and creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for ExpenseReportPage.xaml.</span></span> <span data-ttu-id="6bb39-237">ここでは、さまざまな背景の塗りつぶしの色を追加するも[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素。</span><span class="sxs-lookup"><span data-stu-id="6bb39-237">This section also adds background and fill colors to the various [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> 
  
1. <span data-ttu-id="6bb39-238">ExpenseReportPage.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-238">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="6bb39-239"><xref:System.Windows.Controls.Grid> タグの間に次の XAML を追加します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-239">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
     <span data-ttu-id="6bb39-240">この UI はで、レポート データが表示される点を除いて、ExpenseItHome.xaml で作成した ui と似ています、<xref:System.Windows.Controls.DataGrid>です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-240">This UI is similar to the UI created on ExpenseItHome.xaml except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span> 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. <span data-ttu-id="6bb39-241">アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-241">Build and run the application.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="6bb39-242">エラーを取得する場合、<xref:System.Windows.Controls.DataGrid>が見つかりませんでしたまたは存在しない、プロジェクトの対象 .NET Framework 4 以降であるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-242">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="6bb39-243">詳細については、「[方法: .NET Framework のバージョンをターゲットにする](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bb39-243">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
4. <span data-ttu-id="6bb39-244">クリックして、**ビュー**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-244">Click the **View** button.</span></span> 
  
     <span data-ttu-id="6bb39-245">経費明細書ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-245">The expense report page appears.</span></span> 
  
 <span data-ttu-id="6bb39-246">次の図は、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ExpenseReportPage.xaml に追加された要素。</span><span class="sxs-lookup"><span data-stu-id="6bb39-246">The following illustration shows the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements added to ExpenseReportPage.xaml.</span></span> <span data-ttu-id="6bb39-247">[戻る] ナビゲーション ボタンが有効になっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6bb39-247">Notice that the back navigation button is enabled.</span></span> 
  
 <span data-ttu-id="6bb39-248">![ExpenseIt のサンプルのスクリーン ショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span><span class="sxs-lookup"><span data-stu-id="6bb39-248">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span></span>  
  
## <a name="styling-controls"></a><span data-ttu-id="6bb39-249">コントロールのスタイル</span><span class="sxs-lookup"><span data-stu-id="6bb39-249">Styling controls</span></span>  
 <span data-ttu-id="6bb39-250">さまざまな要素の外観は、同じ型でのすべての要素の同じ多くの場合、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-250">The appearance of various elements can often be the same for all elements of the same type in a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]<span data-ttu-id="6bb39-251"> では、複数の要素間で外観を再利用できるように、スタイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-251"> uses styles to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="6bb39-252">スタイルの再利用が簡略化するのに役立つ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の作成および管理します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-252">The reusability of styles helps to simplify [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] creation and management.</span></span> <span data-ttu-id="6bb39-253">スタイルの詳細については、次を参照してください。[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-253">For more information about styles, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span> <span data-ttu-id="6bb39-254">このセクションでは、これまでの手順で定義した要素ごとの属性を、スタイルに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-254">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span> 
  
1. <span data-ttu-id="6bb39-255">Application.xaml または App.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-255">Open Application.xaml or App.xaml.</span></span> 
  
2. <span data-ttu-id="6bb39-256">間に次の XAML を追加、<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>タグ。</span><span class="sxs-lookup"><span data-stu-id="6bb39-256">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     <span data-ttu-id="6bb39-257">これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]次のスタイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-257">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adds the following styles:</span></span>  
  
    -  <span data-ttu-id="6bb39-258">`headerTextStyle`: ページ タイトル <xref:System.Windows.Controls.Label>の書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-258">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="6bb39-259">`labelStyle`: <xref:System.Windows.Controls.Label> コントロールの書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-259">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span> 
  
    -  <span data-ttu-id="6bb39-260">`columnHeaderStyle`: <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>の書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-260">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span> 
  
    -  <span data-ttu-id="6bb39-261">`listHeaderStyle`: リスト ヘッダーの <xref:System.Windows.Controls.Border> コントロールの書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-261">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span> 
  
    -  <span data-ttu-id="6bb39-262">`listHeaderTextStyle`: 一覧のヘッダーを書式設定するには<xref:System.Windows.Controls.Label>です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-262">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="6bb39-263">`buttonStyle`: 書式設定するには<xref:System.Windows.Controls.Button>ExpenseItHome.xaml にします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-263">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on ExpenseItHome.xaml.</span></span> 
  
     <span data-ttu-id="6bb39-264">スタイルがリソースとの子であることを確認、<xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>プロパティ要素。</span><span class="sxs-lookup"><span data-stu-id="6bb39-264">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="6bb39-265">ここでは、スタイルはアプリケーション内のすべての要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-265">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="6bb39-266">内のリソースを使用する例については、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]アプリケーションを参照してください[アプリケーション リソースの使用](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md)です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-266">For an example of using resources in a [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span> 
  
3. <span data-ttu-id="6bb39-267">ExpenseItHome.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-267">Open ExpenseItHome.xaml.</span></span> 
  
4. <span data-ttu-id="6bb39-268">間のすべてのものを置き換える、<xref:System.Windows.Controls.Grid>を次の XAML 要素。</span><span class="sxs-lookup"><span data-stu-id="6bb39-268">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     <span data-ttu-id="6bb39-269">各コントロールの外観を定義する <xref:System.Windows.VerticalAlignment> や <xref:System.Windows.Media.FontFamily> などのプロパティは、これらのスタイルを適用することで、削除されて置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-269">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="6bb39-270">たとえば、 `headerTextStyle` 、支出レポートの表示 に適用される<xref:System.Windows.Controls.Label>です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-270">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span> 
  
5. <span data-ttu-id="6bb39-271">ExpenseReportPage.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-271">Open ExpenseReportPage.xaml.</span></span> 
  
6. <span data-ttu-id="6bb39-272">間のすべてのものを置き換える、<xref:System.Windows.Controls.Grid>を次の XAML 要素。</span><span class="sxs-lookup"><span data-stu-id="6bb39-272">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     <span data-ttu-id="6bb39-273">これにより、スタイルが <xref:System.Windows.Controls.Label> と <xref:System.Windows.Controls.Border> の要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-273">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span> 
  
7. <span data-ttu-id="6bb39-274">アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-274">Build and run the application.</span></span> 
  
     <span data-ttu-id="6bb39-275">追加した後、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]このセクションで、アプリケーションの外観は同じとスタイルを使用して更新される前にします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-275">After adding the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] in this section, the application looks the same as it did before being updated with styles.</span></span> 
  
## <a name="binding-data-to-a-control"></a><span data-ttu-id="6bb39-276">コントロールへのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="6bb39-276">Binding data to a control</span></span>  
 <span data-ttu-id="6bb39-277">このセクションで作成、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]さまざまなコントロールにバインドされているデータ。</span><span class="sxs-lookup"><span data-stu-id="6bb39-277">In this section, you create the [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] data that is bound to various controls.</span></span> 
  
1. <span data-ttu-id="6bb39-278">ExpenseItHome.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-278">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="6bb39-279">開始後に<xref:System.Windows.Controls.Grid>要素を作成する次の XAML を追加、<xref:System.Windows.Data.XmlDataProvider>個人ごとにデータを格納しています。</span><span class="sxs-lookup"><span data-stu-id="6bb39-279">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person.</span></span> 
  
     <span data-ttu-id="6bb39-280">データとして作成、<xref:System.Windows.Controls.Grid>リソース。</span><span class="sxs-lookup"><span data-stu-id="6bb39-280">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="6bb39-281">通常、これはファイルとして読み込まれますが、説明を簡単にするため、データをインラインで追加します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-281">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. <span data-ttu-id="6bb39-282"><xref:System.Windows.Controls.Grid>リソース、次の追加<xref:System.Windows.DataTemplate>、データを表示する方法を定義する、<xref:System.Windows.Controls.ListBox>です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-282">In the <xref:System.Windows.Controls.Grid> resource, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="6bb39-283">データ テンプレートの詳細については「 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bb39-283">For more information about data templates, see [Data Templating Overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. <span data-ttu-id="6bb39-284">既存の置換<xref:System.Windows.Controls.ListBox>次の XAML を使用します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-284">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     <span data-ttu-id="6bb39-285">次の XAML バインド、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>データ ソースに、データ テンプレートとして適用されると、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-285">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span> 
  
## <a name="connecting-data-to-controls"></a><span data-ttu-id="6bb39-286">コントロールにデータを接続します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-286">Connecting data to controls</span></span>  
 <span data-ttu-id="6bb39-287">このセクションで、ExpenseItHome.xaml ページで、ユーザーの一覧で選択されのコンス トラクターへの参照を渡しますを現在の項目を取得するコードを記述する`ExpenseReportPage`インスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-287">In this section, you write the code that retrieves the current item that is selected in the list of people on the ExpenseItHome.xaml page, and passes its reference to the constructor of `ExpenseReportPage` during instantiation.</span></span> <span data-ttu-id="6bb39-288">`ExpenseReportPage` は、渡された項目を使用してデータ コンテキストを設定します。この項目が、ExpenseReportPage.xaml で定義されたコントロールのバインド先になります。</span><span class="sxs-lookup"><span data-stu-id="6bb39-288">`ExpenseReportPage` sets its data context with the passed item, which is what the controls defined in ExpenseReportPage.xaml will bind to.</span></span> 
  
1. <span data-ttu-id="6bb39-289">ExpenseReportPage.xaml.vb または ExpenseReportPage.xaml.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-289">Open ExpenseReportPage.xaml.vb or ExpenseReportPage.xaml.cs.</span></span> 
  
2. <span data-ttu-id="6bb39-290">オブジェクトを取得するコンストラクターを追加して、選択した個人の経費報告書データを渡せるようにします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-290">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. <span data-ttu-id="6bb39-291">ExpenseItHome.xaml.vb または ExpenseItHome.xaml.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-291">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="6bb39-292">変更、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>選択したユーザーの経費報告書データを渡す新しいコンス トラクターを呼び出すイベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="6bb39-292">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a><span data-ttu-id="6bb39-293">データ テンプレートを使用してデータのスタイル設定</span><span class="sxs-lookup"><span data-stu-id="6bb39-293">Styling data with data templates</span></span>  
 <span data-ttu-id="6bb39-294">このセクションで更新する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]バインドされたリストをデータ テンプレートを使用して、データ内の各項目。</span><span class="sxs-lookup"><span data-stu-id="6bb39-294">In this section, you update the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for each item in the data bound lists by using data templates.</span></span> 
  
1. <span data-ttu-id="6bb39-295">ExpenseReportPage.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="6bb39-295">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="6bb39-296">「名前」と"Department"の内容をバインド<xref:System.Windows.Controls.Label>要素を適切なデータ ソースのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-296">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="6bb39-297">データ バインディングの詳細については、「[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bb39-297">For more information about data binding, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. <span data-ttu-id="6bb39-298">オープン後<xref:System.Windows.Controls.Grid>要素、経費報告書データを表示する方法を定義する次のデータ テンプレートを追加します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-298">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data.</span></span>  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. <span data-ttu-id="6bb39-299">テンプレートを適用する、<xref:System.Windows.Controls.DataGrid>経費を表示する列がデータを報告します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-299">Apply the templates to the <xref:System.Windows.Controls.DataGrid> columns that display the expense report data.</span></span> 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. <span data-ttu-id="6bb39-300">アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="6bb39-300">Build and run the application.</span></span> 
  
6. <span data-ttu-id="6bb39-301">ユーザーを選択し、クリックして、**ビュー**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6bb39-301">Select a person and click the **View** button.</span></span> 
  
 <span data-ttu-id="6bb39-302">次の図には、コントロール、レイアウト、スタイル、データ バインディング、データ テンプレートが適用された ExpenseIt アプリケーションの両方のページが示されています。</span><span class="sxs-lookup"><span data-stu-id="6bb39-302">The following illustration shows both pages of the ExpenseIt application with controls, layout, styles, data binding, and data templates applied.</span></span> 
  
 <span data-ttu-id="6bb39-303">![ExpenseIt のサンプルのスクリーン ショット](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span><span class="sxs-lookup"><span data-stu-id="6bb39-303">![ExpenseIt sample screen shots](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="6bb39-304">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="6bb39-304">Best practices</span></span>  
 <span data-ttu-id="6bb39-305">このサンプルは、WPF の特定の機能を説明するものであり、アプリケーション開発のベスト プラクティスには従っていません。</span><span class="sxs-lookup"><span data-stu-id="6bb39-305">This sample demonstrates a specific feature of WPF and, consequently, does not follow application development best practices.</span></span> <span data-ttu-id="6bb39-306">包括的なカバレッジ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]アプリケーション開発のベスト プラクティスでは、必要に応じて、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bb39-306">For comprehensive coverage of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] and the [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application development best practices, see the following topics as appropriate:</span></span>  
  
-   <span data-ttu-id="6bb39-307">ユーザー補助 - [ユーザー補助のベスト プラクティス](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span><span class="sxs-lookup"><span data-stu-id="6bb39-307">Accessibility - [Accessibility Best Practices](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span></span>  
  
-   <span data-ttu-id="6bb39-308">セキュリティ -[セキュリティ](../../../../docs/framework/wpf/security-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="6bb39-308">Security - [Security](../../../../docs/framework/wpf/security-wpf.md)</span></span>  
  
-   <span data-ttu-id="6bb39-309">ローカリゼーション - [WPF のグローバリゼーションおよびローカリゼーションの概要](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span><span class="sxs-lookup"><span data-stu-id="6bb39-309">Localization - [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span></span>  
  
-   <span data-ttu-id="6bb39-310">パフォーマンス - [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span><span class="sxs-lookup"><span data-stu-id="6bb39-310">Performance - [Optimizing WPF Application Performance](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span></span>  
  
## <a name="whats-next"></a><span data-ttu-id="6bb39-311">次の内容</span><span class="sxs-lookup"><span data-stu-id="6bb39-311">What's next</span></span>  
 <span data-ttu-id="6bb39-312">ユーザーが自由に作成するためのさまざまな手法があるようになりました、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を使用して[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6bb39-312">You now have a number of techniques at your disposal for creating a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] using [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span> <span data-ttu-id="6bb39-313">データ バインドの基本的な構成要素の広範な理解が[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-313">You should now have a broad understanding of the basic building blocks of a data-bound [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application.</span></span> <span data-ttu-id="6bb39-314">このトピックは決して網羅的なものではありませんが、このトピックの手法を基に、自分で学習を進められるようになったはずです。</span><span class="sxs-lookup"><span data-stu-id="6bb39-314">This topic is by no means exhaustive, but hopefully you also now have a sense of some of the possibilities you might discover on your own beyond the techniques in this topic.</span></span> 
  
 <span data-ttu-id="6bb39-315">WPF のアーキテクチャおよびプログラミング モデルの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bb39-315">For more information about the WPF architecture and programming models, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6bb39-316">WPF アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="6bb39-316">WPF Architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [<span data-ttu-id="6bb39-317">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="6bb39-317">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [<span data-ttu-id="6bb39-318">依存関係プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="6bb39-318">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [<span data-ttu-id="6bb39-319">レイアウト</span><span class="sxs-lookup"><span data-stu-id="6bb39-319">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
  
 <span data-ttu-id="6bb39-320">アプリケーションの作成の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bb39-320">For more information about creating applications, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6bb39-321">アプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="6bb39-321">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [<span data-ttu-id="6bb39-322">コントロール</span><span class="sxs-lookup"><span data-stu-id="6bb39-322">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
  
-   [<span data-ttu-id="6bb39-323">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="6bb39-323">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [<span data-ttu-id="6bb39-324">グラフィックスとマルチメディア</span><span class="sxs-lookup"><span data-stu-id="6bb39-324">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [<span data-ttu-id="6bb39-325">WPF のドキュメント</span><span class="sxs-lookup"><span data-stu-id="6bb39-325">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a><span data-ttu-id="6bb39-326">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bb39-326">See also</span></span>  
 [<span data-ttu-id="6bb39-327">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="6bb39-327">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="6bb39-328">データ テンプレートの概要</span><span class="sxs-lookup"><span data-stu-id="6bb39-328">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="6bb39-329">WPF アプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="6bb39-329">Building a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [<span data-ttu-id="6bb39-330">スタイルおよびテンプレート</span><span class="sxs-lookup"><span data-stu-id="6bb39-330">Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
