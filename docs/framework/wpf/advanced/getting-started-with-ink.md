---
title: インクの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: 9a1b53d0513eeef377fe8e012a8d5d7ea3f8a984
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546238"
---
# <a name="getting-started-with-ink"></a><span data-ttu-id="44414-102">インクの概要</span><span class="sxs-lookup"><span data-stu-id="44414-102">Getting Started with Ink</span></span>
<span data-ttu-id="44414-103">デジタル インクを組み込むことをアプリケーションには、これまでよりも簡単です。</span><span class="sxs-lookup"><span data-stu-id="44414-103">Incorporating digital ink into your applications is easier than ever.</span></span> <span data-ttu-id="44414-104">インクのプログラミングに完全な統合を実現するための COM および Windows フォームのメソッドへの推論の進化に伴い、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="44414-104">Ink has evolved from being a corollary to the COM and Windows Forms method of programming to achieving full integration into the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="44414-105">個別の Sdk またはランタイム ライブラリをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="44414-105">You do not need to install separate SDKs or runtime libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="44414-106">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="44414-106">Prerequisites</span></span>  
 <span data-ttu-id="44414-107">次の例を使用する、Microsoft Visual Studio 2005 をインストールする必要があります最初、[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="44414-107">To use the following examples, you must first install Microsoft Visual Studio 2005 and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="44414-108">また、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に対応するアプリケーションの作成方法も理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="44414-108">You should also understand how to write applications for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="44414-109">概要の詳細については、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を参照してください[チュートリアル: 最初の WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="44414-109">For more information about getting started with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="quick-start"></a><span data-ttu-id="44414-110">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="44414-110">Quick Start</span></span>  
 <span data-ttu-id="44414-111">このセクションでは、単純なを作成できます。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]インクを収集するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="44414-111">This section helps you write a simple [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application that collects ink.</span></span>  
  
 <span data-ttu-id="44414-112">完了していない場合は、Microsoft Visual Studio 2005 をインストールし、[!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="44414-112">If you haven't already done so, install Microsoft Visual Studio 2005 and the [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)].</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="44414-113"> アプリケーション通常コンパイルする必要が、それらを表示する前にのみで構成されている場合でも[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="44414-113"> applications usually must be compiled before you can view them, even if they consist entirely of [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="44414-114">ただし、[!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)]を実装するプロセスを高速化するように設計 XamlPad のアプリケーションが含まれています、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-ベースの UI。</span><span class="sxs-lookup"><span data-stu-id="44414-114">However, the [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] includes an application, XamlPad, designed to speed up the process of implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-based UI.</span></span> <span data-ttu-id="44414-115">そのアプリケーションを使用して、表示およびこのドキュメントで最初のいくつかのサンプルを修正することができます。</span><span class="sxs-lookup"><span data-stu-id="44414-115">You can use that application to view and tinker with the first few samples in this document.</span></span> <span data-ttu-id="44414-116">作成プロセスからコンパイルされたアプリケーション[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、このドキュメントの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="44414-116">The process of creating compiled applications from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is covered later in this document.</span></span>  
  
 <span data-ttu-id="44414-117">XAMLPad を起動する をクリックして、**開始** メニューのをポイント**すべてのプログラム**、指す**Microsoft Windows SDK**、 をポイント**ツール**、 をクリック**XAMLPad**です。</span><span class="sxs-lookup"><span data-stu-id="44414-117">To launch XAMLPad, click the **Start** menu, point to **All Programs**, point to **Microsoft Windows SDK**, point to **Tools**, and click **XAMLPad**.</span></span> <span data-ttu-id="44414-118">表示ウィンドウでは、XAMLPad は、コード ペインで記述された XAML コードを表示します。</span><span class="sxs-lookup"><span data-stu-id="44414-118">In the rendering pane, XAMLPad renders the XAML code written in the code pane.</span></span> <span data-ttu-id="44414-119">XAML コードを編集することができ、変更はすぐに表示ウィンドウで表示します。</span><span class="sxs-lookup"><span data-stu-id="44414-119">You can edit the XAML code, and the changes immediately appear in the rendering pane.</span></span>  
  
#### <a name="got-ink"></a><span data-ttu-id="44414-120">インクを取得します。</span><span class="sxs-lookup"><span data-stu-id="44414-120">Got Ink?</span></span>  
 <span data-ttu-id="44414-121">初めて開始する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]インクをサポートするアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="44414-121">To start your first [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application that supports ink:</span></span>  
  
1.  <span data-ttu-id="44414-122">Microsoft Visual Studio 2005 を開きます。</span><span class="sxs-lookup"><span data-stu-id="44414-122">Open Microsoft Visual Studio 2005</span></span>  
  
2.  <span data-ttu-id="44414-123">新しい**Windows アプリケーション (WPF)**</span><span class="sxs-lookup"><span data-stu-id="44414-123">Create a new **Windows Application (WPF)**</span></span>  
  
3.  <span data-ttu-id="44414-124">型`<InkCanvas/>`間、`<Grid>`タグ</span><span class="sxs-lookup"><span data-stu-id="44414-124">Type `<InkCanvas/>` between the `<Grid>` tags</span></span>  
  
4.  <span data-ttu-id="44414-125">キーを押して**f5 キーを押して**デバッガーでアプリケーションを起動するには</span><span class="sxs-lookup"><span data-stu-id="44414-125">Press **F5** to launch your application in the debugger</span></span>  
  
5.  <span data-ttu-id="44414-126">スタイラスおよびマウスを使用して、記述**hello world**  ウィンドウで</span><span class="sxs-lookup"><span data-stu-id="44414-126">Using a stylus or mouse, write **hello world** in the window</span></span>  
  
 <span data-ttu-id="44414-127">相当するインクのみ 12 回のキーストロークで"hello world"アプリケーションを作成した!</span><span class="sxs-lookup"><span data-stu-id="44414-127">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>  
  
#### <a name="spice-up-your-application"></a><span data-ttu-id="44414-128">アプリケーションを楽しくする. します。</span><span class="sxs-lookup"><span data-stu-id="44414-128">Spice Up Your Application</span></span>  
 <span data-ttu-id="44414-129">一部の機能のライセンス認証の利用、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="44414-129">Let’s take advantage of some features of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  <span data-ttu-id="44414-130">開く間にあるすべてを置換\<ウィンドウ > タグと終了\</Window > タグで、次マークアップでします。</span><span class="sxs-lookup"><span data-stu-id="44414-130">Replace everything between the opening \<Window> and closing \</Window> tags with the following markup to get a gradient brush background on your inking surface.</span></span>  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a><span data-ttu-id="44414-131">アニメーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="44414-131">Using Animation</span></span>  
 <span data-ttu-id="44414-132">楽しい、グラデーション ブラシの色をアニメーション化してみましょう。</span><span class="sxs-lookup"><span data-stu-id="44414-132">For fun, let's animate the colors of the gradient brush.</span></span> <span data-ttu-id="44414-133">次の追加[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、終了後に`</InkCanvas>`タグが終了する前に`</Page>`タグ。</span><span class="sxs-lookup"><span data-stu-id="44414-133">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] after the closing `</InkCanvas>` tag but before the closing `</Page>` tag.</span></span>  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a><span data-ttu-id="44414-134">XAML の背後にある一部のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="44414-134">Adding Some Code Behind the XAML</span></span>  
 <span data-ttu-id="44414-135">XAML では、非常に簡単にユーザー インターフェイスをデザイン、イベントを処理するコードを追加する任意の実際のアプリケーションが必要です。</span><span class="sxs-lookup"><span data-stu-id="44414-135">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="44414-136">右クリック マウスからの応答でインクを拡大する簡単な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="44414-136">Here is a simple example that zooms in on the ink in response to a right-click from a mouse:</span></span>  
  
 <span data-ttu-id="44414-137">設定、`MouseRightButtonUp`ハンドラー、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="44414-137">Set the `MouseRightButtonUp` handler in your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:</span></span>  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 <span data-ttu-id="44414-138">Visual Studio のソリューション エクスプ ローラーで、Windows1.xaml を展開し、window1.xaml.cs の名前または Window1.xaml.vb Visual Basic を使用している場合、分離コード ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="44414-138">In Visual Studio’s Solution Explorer, expand Windows1.xaml and open the code-behind file, Window1.xaml.cs or Window1.xaml.vb if you are using Visual Basic.</span></span> <span data-ttu-id="44414-139">次のイベント ハンドラーのコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="44414-139">Add the following event handler code:</span></span>  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 <span data-ttu-id="44414-140">ここで、アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="44414-140">Now, run your application.</span></span> <span data-ttu-id="44414-141">インクを追加およびマウスで右クリックするか、スタイラスを使用して、等価なプレス アンド ホールドを実行します。</span><span class="sxs-lookup"><span data-stu-id="44414-141">Add some ink and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>  
  
#### <a name="using-procedural-code-instead-of-xaml"></a><span data-ttu-id="44414-142">XAML ではなく、手続き型コードを使用します。</span><span class="sxs-lookup"><span data-stu-id="44414-142">Using Procedural Code Instead of XAML</span></span>  
 <span data-ttu-id="44414-143">すべてにアクセスできる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]手続き型コードから機能します。</span><span class="sxs-lookup"><span data-stu-id="44414-143">You can access all [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] features from procedural code.</span></span> <span data-ttu-id="44414-144">ここでは、"こんにちはインク World"アプリケーションの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用しない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]まったくです。</span><span class="sxs-lookup"><span data-stu-id="44414-144">Here is a "Hello Ink World" application for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] that doesn’t use any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] at all.</span></span> <span data-ttu-id="44414-145">Visual Studio での空のコンソール アプリケーションには、次のコードを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="44414-145">Paste the code below into an empty Console Application in Visual Studio.</span></span> <span data-ttu-id="44414-146">PresentationCore、PresentationFramework、および WindowsBase アセンブリへの参照を追加し、キーを押してアプリケーションをビルド**f5 キーを押して**:</span><span class="sxs-lookup"><span data-stu-id="44414-146">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies, and build the application by pressing **F5**:</span></span>  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="44414-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="44414-147">See Also</span></span>  
 [<span data-ttu-id="44414-148">デジタル インク</span><span class="sxs-lookup"><span data-stu-id="44414-148">Digital Ink</span></span>](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [<span data-ttu-id="44414-149">インクの収集</span><span class="sxs-lookup"><span data-stu-id="44414-149">Collecting Ink</span></span>](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [<span data-ttu-id="44414-150">手書き認識</span><span class="sxs-lookup"><span data-stu-id="44414-150">Handwriting Recognition</span></span>](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [<span data-ttu-id="44414-151">インクの格納</span><span class="sxs-lookup"><span data-stu-id="44414-151">Storing Ink</span></span>](../../../../docs/framework/wpf/advanced/storing-ink.md)
