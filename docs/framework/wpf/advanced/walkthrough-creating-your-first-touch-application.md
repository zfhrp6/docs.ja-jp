---
title: 'チュートリアル: 初めてのタッチ アプリケーションの作成'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
ms.openlocfilehash: 94a97c30179f7a8231426e31b8cacc364629ffc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-your-first-touch-application"></a><span data-ttu-id="7e3e5-102">チュートリアル: 初めてのタッチ アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="7e3e5-102">Walkthrough: Creating Your First Touch Application</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="7e3e5-103"> タッチに応答するアプリケーションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-103"> enables applications to respond to touch.</span></span> <span data-ttu-id="7e3e5-104">たとえば、1 つを使用して、アプリケーションと対話できます。 または多くを指でタッチ スクリーンがこのチュートリアルにより、ユーザーに移動するアプリケーションを作成するなどのタッチ依存型デバイスのサイズ変更、またはタッチを使用して、1 つのオブジェクトを回転します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-104">For example, you can interact with an application by using one or more fingers on a touch-sensitive device, such as a touchscreen This walkthrough creates an application that enables the user to move, resize, or rotate a single object by using touch.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7e3e5-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7e3e5-105">Prerequisites</span></span>  
 <span data-ttu-id="7e3e5-106">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]<span data-ttu-id="7e3e5-107">。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-107">.</span></span>  
  
-   <span data-ttu-id="7e3e5-108">Windows 7。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-108">Windows 7.</span></span>  
  
-   <span data-ttu-id="7e3e5-109">Windows タッチをサポートするタッチ スクリーンなど、タッチ入力を受け付けるデバイス。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-109">A device that accepts touch input, such as a touchscreen, that supports Windows Touch.</span></span>  
  
 <span data-ttu-id="7e3e5-110">さらでアプリケーションを作成する方法の基本的な知識を持つ必要があります[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]にサブスクライブし、イベントを処理する方法に特にです。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-110">Additionally, you should have a basic understanding of how to create an application in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especially how to subscribe to and handle an event.</span></span> <span data-ttu-id="7e3e5-111">詳細については、次を参照してください。[チュートリアル: 最初の WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-111">For more information, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="creating-the-application"></a><span data-ttu-id="7e3e5-112">アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="7e3e5-112">Creating the Application</span></span>  
  
#### <a name="to-create-the-application"></a><span data-ttu-id="7e3e5-113">アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="7e3e5-113">To create the application</span></span>  
  
1.  <span data-ttu-id="7e3e5-114">Visual Basic または Visual c# のという名前の新しい WPF アプリケーション プロジェクトを作成する`BasicManipulation`です。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-114">Create a new WPF Application project in Visual Basic or Visual C# named `BasicManipulation`.</span></span> <span data-ttu-id="7e3e5-115">詳細については、次を参照してください。[する方法: 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)です。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-115">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="7e3e5-116">MainWindow.xaml の内容を次の XAML に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-116">Replace the contents of MainWindow.xaml with the following XAML.</span></span>  
  
     <span data-ttu-id="7e3e5-117">このマークアップを含む赤い簡単なアプリケーションを作成する<xref:System.Windows.Shapes.Rectangle>上、<xref:System.Windows.Controls.Canvas>です。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-117">This markup creates a simple application that contains a red <xref:System.Windows.Shapes.Rectangle> on a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="7e3e5-118"><xref:System.Windows.UIElement.IsManipulationEnabled%2A>のプロパティ、<xref:System.Windows.Shapes.Rectangle>操作イベントを受信するために true に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-118">The <xref:System.Windows.UIElement.IsManipulationEnabled%2A> property of the <xref:System.Windows.Shapes.Rectangle> is set to true so that it will receive manipulation events.</span></span> <span data-ttu-id="7e3e5-119">サブスクライブするアプリケーション、 <xref:System.Windows.UIElement.ManipulationStarting>、 <xref:System.Windows.UIElement.ManipulationDelta>、および<xref:System.Windows.UIElement.ManipulationInertiaStarting>イベント。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-119">The application subscribes to the <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, and <xref:System.Windows.UIElement.ManipulationInertiaStarting> events.</span></span> <span data-ttu-id="7e3e5-120">これらのイベントに移動するためのロジックが含まれて、<xref:System.Windows.Shapes.Rectangle>ユーザーからの操作をすることです。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-120">These events contain the logic to move the <xref:System.Windows.Shapes.Rectangle> when the user manipulates it.</span></span>  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  <span data-ttu-id="7e3e5-121">Visual Basic で MainWindow.xaml の最初の行を使用している場合は置き換えます`x:Class="BasicManipulation.MainWindow"`で`x:Class="MainWindow"`です。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-121">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="BasicManipulation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
