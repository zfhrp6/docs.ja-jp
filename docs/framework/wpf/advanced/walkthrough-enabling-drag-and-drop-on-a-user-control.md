---
title: "チュートリアル: ユーザー コントロールでのドラッグ アンド ドロップの有効化"
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
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 360b453b2a25b6822485f18cc81cb43e313949eb
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="00391-102">チュートリアル: ユーザー コントロールでのドラッグ アンド ドロップの有効化</span><span class="sxs-lookup"><span data-stu-id="00391-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>
<span data-ttu-id="00391-103">このチュートリアルでのドラッグ アンド ドロップのデータ転送に含めることができるカスタム ユーザー コントロールを作成する方法を示します[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="00391-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="00391-104">このチュートリアルでは、カスタムの WPF を作成します<xref:System.Windows.Controls.UserControl>を表す円を選択します。</span><span class="sxs-lookup"><span data-stu-id="00391-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="00391-105">ドラッグ アンド ドロップ経由のデータ転送を有効にするコントロールの機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="00391-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="00391-106">たとえば、別に 1 つの円コントロールからドラッグした場合の塗りつぶしの色データがソースからコピー、円ターゲットにします。</span><span class="sxs-lookup"><span data-stu-id="00391-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="00391-107">円コントロールからドラッグした場合、 <xref:System.Windows.Controls.TextBox>、塗りつぶしの色の文字列形式にコピー、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="00391-108">2 つのパネル コントロールが含まれた小さなアプリケーションを作成することも、および<xref:System.Windows.Controls.TextBox>ドラッグ アンド ドロップ機能をテストします。</span><span class="sxs-lookup"><span data-stu-id="00391-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="00391-109">移動または 1 つのパネルの子のコレクションから、他の円をコピーすることができますが、削除された円のデータを処理するパネルをできるようにするコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="00391-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>  
  
 <span data-ttu-id="00391-110">このチュートリアルでは、次の作業について説明します。</span><span class="sxs-lookup"><span data-stu-id="00391-110">This walkthrough illustrates the following tasks:</span></span>  
  
-   <span data-ttu-id="00391-111">カスタム ユーザー コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="00391-111">Create a custom user control.</span></span>  
  
-   <span data-ttu-id="00391-112">ドラッグ元であるユーザー コントロールを有効にします。</span><span class="sxs-lookup"><span data-stu-id="00391-112">Enable the user control to be a drag source.</span></span>  
  
-   <span data-ttu-id="00391-113">ドロップ ターゲットにするユーザー コントロールを有効にします。</span><span class="sxs-lookup"><span data-stu-id="00391-113">Enable the user control to be a drop target.</span></span>  
  
-   <span data-ttu-id="00391-114">ユーザー コントロールから削除されるデータを受信するパネルを有効にします。</span><span class="sxs-lookup"><span data-stu-id="00391-114">Enable a panel to receive data dropped from the user control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="00391-115">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="00391-115">Prerequisites</span></span>  
 <span data-ttu-id="00391-116">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="00391-116">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="00391-117">Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="00391-117">Visual Studio 2010</span></span>  
  
## <a name="creating-the-application-project"></a><span data-ttu-id="00391-118">アプリケーション プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="00391-118">Creating the Application Project</span></span>  
 <span data-ttu-id="00391-119">このセクションでは、2 つのパネルでのメイン ページが含まれるアプリケーション インフラストラクチャを作成します、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
### <a name="to-create-the-project"></a><span data-ttu-id="00391-120">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="00391-120">To create the project</span></span>  
  
1.  <span data-ttu-id="00391-121">Visual Basic または Visual c# のという名前の新しい WPF アプリケーション プロジェクトを作成する`DragDropExample`です。</span><span class="sxs-lookup"><span data-stu-id="00391-121">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="00391-122">詳細については、次を参照してください。[する方法: 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)です。</span><span class="sxs-lookup"><span data-stu-id="00391-122">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="00391-123">MainWindow.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-123">Open MainWindow.xaml.</span></span>  
  
3.  <span data-ttu-id="00391-124">開始タグと終了の間で、次のマークアップを追加<xref:System.Windows.Controls.Grid>タグ。</span><span class="sxs-lookup"><span data-stu-id="00391-124">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>  
  
     <span data-ttu-id="00391-125">このマークアップでは、テスト アプリケーションのユーザー インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="00391-125">This markup creates the user interface for the test application.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a><span data-ttu-id="00391-126">プロジェクトに新しいユーザー コントロールの追加</span><span class="sxs-lookup"><span data-stu-id="00391-126">Adding a New User Control to the Project</span></span>  
 <span data-ttu-id="00391-127">このセクションでは、プロジェクトに新しいユーザー コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="00391-127">In this section, you will add a new user control to the project.</span></span>  
  
### <a name="to-add-a-new-user-control"></a><span data-ttu-id="00391-128">新しいユーザー コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="00391-128">To add a new user control</span></span>  
  
1.  <span data-ttu-id="00391-129">[プロジェクト] メニューで、次のように選択します。**ユーザー コントロールの追加**です。</span><span class="sxs-lookup"><span data-stu-id="00391-129">On the Project menu, select **Add User Control**.</span></span>  
  
2.  <span data-ttu-id="00391-130">新しい項目の追加 ダイアログ ボックスに名前を変更`Circle.xaml`、 をクリック**追加**です。</span><span class="sxs-lookup"><span data-stu-id="00391-130">In the Add New Item dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>  
  
     <span data-ttu-id="00391-131">Circle.xaml とその分離コードは、プロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="00391-131">Circle.xaml and its code-behind is added to the project.</span></span>  
  
3.  <span data-ttu-id="00391-132">Circle.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-132">Open Circle.xaml.</span></span>  
  
     <span data-ttu-id="00391-133">このファイルは、ユーザー コントロールのユーザー インターフェイス要素が格納されます。</span><span class="sxs-lookup"><span data-stu-id="00391-133">This file will contain the user interface elements of the user control.</span></span>  
  
4.  <span data-ttu-id="00391-134">ルートに、次のマークアップを追加<xref:System.Windows.Controls.Grid>UI として青い円形のある単純なユーザー コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="00391-134">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  <span data-ttu-id="00391-135">Circle.xaml.cs または Circle.xaml.vb を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-135">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
6.  <span data-ttu-id="00391-136">C# の場合は、既定のコンス トラクターとコピー コンス トラクターを作成した後、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="00391-136">In C#, add the following code after the default constructor to create a copy constructor.</span></span> <span data-ttu-id="00391-137">Visual basic では、既定のコンス トラクターとコピー コンス トラクターの両方を作成するには、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="00391-137">In Visual Basic, add the following code to create both a default constructor and a copy constructor.</span></span>  
  
     <span data-ttu-id="00391-138">コピーするユーザー コントロールをできるようにするのには、分離コード ファイルにコピー コンス トラクター メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="00391-138">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="00391-139">簡略化された円のユーザー コントロールではのみ塗りつぶしおよびコピーのサイズ、ユーザー コントロールのです。</span><span class="sxs-lookup"><span data-stu-id="00391-139">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a><span data-ttu-id="00391-140">メイン ウィンドウにユーザー コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="00391-140">To add the user control to the main window</span></span>  
  
1.  <span data-ttu-id="00391-141">MainWindow.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-141">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="00391-142">次の XAML を開くときに追加<xref:System.Windows.Window>タグを現在のアプリケーションへの XML 名前空間参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="00391-142">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  <span data-ttu-id="00391-143">最初の<xref:System.Windows.Controls.StackPanel>、最初のパネルで、円のユーザー コントロールの 2 つのインスタンスを作成する次の XAML を追加します。</span><span class="sxs-lookup"><span data-stu-id="00391-143">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     <span data-ttu-id="00391-144">パネルのすべての XAML は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="00391-144">The full XAML for the panel looks like the following.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a><span data-ttu-id="00391-145">ユーザー コントロールでドラッグ ソース イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="00391-145">Implementing Drag Source Events in the User Control</span></span>  
 <span data-ttu-id="00391-146">上書きは、このセクションで、<xref:System.Windows.UIElement.OnMouseMove%2A>メソッドと、ドラッグ アンド ドロップ操作を開始します。</span><span class="sxs-lookup"><span data-stu-id="00391-146">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>  
  
 <span data-ttu-id="00391-147">場合は、ドラッグを開始 (マウス ボタンが押され、マウスを移動) に転送されるデータをパッケージ化は、<xref:System.Windows.DataObject>です。</span><span class="sxs-lookup"><span data-stu-id="00391-147">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="00391-148">ここでは、円コントロールはパッケージの 3 つのデータ項目塗りつぶしの色の高さの double 型の表現とそれ自体のコピーの文字列形式。</span><span class="sxs-lookup"><span data-stu-id="00391-148">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="00391-149">ドラッグ アンド ドロップ操作を開始するには</span><span class="sxs-lookup"><span data-stu-id="00391-149">To initiate a drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="00391-150">Circle.xaml.cs または Circle.xaml.vb を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-150">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="00391-151">次の追加<xref:System.Windows.UIElement.OnMouseMove%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.MouseMove>イベント。</span><span class="sxs-lookup"><span data-stu-id="00391-151">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     <span data-ttu-id="00391-152">これは、<xref:System.Windows.UIElement.OnMouseMove%2A>オーバーライドは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-152">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="00391-153">マウスの移動中に、マウスの左ボタンが押されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="00391-153">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>  
  
    -   <span data-ttu-id="00391-154">パッケージの円にデータを<xref:System.Windows.DataObject>です。</span><span class="sxs-lookup"><span data-stu-id="00391-154">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="00391-155">ここでは、次の 3 つのデータ項目のパッケージ円コントロール塗りつぶしの色の高さの double 型の表現とそれ自体のコピーの文字列形式。</span><span class="sxs-lookup"><span data-stu-id="00391-155">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
    -   <span data-ttu-id="00391-156">静的なを呼び出して<xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType>をドラッグ アンド ドロップ操作を開始するメソッド。</span><span class="sxs-lookup"><span data-stu-id="00391-156">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="00391-157">次の 3 つのパラメーターを渡す、<xref:System.Windows.DragDrop.DoDragDrop%2A>メソッド。</span><span class="sxs-lookup"><span data-stu-id="00391-157">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>  
  
        -   <span data-ttu-id="00391-158">`dragSource`– このコントロールへの参照。</span><span class="sxs-lookup"><span data-stu-id="00391-158">`dragSource` – A reference to this control.</span></span>  
  
        -   <span data-ttu-id="00391-159">`data`–<xref:System.Windows.DataObject>前のコードで作成します。</span><span class="sxs-lookup"><span data-stu-id="00391-159">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>  
  
        -   <span data-ttu-id="00391-160">`allowedEffects`– の許可されているドラッグ アンド ドロップ操作<xref:System.Windows.DragDropEffects.Copy>または<xref:System.Windows.DragDropEffects.Move>です。</span><span class="sxs-lookup"><span data-stu-id="00391-160">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="00391-161">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-161">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="00391-162">円コントロールのいずれかをクリックし、その他の円、パネル上にドラッグし、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-162">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="00391-163">ドラッグしたとき、<xref:System.Windows.Controls.TextBox>カーソルが移動を示すために変わります。</span><span class="sxs-lookup"><span data-stu-id="00391-163">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>  
  
5.  <span data-ttu-id="00391-164">経由で Circle をドラッグするときに、 <xref:System.Windows.Controls.TextBox>、CTRL キーを押します。</span><span class="sxs-lookup"><span data-stu-id="00391-164">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the CTRL key.</span></span> <span data-ttu-id="00391-165">コピーを示すために、カーソルがどのように変化するかに注意してください。</span><span class="sxs-lookup"><span data-stu-id="00391-165">Notice how the cursor changes to indicate a copy.</span></span>  
  
6.  <span data-ttu-id="00391-166">ドラッグ アンド ドロップ上の円、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-166">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="00391-167">円の塗りつぶしの色の文字列形式を追加、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-167">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
     <span data-ttu-id="00391-168">![Circle の塗りつぶしの色の文字列表現](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="00391-168">![String representation of Circle's fill color](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>  
  
 <span data-ttu-id="00391-169">既定では、カーソルは、データのドロップ効果が起こるかになりますを示すためにドラッグ アンド ドロップ操作中に変更されます。</span><span class="sxs-lookup"><span data-stu-id="00391-169">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="00391-170">処理することにより、ユーザーに指定されたフィードバックをカスタマイズすることができます、<xref:System.Windows.UIElement.GiveFeedback>イベントと異なるカーソルを設定します。</span><span class="sxs-lookup"><span data-stu-id="00391-170">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>  
  
### <a name="to-give-feedback-to-the-user"></a><span data-ttu-id="00391-171">ユーザーにフィードバックできる</span><span class="sxs-lookup"><span data-stu-id="00391-171">To give feedback to the user</span></span>  
  
1.  <span data-ttu-id="00391-172">Circle.xaml.cs または Circle.xaml.vb を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-172">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="00391-173">次の追加<xref:System.Windows.UIElement.OnGiveFeedback%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.GiveFeedback>イベント。</span><span class="sxs-lookup"><span data-stu-id="00391-173">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     <span data-ttu-id="00391-174">これは、<xref:System.Windows.UIElement.OnGiveFeedback%2A>オーバーライドは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-174">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="00391-175">チェック、<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>ドロップ ターゲットに設定されている値<xref:System.Windows.UIElement.DragOver>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="00391-175">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
    -   <span data-ttu-id="00391-176">基づくカスタム カーソル設定、<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>値。</span><span class="sxs-lookup"><span data-stu-id="00391-176">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="00391-177">カーソルはについてどのような影響がデータを削除するには、ユーザーに視覚的なフィードバックを提供するためのものです。</span><span class="sxs-lookup"><span data-stu-id="00391-177">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>  
  
3.  <span data-ttu-id="00391-178">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-178">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="00391-179">パネル、他の円を統制、円の 1 つをドラッグし、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-179">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="00391-180">カーソルがで指定したカスタムのカーソルでになっていることを確認、<xref:System.Windows.UIElement.OnGiveFeedback%2A>をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="00391-180">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>  
  
     <span data-ttu-id="00391-181">![カスタム カーソルによるドラッグ アンド ドロップ](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="00391-181">![Drag and drop with custom cursors](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>  
  
5.  <span data-ttu-id="00391-182">テキスト選択`green`から、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-182">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
6.  <span data-ttu-id="00391-183">ドラッグ、`green`円コントロールにテキストです。</span><span class="sxs-lookup"><span data-stu-id="00391-183">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="00391-184">既定のカーソルをドラッグ アンド ドロップ操作の効果を示すために表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="00391-184">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="00391-185">フィードバックのカーソルは、ドラッグ ソースが常に設定されます。</span><span class="sxs-lookup"><span data-stu-id="00391-185">The feedback cursor is always set by the drag source.</span></span>  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a><span data-ttu-id="00391-186">ユーザー コントロールにドロップ対象のイベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="00391-186">Implementing Drop Target Events in the User Control</span></span>  
 <span data-ttu-id="00391-187">このセクションでは、ユーザー コントロールがドロップ ターゲット、オーバーライドにより、ユーザーは、メソッドがドロップ ターゲットにするのに制御し、データの削除を処理を指定します。</span><span class="sxs-lookup"><span data-stu-id="00391-187">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="00391-188">ドロップ ターゲットにするユーザー コントロールを有効にするには</span><span class="sxs-lookup"><span data-stu-id="00391-188">To enable the user control to be a drop target</span></span>  
  
1.  <span data-ttu-id="00391-189">Circle.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-189">Open Circle.xaml.</span></span>  
  
2.  <span data-ttu-id="00391-190">開く際に<xref:System.Windows.Controls.UserControl>タグ、追加、<xref:System.Windows.UIElement.AllowDrop%2A>プロパティに設定し、`true`です。</span><span class="sxs-lookup"><span data-stu-id="00391-190">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <span data-ttu-id="00391-191"><xref:System.Windows.UIElement.OnDrop%2A>メソッドが呼び出されます、<xref:System.Windows.UIElement.AllowDrop%2A>プロパティに設定されている`true`円ユーザー コントロール、ドラッグ ソースからのデータが削除されるとします。</span><span class="sxs-lookup"><span data-stu-id="00391-191">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="00391-192">このメソッドでは、削除されたデータを処理し、データを円に適用します。</span><span class="sxs-lookup"><span data-stu-id="00391-192">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>  
  
### <a name="to-process-the-dropped-data"></a><span data-ttu-id="00391-193">削除されたデータを処理するには</span><span class="sxs-lookup"><span data-stu-id="00391-193">To process the dropped data</span></span>  
  
1.  <span data-ttu-id="00391-194">Circle.xaml.cs または Circle.xaml.vb を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-194">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="00391-195">次の追加<xref:System.Windows.UIElement.OnDrop%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.Drop>イベント。</span><span class="sxs-lookup"><span data-stu-id="00391-195">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     <span data-ttu-id="00391-196">これは、<xref:System.Windows.UIElement.OnDrop%2A>オーバーライドは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-196">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="00391-197">使用して、<xref:System.Windows.DataObject.GetDataPresent%2A>メソッドをドラッグしたデータに、文字列オブジェクトが含まれているかどうかは確認します。</span><span class="sxs-lookup"><span data-stu-id="00391-197">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>  
  
    -   <span data-ttu-id="00391-198">使用して、<xref:System.Windows.DataObject.GetData%2A>メソッドが存在する場合は、文字列データを抽出します。</span><span class="sxs-lookup"><span data-stu-id="00391-198">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>  
  
    -   <span data-ttu-id="00391-199">使用して、<xref:System.Windows.Media.BrushConverter>を文字列に変換しようとする、<xref:System.Windows.Media.Brush>です。</span><span class="sxs-lookup"><span data-stu-id="00391-199">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="00391-200">変換が成功した場合は、適用するブラシ、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>円コントロールの UI を提供します。</span><span class="sxs-lookup"><span data-stu-id="00391-200">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>  
  
    -   <span data-ttu-id="00391-201">マーク、<xref:System.Windows.UIElement.Drop>イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="00391-201">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="00391-202">このイベントを受け取るその他の要素は、円のユーザー コントロールにそれが処理されることが認識されるように処理済みとしては、ドロップ イベントをマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="00391-202">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>  
  
3.  <span data-ttu-id="00391-203">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-203">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="00391-204">テキスト選択`green`で、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-204">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="00391-205">円のコントロールにテキストをドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="00391-205">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="00391-206">円は、blue から緑色に変わります。</span><span class="sxs-lookup"><span data-stu-id="00391-206">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="00391-207">![ブラシに文字列を変換](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="00391-207">![Convert a string to a brush](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>  
  
6.  <span data-ttu-id="00391-208">テキスト入力`green`で、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-208">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="00391-209">テキスト選択`gre`で、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-209">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="00391-210">円コントロールにドラッグし、それをドロップします。</span><span class="sxs-lookup"><span data-stu-id="00391-210">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="00391-211">通知を削除可能ですが、円の色は変更されませんを示すために、カーソルが変化する`gre`は有効な色ではありません。</span><span class="sxs-lookup"><span data-stu-id="00391-211">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>  
  
9. <span data-ttu-id="00391-212">緑色の円コントロールからドラッグし、青の円コントロール上にドロップします。</span><span class="sxs-lookup"><span data-stu-id="00391-212">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="00391-213">円は、blue から緑色に変わります。</span><span class="sxs-lookup"><span data-stu-id="00391-213">The Circle changes from blue to green.</span></span> <span data-ttu-id="00391-214">カーソルが表示されるかどうかに依存する通知、<xref:System.Windows.Controls.TextBox>円は、ドラッグ ソースまたはします。</span><span class="sxs-lookup"><span data-stu-id="00391-214">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>  
  
 <span data-ttu-id="00391-215">設定、<xref:System.Windows.UIElement.AllowDrop%2A>プロパティを`true`要素をドロップ ターゲットを有効にするために必要なものがドロップされたデータを処理します。</span><span class="sxs-lookup"><span data-stu-id="00391-215">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="00391-216">ただしより優れたユーザー エクスペリエンスを提供する必要がありますも処理する、 <xref:System.Windows.UIElement.DragEnter>、 <xref:System.Windows.UIElement.DragLeave>、および<xref:System.Windows.UIElement.DragOver>イベント。</span><span class="sxs-lookup"><span data-stu-id="00391-216">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="00391-217">これらのイベントでは、チェックを実行し、データが削除される前に、ユーザーにその他のフィードバックを提供できます。</span><span class="sxs-lookup"><span data-stu-id="00391-217">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>  
  
 <span data-ttu-id="00391-218">円ユーザー コントロールの上のデータをドラッグすると場合、コントロールはドラッグされるデータを処理できるかどうか、ドラッグ ソースで通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00391-218">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="00391-219">コントロールがデータを処理する方法を知らない場合は、ドロップを拒否する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00391-219">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="00391-220">これを行うには処理、<xref:System.Windows.UIElement.DragOver>イベントとセット、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="00391-220">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="00391-221">データの削除が許可されていることを確認するには</span><span class="sxs-lookup"><span data-stu-id="00391-221">To verify that the data drop is allowed</span></span>  
  
1.  <span data-ttu-id="00391-222">Circle.xaml.cs または Circle.xaml.vb を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-222">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="00391-223">次の追加<xref:System.Windows.UIElement.OnDragOver%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.DragOver>イベント。</span><span class="sxs-lookup"><span data-stu-id="00391-223">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     <span data-ttu-id="00391-224">これは、<xref:System.Windows.UIElement.OnDragOver%2A>オーバーライドは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-224">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="00391-225"><xref:System.Windows.DragEventArgs.Effects%2A> プロパティを <xref:System.Windows.DragDropEffects.None> に設定します。</span><span class="sxs-lookup"><span data-stu-id="00391-225">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>  
  
    -   <span data-ttu-id="00391-226">実行される同じチェックを実行、<xref:System.Windows.UIElement.OnDrop%2A>円ユーザー コントロールがドラッグしたデータを処理できるかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="00391-226">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>  
  
    -   <span data-ttu-id="00391-227">ユーザー コントロールには、データを処理できますが、設定、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティを<xref:System.Windows.DragDropEffects.Copy>または<xref:System.Windows.DragDropEffects.Move>です。</span><span class="sxs-lookup"><span data-stu-id="00391-227">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="00391-228">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-228">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="00391-229">テキスト選択`gre`で、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-229">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="00391-230">円のコントロールにテキストをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="00391-230">Drag the text to a Circle control.</span></span> <span data-ttu-id="00391-231">カーソルは、ために、ボックスの一覧が使用できないことを示すために今すぐ変更通知`gre`は有効な色ではありません。</span><span class="sxs-lookup"><span data-stu-id="00391-231">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>  
  
 <span data-ttu-id="00391-232">さらに、drop 操作のプレビューを適用することにより、ユーザー エクスペリエンスを強化できます。</span><span class="sxs-lookup"><span data-stu-id="00391-232">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="00391-233">円ユーザー コントロールが無効にする、<xref:System.Windows.UIElement.OnDragEnter%2A>と<xref:System.Windows.UIElement.OnDragLeave%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="00391-233">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="00391-234">コントロールを現在の背景の上にデータをドラッグするときに<xref:System.Windows.Shapes.Shape.Fill%2A>はプレース ホルダー変数に保存します。</span><span class="sxs-lookup"><span data-stu-id="00391-234">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="00391-235">文字列は、ブラシに変換しに適用される、<xref:System.Windows.Shapes.Ellipse>円を提供する UI。</span><span class="sxs-lookup"><span data-stu-id="00391-235">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="00391-236">場合は、データがドロップされず、元の円外にドラッグされた<xref:System.Windows.Shapes.Shape.Fill%2A>値は、円を再適用します。</span><span class="sxs-lookup"><span data-stu-id="00391-236">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="00391-237">ドラッグ アンド ドロップ操作の効果をプレビューするには</span><span class="sxs-lookup"><span data-stu-id="00391-237">To preview the effects of the drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="00391-238">Circle.xaml.cs または Circle.xaml.vb を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-238">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="00391-239">円クラスで宣言プライベート<xref:System.Windows.Media.Brush>という名前の変数`_previousFill`し初期化`null`です。</span><span class="sxs-lookup"><span data-stu-id="00391-239">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  <span data-ttu-id="00391-240">次の追加<xref:System.Windows.UIElement.OnDragEnter%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.DragEnter>イベント。</span><span class="sxs-lookup"><span data-stu-id="00391-240">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     <span data-ttu-id="00391-241">これは、<xref:System.Windows.UIElement.OnDragEnter%2A>オーバーライドは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-241">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="00391-242">保存、<xref:System.Windows.Shapes.Shape.Fill%2A>のプロパティ、<xref:System.Windows.Shapes.Ellipse>で、`_previousFill`変数。</span><span class="sxs-lookup"><span data-stu-id="00391-242">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>  
  
    -   <span data-ttu-id="00391-243">実行される同じチェックを実行、<xref:System.Windows.UIElement.OnDrop%2A>にデータを変換できるかどうかを決定するメソッド、<xref:System.Windows.Media.Brush>です。</span><span class="sxs-lookup"><span data-stu-id="00391-243">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="00391-244">有効なデータが変換される場合<xref:System.Windows.Media.Brush>、それを適用、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>です。</span><span class="sxs-lookup"><span data-stu-id="00391-244">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
4.  <span data-ttu-id="00391-245">次の追加<xref:System.Windows.UIElement.OnDragLeave%2A>に対するクラス処理を提供する上書き、<xref:System.Windows.UIElement.DragLeave>イベント。</span><span class="sxs-lookup"><span data-stu-id="00391-245">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     <span data-ttu-id="00391-246">これは、<xref:System.Windows.UIElement.OnDragLeave%2A>オーバーライドは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-246">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="00391-247">適用される、<xref:System.Windows.Media.Brush>に保存されている、`_previousFill`変数を<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Ellipse>円ユーザー コントロールの UI を提供します。</span><span class="sxs-lookup"><span data-stu-id="00391-247">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>  
  
5.  <span data-ttu-id="00391-248">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-248">Press F5 to build and run the application.</span></span>  
  
6.  <span data-ttu-id="00391-249">テキスト選択`green`で、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-249">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="00391-250">円コントロールの上にドロップせず、テキストをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="00391-250">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="00391-251">円は、blue から緑色に変わります。</span><span class="sxs-lookup"><span data-stu-id="00391-251">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="00391-252">![ドラッグ &#45; の効果のプレビューおよび &#45; ドロップ](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="00391-252">![Preview the effects of a drag&#45;and&#45;drop operation](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>  
  
8.  <span data-ttu-id="00391-253">円コントロールのテキストをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="00391-253">Drag the text away from the Circle control.</span></span> <span data-ttu-id="00391-254">円を青に緑のバックアップから変更します。</span><span class="sxs-lookup"><span data-stu-id="00391-254">The Circle changes from green back to blue.</span></span>  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a><span data-ttu-id="00391-255">データを受信するパネルを有効にすると削除</span><span class="sxs-lookup"><span data-stu-id="00391-255">Enabling a Panel to Receive Dropped Data</span></span>  
 <span data-ttu-id="00391-256">このセクションでは、ドラッグしたデータのマークのドロップ ターゲットとして機能する円のユーザー コントロールをホストしているパネルを有効になります。</span><span class="sxs-lookup"><span data-stu-id="00391-256">In this section, you will enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="00391-257">使用すると、円を 1 つのパネルから、別に移動するか、CTRL キーを押しながらドラッグ アンド ドロップ、円、円のコントロールのコピーを作成するコードを実装します。</span><span class="sxs-lookup"><span data-stu-id="00391-257">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the CTRL key while dragging and dropping a Circle.</span></span>  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a><span data-ttu-id="00391-258">ドロップ ターゲットにするのには、パネルを有効にするには</span><span class="sxs-lookup"><span data-stu-id="00391-258">To enable the panel to be a drop target</span></span>  
  
1.  <span data-ttu-id="00391-259">MainWindow.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-259">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="00391-260">それぞれで、次の XAML のように、<xref:System.Windows.Controls.StackPanel>のハンドラーを追加、コントロール、<xref:System.Windows.UIElement.DragOver>と<xref:System.Windows.UIElement.Drop>イベント。</span><span class="sxs-lookup"><span data-stu-id="00391-260">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="00391-261">名前、<xref:System.Windows.UIElement.DragOver>イベント ハンドラー、 `panel_DragOver`、し、名前、<xref:System.Windows.UIElement.Drop>イベント ハンドラー、`panel_Drop`です。</span><span class="sxs-lookup"><span data-stu-id="00391-261">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  <span data-ttu-id="00391-262">MainWindows.xaml.cs または MainWindow.xaml.vb を開きます。</span><span class="sxs-lookup"><span data-stu-id="00391-262">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>  
  
4.  <span data-ttu-id="00391-263">次のコードを追加、<xref:System.Windows.UIElement.DragOver>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="00391-263">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     <span data-ttu-id="00391-264">これは、<xref:System.Windows.UIElement.DragOver>イベント ハンドラーは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-264">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="00391-265">ドラッグしたデータが内にパッケージ化された"Object"データを含むことを確認、<xref:System.Windows.DataObject>円ユーザー コントロールでの呼び出しで渡されると<xref:System.Windows.DragDrop.DoDragDrop%2A>です。</span><span class="sxs-lookup"><span data-stu-id="00391-265">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>  
  
    -   <span data-ttu-id="00391-266">「オブジェクト」のデータが存在する場合は、CTRL キーが押されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="00391-266">If the "Object" data is present, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="00391-267">CTRL キーが押された場合、設定、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティを<xref:System.Windows.DragDropEffects.Copy>です。</span><span class="sxs-lookup"><span data-stu-id="00391-267">If the CTRL key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="00391-268">それ以外の場合、設定、<xref:System.Windows.DragEventArgs.Effects%2A>プロパティを<xref:System.Windows.DragDropEffects.Move>です。</span><span class="sxs-lookup"><span data-stu-id="00391-268">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
5.  <span data-ttu-id="00391-269">次のコードを追加、<xref:System.Windows.UIElement.Drop>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="00391-269">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     <span data-ttu-id="00391-270">これは、<xref:System.Windows.UIElement.Drop>イベント ハンドラーは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-270">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="00391-271">チェックするかどうか、<xref:System.Windows.UIElement.Drop>イベントは既に処理されています。</span><span class="sxs-lookup"><span data-stu-id="00391-271">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="00391-272">たとえば、別の円が削除された場合の円をハンドル、<xref:System.Windows.UIElement.Drop>イベント、たくないもそれを処理する円を格納しているパネルです。</span><span class="sxs-lookup"><span data-stu-id="00391-272">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>  
  
    -   <span data-ttu-id="00391-273">場合、<xref:System.Windows.UIElement.Drop>イベントが処理されない、チェック、CTRL キーが押されたかどうか。</span><span class="sxs-lookup"><span data-stu-id="00391-273">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="00391-274">CTRL キーが押された場合、<xref:System.Windows.UIElement.Drop>発生、円のコピーを制御およびそれを追加、<xref:System.Windows.Controls.Panel.Children%2A>のコレクション、<xref:System.Windows.Controls.StackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="00391-274">If the CTRL key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
    -   <span data-ttu-id="00391-275">CTRL キーが押されていない場合から円を移動、<xref:System.Windows.Controls.Panel.Children%2A>をその親パネルのコレクション、<xref:System.Windows.Controls.Panel.Children%2A>時に削除されましたが、パネルのコレクション。</span><span class="sxs-lookup"><span data-stu-id="00391-275">If the CTRL key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>  
  
    -   <span data-ttu-id="00391-276">セット、<xref:System.Windows.DragEventArgs.Effects%2A>に通知するプロパティ、<xref:System.Windows.DragDrop.DoDragDrop%2A>メソッド移動またはコピー操作が実行されたかどうか。</span><span class="sxs-lookup"><span data-stu-id="00391-276">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>  
  
6.  <span data-ttu-id="00391-277">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="00391-277">Press F5 to build and run the application.</span></span>  
  
7.  <span data-ttu-id="00391-278">テキスト選択`green`から、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="00391-278">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="00391-279">円コントロール上でテキストをドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="00391-279">Drag the text over a Circle control and drop it.</span></span>  
  
9. <span data-ttu-id="00391-280">左側のパネルから、右側のパネルを円コントロールをドラッグし、ドロップします。</span><span class="sxs-lookup"><span data-stu-id="00391-280">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="00391-281">円はから削除、<xref:System.Windows.Controls.Panel.Children%2A>左側のパネルのコレクションと、右側のパネルの子のコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="00391-281">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>  
  
10. <span data-ttu-id="00391-282">もう一方のパネルにはパネルから円コントロールをドラッグし、CTRL キーを押しながらにドロップします。</span><span class="sxs-lookup"><span data-stu-id="00391-282">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the CTRL key.</span></span> <span data-ttu-id="00391-283">円がコピーされ、コピーに追加されます、<xref:System.Windows.Controls.Panel.Children%2A>受信側のパネルのコレクション。</span><span class="sxs-lookup"><span data-stu-id="00391-283">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>  
  
     <span data-ttu-id="00391-284">![CTRL キーを押しながら Circle をドラッグ](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="00391-284">![Dragging a Circle while pressing the CTRL key](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00391-285">関連項目</span><span class="sxs-lookup"><span data-stu-id="00391-285">See Also</span></span>  
 [<span data-ttu-id="00391-286">ドラッグ アンド ドロップの概要</span><span class="sxs-lookup"><span data-stu-id="00391-286">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