4.  <span data-ttu-id="7e3e5-122">`MainWindow`クラス、次の追加<xref:System.Windows.UIElement.ManipulationStarting>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-122">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationStarting> event handler.</span></span>  
  
     <span data-ttu-id="7e3e5-123"><xref:System.Windows.UIElement.ManipulationStarting>イベントが発生したときに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]そのタッチを検出したオブジェクトを操作する入力を開始します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-123">The <xref:System.Windows.UIElement.ManipulationStarting> event occurs when [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detects that touch input begins to manipulate an object.</span></span> <span data-ttu-id="7e3e5-124">コードでは、操作の位置が基準にする必要がありますを指定します、<xref:System.Windows.Window>を設定して、<xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-124">The code specifies that the position of the manipulation should be relative to the <xref:System.Windows.Window> by setting the <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> property.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  <span data-ttu-id="7e3e5-125">`MainWindow`クラス、次の追加<xref:System.Windows.Input.ManipulationDelta>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-125">In the `MainWindow` class, add the following <xref:System.Windows.Input.ManipulationDelta> event handler.</span></span>  
  
     <span data-ttu-id="7e3e5-126"><xref:System.Windows.Input.ManipulationDelta>イベント、タッチ入力の位置を変更および操作中に複数回発生する可能性がときに発生します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-126">The <xref:System.Windows.Input.ManipulationDelta> event occurs when the touch input changes position and can occur multiple times during a manipulation.</span></span> <span data-ttu-id="7e3e5-127">イベントは、指が発生した後にも発生することができます。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-127">The event can also occur after a finger is raised.</span></span> <span data-ttu-id="7e3e5-128">たとえば、ユーザーが、画面上で指をドラッグする場合、<xref:System.Windows.Input.ManipulationDelta>イベントは、複数回を指移動するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-128">For example, if the user drags a finger across a screen, the <xref:System.Windows.Input.ManipulationDelta> event occurs multiple times as the finger moves.</span></span> <span data-ttu-id="7e3e5-129">ユーザーが画面で、指を発生させた、<xref:System.Windows.Input.ManipulationDelta>慣性をシミュレートするためにイベントが発生し続けます。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-129">When the user raises a finger from the screen, the <xref:System.Windows.Input.ManipulationDelta> event keeps occurring to simulate inertia.</span></span>  
  
     <span data-ttu-id="7e3e5-130">コードが適用されます、<xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A>を<xref:System.Windows.UIElement.RenderTransform%2A>の<xref:System.Windows.Shapes.Rectangle>ユーザーは、タッチを移動すると移動する入力します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-130">The code applies the <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> to the <xref:System.Windows.UIElement.RenderTransform%2A> of the <xref:System.Windows.Shapes.Rectangle> to move it as the user moves the touch input.</span></span> <span data-ttu-id="7e3e5-131">またを確認するかどうか、<xref:System.Windows.Shapes.Rectangle>の境界外または、<xref:System.Windows.Window>慣性中に、イベントの発生します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-131">It also checks whether the <xref:System.Windows.Shapes.Rectangle> is outside the bounds of the <xref:System.Windows.Window> when the event occurs during inertia.</span></span> <span data-ttu-id="7e3e5-132">そのため、アプリケーションを呼び出す場合、<xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType>メソッドを操作を終了します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-132">If so, the application calls the <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> method to end the manipulation.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  <span data-ttu-id="7e3e5-133">`MainWindow`クラス、次の追加<xref:System.Windows.UIElement.ManipulationInertiaStarting>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-133">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationInertiaStarting> event handler.</span></span>  
  
     <span data-ttu-id="7e3e5-134"><xref:System.Windows.UIElement.ManipulationInertiaStarting>イベント、ユーザーが画面からのすべての指を発生させるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-134">The <xref:System.Windows.UIElement.ManipulationInertiaStarting> event occurs when the user raises all fingers from the screen.</span></span> <span data-ttu-id="7e3e5-135">コードでは、初期速度と、移動、拡張、および四角形の回転の減速を設定します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-135">The code sets the initial velocity and deceleration for the movement, expansion, and rotation of the rectangle.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  <span data-ttu-id="7e3e5-136">プロジェクトをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-136">Build and run the project.</span></span>  
  
     <span data-ttu-id="7e3e5-137">ウィンドウに表示される赤い四角形が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-137">You should see a red square appear in the window.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="7e3e5-138">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="7e3e5-138">Testing the Application</span></span>  
 <span data-ttu-id="7e3e5-139">アプリケーションをテストするには、次の操作を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-139">To test the application, try the following manipulations.</span></span> <span data-ttu-id="7e3e5-140">複数の次のいずれか、同時に実行できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-140">Note that you can do more than one of the following at the same time.</span></span>  
  
-   <span data-ttu-id="7e3e5-141">移動する、 <xref:System.Windows.Shapes.Rectangle>、に指を置き、<xref:System.Windows.Shapes.Rectangle>し、画面上で指を移動します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-141">To move the <xref:System.Windows.Shapes.Rectangle>, put a finger on the <xref:System.Windows.Shapes.Rectangle> and move the finger across the screen.</span></span>  
  
-   <span data-ttu-id="7e3e5-142">サイズを変更する、 <xref:System.Windows.Shapes.Rectangle>、2 本の指の電源を入れます、<xref:System.Windows.Shapes.Rectangle>して近い一緒にまたは遠く互いとは別に、指を移動します。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-142">To resize the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and move the fingers closer together or farther apart from each other.</span></span>  
  
-   <span data-ttu-id="7e3e5-143">回転する、 <xref:System.Windows.Shapes.Rectangle>、2 本の指の電源を入れます、<xref:System.Windows.Shapes.Rectangle>指が互いの周りの回転とします。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-143">To rotate the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and rotate the fingers around each other.</span></span>  
  
 <span data-ttu-id="7e3e5-144">慣性の直前の操作を実行するとは、指を画面からすばやくを発生させます。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-144">To cause inertia, quickly raise your fingers from the screen as you perform the previous manipulations.</span></span> <span data-ttu-id="7e3e5-145"><xref:System.Windows.Shapes.Rectangle>移動、サイズ変更、または停止する前に、数秒回転し続けます。</span><span class="sxs-lookup"><span data-stu-id="7e3e5-145">The <xref:System.Windows.Shapes.Rectangle> will continue to move, resize, or rotate for a few seconds before it stops.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3e5-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e3e5-146">See Also</span></span>  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>
