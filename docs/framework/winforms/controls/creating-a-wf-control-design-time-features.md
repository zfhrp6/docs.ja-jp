---
title: "チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
caps.latest.revision: "46"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4e84c665897159d08cec36b0f35b4f5f2674445
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-a-windows-forms-control-that-takes-advantage-of-visual-studio-design-time-features"></a><span data-ttu-id="41784-102">チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="41784-102">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>
<span data-ttu-id="41784-103">関連付けられているカスタム デザイナーを作成して、カスタム コントロールのデザイン時機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="41784-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>  
  
 <span data-ttu-id="41784-104">このチュートリアルでは、カスタム コントロールのカスタム デザイナーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="41784-104">This walkthrough illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="41784-105">実装、`MarqueeControl`型およびと呼ばれる、関連付けられたデザイナー クラス`MarqueeControlRootDesigner`です。</span><span class="sxs-lookup"><span data-stu-id="41784-105">You will implement a `MarqueeControl` type and an associated designer class, called `MarqueeControlRootDesigner`.</span></span>  
  
 <span data-ttu-id="41784-106">`MarqueeControl`アニメーションと点滅しているテキストのシアター marquee ような表示を実装しています。</span><span class="sxs-lookup"><span data-stu-id="41784-106">The `MarqueeControl` type implements a display similar to a theater marquee, with animated lights and flashing text.</span></span>  
  
 <span data-ttu-id="41784-107">このコントロールのデザイナーは、カスタム デザイン時のエクスペリエンスを提供するデザイン環境とやり取りします。</span><span class="sxs-lookup"><span data-stu-id="41784-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="41784-108">カスタム デザイナーを使用するカスタムをアセンブルできます`MarqueeControl`アニメーションと多くの組み合わせで点滅しているテキストを使用して実装します。</span><span class="sxs-lookup"><span data-stu-id="41784-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="41784-109">アセンブルされたコントロールは、他の Windows フォーム コントロールと同様に、フォームを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="41784-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>  
  
 <span data-ttu-id="41784-110">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="41784-110">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="41784-111">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="41784-111">Creating the Project</span></span>  
  
-   <span data-ttu-id="41784-112">コントロール ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-112">Creating a Control Library Project</span></span>  
  
-   <span data-ttu-id="41784-113">カスタム コントロール プロジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="41784-113">Referencing the Custom Control Project</span></span>  
  
-   <span data-ttu-id="41784-114">カスタム コントロールとそのカスタム デザイナーを定義します。</span><span class="sxs-lookup"><span data-stu-id="41784-114">Defining a Custom Control and Its Custom Designer</span></span>  
  
-   <span data-ttu-id="41784-115">カスタム コントロールのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-115">Creating an Instance of Your Custom Control</span></span>  
  
-   <span data-ttu-id="41784-116">デザイン時デバッグのためのプロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="41784-116">Setting Up the Project for Design-Time Debugging</span></span>  
  
-   <span data-ttu-id="41784-117">カスタム コントロールの実装</span><span class="sxs-lookup"><span data-stu-id="41784-117">Implementing Your Custom Control</span></span>  
  
-   <span data-ttu-id="41784-118">カスタム コントロールの子コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="41784-118">Creating a Child Control for Your Custom Control</span></span>  
  
-   <span data-ttu-id="41784-119">MarqueeBorder 子コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-119">Create the MarqueeBorder Child Control</span></span>  
  
-   <span data-ttu-id="41784-120">シャドウとフィルターのプロパティにカスタム デザイナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-120">Creating a Custom Designer to Shadow and Filter Properties</span></span>  
  
-   <span data-ttu-id="41784-121">コンポーネントの変更の処理</span><span class="sxs-lookup"><span data-stu-id="41784-121">Handling Component Changes</span></span>  
  
-   <span data-ttu-id="41784-122">カスタム デザイナー動詞を追加します。</span><span class="sxs-lookup"><span data-stu-id="41784-122">Adding Designer Verbs to your Custom Designer</span></span>  
  
-   <span data-ttu-id="41784-123">カスタム</span><span class="sxs-lookup"><span data-stu-id="41784-123">Creating a Custom UITypeEditor</span></span>  
  
-   <span data-ttu-id="41784-124">デザイナーでカスタム コントロールのテスト</span><span class="sxs-lookup"><span data-stu-id="41784-124">Testing your Custom Control in the Designer</span></span>  
  
 <span data-ttu-id="41784-125">完了したら、カスタム コントロールは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="41784-125">When you are finished, your custom control will look something like the following:</span></span>  
  
 <span data-ttu-id="41784-126">![可能な MarqueeControl 配置](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "により")</span><span class="sxs-lookup"><span data-stu-id="41784-126">![A possible MarqueeControl arrangement](../../../../docs/framework/winforms/controls/media/demomarqueecontrol.gif "DemoMarqueeControl")</span></span>  
  
 <span data-ttu-id="41784-127">完全なコード リストを参照してください。[する方法:、Windows フォーム コントロールを受け取る利点のデザイン時機能の作成](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)です。</span><span class="sxs-lookup"><span data-stu-id="41784-127">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41784-128">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="41784-128">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="41784-129">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41784-129">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="41784-130">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41784-130">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="41784-131">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="41784-131">Prerequisites</span></span>  
 <span data-ttu-id="41784-132">このチュートリアルを完了するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="41784-132">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="41784-133">作成し、Visual Studio がインストールされているコンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="41784-133">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="41784-134">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="41784-134">Creating the Project</span></span>  
 <span data-ttu-id="41784-135">最初の手順では、アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-135">The first step is to create the application project.</span></span> <span data-ttu-id="41784-136">このプロジェクトを使用するカスタム コントロールをホストするアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="41784-136">You will use this project to build the application that hosts the custom control.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="41784-137">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="41784-137">To create the project</span></span>  
  
-   <span data-ttu-id="41784-138">「ためです」と呼ばれる Windows フォーム アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-138">Create a Windows Forms Application project called "MarqueeControlTest."</span></span> <span data-ttu-id="41784-139">詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41784-139">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
## <a name="creating-a-control-library-project"></a><span data-ttu-id="41784-140">コントロール ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-140">Creating a Control Library Project</span></span>  
 <span data-ttu-id="41784-141">次の手順では、コントロール ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-141">The next step is to create the control library project.</span></span> <span data-ttu-id="41784-142">新しいカスタム コントロールとその対応するカスタム デザイナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-142">You will create a new custom control and its corresponding custom designer.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="41784-143">コントロール ライブラリ プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="41784-143">To create the control library project</span></span>  
  
1.  <span data-ttu-id="41784-144">Windows フォーム コントロール ライブラリ プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="41784-144">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="41784-145">プロジェクト「に」の名前します。</span><span class="sxs-lookup"><span data-stu-id="41784-145">Name the project "MarqueeControlLibrary."</span></span>  
  
2.  <span data-ttu-id="41784-146">使用して**ソリューション エクスプ ローラー**、選択した言語に応じて"UserControl1.cs"または"UserControl1.vb"をという名前のソース ファイルを削除して、プロジェクトの既定のコントロールを削除します。</span><span class="sxs-lookup"><span data-stu-id="41784-146">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span> <span data-ttu-id="41784-147">詳細については、次を参照してください。 [NIB: 方法:: 削除、削除、および項目の除外](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73)です。</span><span class="sxs-lookup"><span data-stu-id="41784-147">For more information, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
3.  <span data-ttu-id="41784-148">新しい<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlLibrary`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-148">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="41784-149">新しいソース ファイル"MarqueeControl"の基本の名前を付けます</span><span class="sxs-lookup"><span data-stu-id="41784-149">Give the new source file a base name of "MarqueeControl."</span></span>  
  
4.  <span data-ttu-id="41784-150">使用して**ソリューション エクスプ ローラー**で新しいフォルダーを作成、`MarqueeControlLibrary`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-150">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="41784-151">詳細については、次を参照してください。 [NIB: 方法: 新しいプロジェクト項目の追加](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)です。</span><span class="sxs-lookup"><span data-stu-id="41784-151">For more information, see [NIB:How to: Add New Project Items](http://msdn.microsoft.com/library/63d3e16b-de6e-4bb5-a0e3-ecec762201ce).</span></span> <span data-ttu-id="41784-152">新しいフォルダーの名前を""設計します。</span><span class="sxs-lookup"><span data-stu-id="41784-152">Name the new folder "Design."</span></span>  
  
5.  <span data-ttu-id="41784-153">右クリックし、**デザイン**フォルダーと、新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="41784-153">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="41784-154">ソース ファイル「ここでします」の基本の名前を付けます</span><span class="sxs-lookup"><span data-stu-id="41784-154">Give the source file a base name of "MarqueeControlRootDesigner."</span></span>  
  
6.  <span data-ttu-id="41784-155">System.Design アセンブリから型を使用して、この参照を追加する必要があります、`MarqueeControlLibrary`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-155">You will need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41784-156">System.Design アセンブリを使用するのには、プロジェクトは .NET Framework クライアント プロファイルではなく、.NET Framework の完全バージョンを対象する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41784-156">To use the System.Design assembly, your project must target the full version of the .NET Framework, not the .NET Framework Client Profile.</span></span> <span data-ttu-id="41784-157">ターゲット フレームワークを変更するを参照してください。[する方法: .NET Framework のバージョンを対象に](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)です。</span><span class="sxs-lookup"><span data-stu-id="41784-157">To change the target framework, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>  
  
## <a name="referencing-the-custom-control-project"></a><span data-ttu-id="41784-158">カスタム コントロール プロジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="41784-158">Referencing the Custom Control Project</span></span>  
 <span data-ttu-id="41784-159">使用して、`MarqueeControlTest`プロジェクトにカスタム コントロールをテストします。</span><span class="sxs-lookup"><span data-stu-id="41784-159">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="41784-160">プロジェクト参照を追加すると、テスト プロジェクトにカスタム コントロールを認識なります、`MarqueeControlLibrary`アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="41784-160">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>  
  
#### <a name="to-reference-the-custom-control-project"></a><span data-ttu-id="41784-161">カスタム コントロール プロジェクトを参照するには</span><span class="sxs-lookup"><span data-stu-id="41784-161">To reference the custom control project</span></span>  
  
-   <span data-ttu-id="41784-162">`MarqueeControlTest`プロジェクト、プロジェクト参照を追加、`MarqueeControlLibrary`アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="41784-162">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="41784-163">使用してください、**プロジェクト** タブで、**参照の追加** ダイアログ ボックスを参照するのではなく、`MarqueeControlLibrary`直接アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="41784-163">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>  
  
## <a name="defining-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="41784-164">カスタム コントロールとそのカスタム デザイナーを定義します。</span><span class="sxs-lookup"><span data-stu-id="41784-164">Defining a Custom Control and Its Custom Designer</span></span>  
 <span data-ttu-id="41784-165">カスタム コントロールの継承元、<xref:System.Windows.Forms.UserControl>クラスです。</span><span class="sxs-lookup"><span data-stu-id="41784-165">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="41784-166">これにより、他のコントロールを格納する、制御でき、コントロールの既定の機能が大幅に向上できます。</span><span class="sxs-lookup"><span data-stu-id="41784-166">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>  
  
 <span data-ttu-id="41784-167">カスタム コントロールは、関連するカスタム デザイナーがあります。</span><span class="sxs-lookup"><span data-stu-id="41784-167">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="41784-168">これにより、カスタム コントロールに特化した独自のデザイン エクスペリエンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="41784-168">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>  
  
 <span data-ttu-id="41784-169">使用して、コントロールをそのデザイナーを関連付ける、<xref:System.ComponentModel.DesignerAttribute>クラスです。</span><span class="sxs-lookup"><span data-stu-id="41784-169">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="41784-170">カスタム デザイナーの実装は、カスタム コントロールの全体のデザイン時の動作を開発しているため、<xref:System.ComponentModel.Design.IRootDesigner>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="41784-170">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>  
  
#### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="41784-171">カスタム コントロールとそのカスタム デザイナーを定義するには</span><span class="sxs-lookup"><span data-stu-id="41784-171">To define a custom control and its custom designer</span></span>  
  
1.  <span data-ttu-id="41784-172">開く、`MarqueeControl`内のソース ファイル、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="41784-172">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="41784-173">ファイルの上部には、次の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="41784-173">At the top of the file, import the following namespaces:</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]  
  
2.  <span data-ttu-id="41784-174">追加、<xref:System.ComponentModel.DesignerAttribute>を`MarqueeControl`クラス宣言します。</span><span class="sxs-lookup"><span data-stu-id="41784-174">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="41784-175">これは、そのデザイナーをカスタム コントロールを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="41784-175">This associates the custom control with its designer.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]  
  
3.  <span data-ttu-id="41784-176">開く、`MarqueeControlRootDesigner`内のソース ファイル、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="41784-176">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="41784-177">ファイルの上部には、次の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="41784-177">At the top of the file, import the following namespaces:</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]  
  
4.  <span data-ttu-id="41784-178">宣言を変更する`MarqueeControlRootDesigner`から継承する、<xref:System.Windows.Forms.Design.DocumentDesigner>クラスです。</span><span class="sxs-lookup"><span data-stu-id="41784-178">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="41784-179">適用、<xref:System.ComponentModel.ToolboxItemFilterAttribute>デザイナー対話方式を指定する、**ツールボックス**です。</span><span class="sxs-lookup"><span data-stu-id="41784-179">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>  
  
     <span data-ttu-id="41784-180">**注**の定義、`MarqueeControlRootDesigner`クラスは、"MarqueeControlLibrary.Design"と呼ばれる名前空間で囲まれています。</span><span class="sxs-lookup"><span data-stu-id="41784-180">**Note** The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called "MarqueeControlLibrary.Design."</span></span> <span data-ttu-id="41784-181">この宣言にデザイナーが配置特別な名前空間型のデザインに関連するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="41784-181">This declaration places the designer in a special namespace reserved for design-related types.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]  
  
5.  <span data-ttu-id="41784-182">コンス トラクターを定義、`MarqueeControlRootDesigner`クラスです。</span><span class="sxs-lookup"><span data-stu-id="41784-182">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="41784-183">挿入、<xref:System.Diagnostics.Trace.WriteLine%2A>コンス トラクターの本体のステートメント。</span><span class="sxs-lookup"><span data-stu-id="41784-183">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="41784-184">これは、デバッグのために便利になります。</span><span class="sxs-lookup"><span data-stu-id="41784-184">This will be useful for debugging purposes.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]  
  
## <a name="creating-an-instance-of-your-custom-control"></a><span data-ttu-id="41784-185">カスタム コントロールのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-185">Creating an Instance of Your Custom Control</span></span>  
 <span data-ttu-id="41784-186">フォームにコントロールのインスタンスを配置するカスタム コントロールのデザイン時動作を観察する`MarqueeControlTest`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-186">To observe the custom design-time behavior of your control, you will place an instance of your control on the form in `MarqueeControlTest` project.</span></span>  
  
#### <a name="to-create-an-instance-of-your-custom-control"></a><span data-ttu-id="41784-187">カスタム コントロールのインスタンスを作成するには</span><span class="sxs-lookup"><span data-stu-id="41784-187">To create an instance of your custom control</span></span>  
  
1.  <span data-ttu-id="41784-188">新しい<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlTest`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-188">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="41784-189">新しいソース ファイルの「により」ベースの名前を付けます</span><span class="sxs-lookup"><span data-stu-id="41784-189">Give the new source file a base name of "DemoMarqueeControl."</span></span>  
  
2.  <span data-ttu-id="41784-190">開く、`DemoMarqueeControl`ファイルで、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="41784-190">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="41784-191">ファイルの上部には、インポート、`MarqueeControlLibrary`名前空間。</span><span class="sxs-lookup"><span data-stu-id="41784-191">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>  
  
```vb  
Imports MarqueeControlLibrary  
```  
  
```csharp  
using MarqueeControlLibrary;  
```  
  
1.  <span data-ttu-id="41784-192">宣言を変更する`DemoMarqueeControl`から継承する、`MarqueeControl`クラスです。</span><span class="sxs-lookup"><span data-stu-id="41784-192">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>  
  
2.  <span data-ttu-id="41784-193">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="41784-193">Build the project.</span></span>  
  
3.  <span data-ttu-id="41784-194">Windows フォーム デザイナーで `Form1` を開きます。</span><span class="sxs-lookup"><span data-stu-id="41784-194">Open `Form1` in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="41784-195">検索、**ためコンポーネント** タブで、**ツールボックス**して開きます。</span><span class="sxs-lookup"><span data-stu-id="41784-195">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="41784-196">ドラッグ、`DemoMarqueeControl`から、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="41784-196">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>  
  
5.  <span data-ttu-id="41784-197">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="41784-197">Build the project.</span></span>  
  
## <a name="setting-up-the-project-for-design-time-debugging"></a><span data-ttu-id="41784-198">デザイン時デバッグのためのプロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="41784-198">Setting Up the Project for Design-Time Debugging</span></span>  
 <span data-ttu-id="41784-199">カスタム デザイン時機能を開発する際は、コントロールとコンポーネントをデバッグする必要があります。</span><span class="sxs-lookup"><span data-stu-id="41784-199">When you are developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="41784-200">デザイン時デバッグを許可する、プロジェクトを設定する簡単な方法があります。</span><span class="sxs-lookup"><span data-stu-id="41784-200">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="41784-201">詳細については、次を参照してください。[チュートリアル: デザイン時にカスタム Windows フォーム コントロールをデバッグ](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)です。</span><span class="sxs-lookup"><span data-stu-id="41784-201">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
#### <a name="to-set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="41784-202">デザイン時デバッグ用のプロジェクトを設定するには</span><span class="sxs-lookup"><span data-stu-id="41784-202">To set up the project for design-time debugging</span></span>  
  
1.  <span data-ttu-id="41784-203">右クリックし、`MarqueeControlLibrary`プロジェクトし、選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="41784-203">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="41784-204">"にプロパティ ページ ダイアログ ボックスで、選択、**デバッグ**ページ。</span><span class="sxs-lookup"><span data-stu-id="41784-204">In the "MarqueeControlLibrary Property Pages" dialog box, select the **Debug** page.</span></span>  
  
3.  <span data-ttu-id="41784-205">**開始動作**セクションで、**外部プログラムの開始**です。</span><span class="sxs-lookup"><span data-stu-id="41784-205">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="41784-206">できます、省略記号ボタンをクリックして、Visual Studio の別のインスタンスをデバッグ (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) を Visual Studio IDE の参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="41784-206">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="41784-207">実行可能ファイルの名前は、devenv.exe され、パスが %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe は既定の場所にインストールした場合。</span><span class="sxs-lookup"><span data-stu-id="41784-207">The name of the executable file is devenv.exe, and if you installed to the default location, its path is %programfiles%\Microsoft Visual Studio 9.0\Common7\IDE\devenv.exe.</span></span>  
  
4.  <span data-ttu-id="41784-208">ダイアログ ボックスを閉じるには、[ok] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="41784-208">Click OK to close the dialog box.</span></span>  
  
5.  <span data-ttu-id="41784-209">右クリックし、`MarqueeControlLibrary`プロジェクトし、「スタートアップ プロジェクトに」このデバッグ構成を有効にするを選択します。</span><span class="sxs-lookup"><span data-stu-id="41784-209">Right-click the `MarqueeControlLibrary` project and select "Set as StartUp Project" to enable this debugging configuration.</span></span>  
  
## <a name="checkpoint"></a><span data-ttu-id="41784-210">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="41784-210">Checkpoint</span></span>  
 <span data-ttu-id="41784-211">カスタム コントロールのデザイン時動作をデバッグする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="41784-211">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="41784-212">デバッグ環境が正しく設定されているを確認した後は、カスタム コントロールとカスタム デザイナー間の関連付けをテストします。</span><span class="sxs-lookup"><span data-stu-id="41784-212">Once you have determined that the debugging environment is set up correctly, you will test the association between the custom control and the custom designer.</span></span>  
  
#### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="41784-213">デバッグ環境と、デザイナーとの関連付けをテストするには</span><span class="sxs-lookup"><span data-stu-id="41784-213">To test the debugging environment and the designer association</span></span>  
  
1.  <span data-ttu-id="41784-214">開く、`MarqueeControlRootDesigner`内のソース ファイル、**コード エディター**にブレークポイントを配置し、<xref:System.Diagnostics.Trace.WriteLine%2A>ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="41784-214">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>  
  
2.  <span data-ttu-id="41784-215">F5 キーを押してデバッグ セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="41784-215">Press F5 to start the debugging session.</span></span> <span data-ttu-id="41784-216">Visual Studio の新しいインスタンスを作成することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="41784-216">Note that a new instance of Visual Studio is created.</span></span>  
  
3.  <span data-ttu-id="41784-217">Visual Studio の新しいインスタンスの「ため」ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="41784-217">In the new instance of Visual Studio, open the "MarqueeControlTest" solution.</span></span> <span data-ttu-id="41784-218">選択して、ソリューションを簡単に見つけることができます**最近使ったプロジェクト**から、**ファイル**メニュー。</span><span class="sxs-lookup"><span data-stu-id="41784-218">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="41784-219">最近使用したファイル、"MarqueeControlTest.sln"ソリューション ファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="41784-219">The "MarqueeControlTest.sln" solution file will be listed as the most recently used file.</span></span>  
  
4.  <span data-ttu-id="41784-220">開く、`DemoMarqueeControl`デザイナーでします。</span><span class="sxs-lookup"><span data-stu-id="41784-220">Open the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="41784-221">Visual Studio のデバッグのインスタンスがフォーカスを取得し、実行をブレークポイントで停止することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="41784-221">Note that the debugging instance of Visual Studio acquires focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="41784-222">F5 キーを押してデバッグ セッションを続行します。</span><span class="sxs-lookup"><span data-stu-id="41784-222">Press F5 to continue the debugging session.</span></span>  
  
 <span data-ttu-id="41784-223">この時点では、カスタム コントロールおよびその関連するカスタム デザイナーを開発、デバッグするためにすべてがされます。</span><span class="sxs-lookup"><span data-stu-id="41784-223">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="41784-224">このチュートリアルの残りの部分は、コントロールと、デザイナーの機能の実装の詳細に集中されます。</span><span class="sxs-lookup"><span data-stu-id="41784-224">The remainder of this walkthrough will concentrate on the details of implementing features of the control and the designer.</span></span>  
  
## <a name="implementing-your-custom-control"></a><span data-ttu-id="41784-225">カスタム コントロールの実装</span><span class="sxs-lookup"><span data-stu-id="41784-225">Implementing Your Custom Control</span></span>  
 <span data-ttu-id="41784-226">`MarqueeControl`は、<xref:System.Windows.Forms.UserControl>カスタマイズのほんの少しです。</span><span class="sxs-lookup"><span data-stu-id="41784-226">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="41784-227">2 つのメソッドを公開: `Start`、marquee アニメーションを開始し、`Stop`アニメーションは停止します。</span><span class="sxs-lookup"><span data-stu-id="41784-227">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="41784-228">`MarqueeControl`を実装する子コントロールが含まれています、`IMarqueeWidget`インターフェイス、`Start`と`Stop`各子コントロールと呼び出しの列挙、`StartMarquee`と`StopMarquee`メソッド、それぞれ、各子コントロール上実装する`IMarqueeWidget`です。</span><span class="sxs-lookup"><span data-stu-id="41784-228">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>  
  
 <span data-ttu-id="41784-229">外観、`MarqueeBorder`と`MarqueeText`コントロールは、レイアウトに依存するため、`MarqueeControl`よりも優先、<xref:System.Windows.Forms.Control.OnLayout%2A>メソッドと呼び出し<xref:System.Windows.Forms.Control.PerformLayout%2A>子コントロールをこの型のです。</span><span class="sxs-lookup"><span data-stu-id="41784-229">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>  
  
 <span data-ttu-id="41784-230">これは、程度、`MarqueeControl`カスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="41784-230">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="41784-231">によって実行時の機能が実装されている、`MarqueeBorder`と`MarqueeText`コントロール、およびデザイン時の機能によって実装される、`MarqueeBorderDesigner`と`MarqueeControlRootDesigner`クラスです。</span><span class="sxs-lookup"><span data-stu-id="41784-231">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>  
  
#### <a name="to-implement-your-custom-control"></a><span data-ttu-id="41784-232">カスタム コントロールを実装するには</span><span class="sxs-lookup"><span data-stu-id="41784-232">To implement your custom control</span></span>  
  
1.  <span data-ttu-id="41784-233">開く、`MarqueeControl`内のソース ファイル、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="41784-233">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="41784-234">実装、`Start`と`Stop`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="41784-234">Implement the `Start` and `Stop` methods.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]  
  
2.  <span data-ttu-id="41784-235"><xref:System.Windows.Forms.Control.OnLayout%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="41784-235">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]  
  
## <a name="creating-a-child-control-for-your-custom-control"></a><span data-ttu-id="41784-236">カスタム コントロールの子コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="41784-236">Creating a Child Control for Your Custom Control</span></span>  
 <span data-ttu-id="41784-237">`MarqueeControl` 2 種類の子コントロールをホストする:`MarqueeBorder`コントロールと`MarqueeText`コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-237">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>  
  
-   <span data-ttu-id="41784-238">`MarqueeBorder`: このコントロールは、"lights"の端の周りの境界線を描画します。</span><span class="sxs-lookup"><span data-stu-id="41784-238">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="41784-239">ライトは、境界線を移動するように表示されるように、シーケンスで点滅します。</span><span class="sxs-lookup"><span data-stu-id="41784-239">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="41784-240">ライトが点滅する速度がという名前のプロパティによって制御されます`UpdatePeriod`です。</span><span class="sxs-lookup"><span data-stu-id="41784-240">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="41784-241">その他のいくつかのカスタム プロパティは、コントロールの外観の他の側面を決定します。</span><span class="sxs-lookup"><span data-stu-id="41784-241">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="41784-242">2 つのメソッドと呼ばれる`StartMarquee`と`StopMarquee`、ときに、アニメーションの開始し、停止を制御します。</span><span class="sxs-lookup"><span data-stu-id="41784-242">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>  
  
-   <span data-ttu-id="41784-243">`MarqueeText`: このコントロールは、点滅している文字列を描画します。</span><span class="sxs-lookup"><span data-stu-id="41784-243">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="41784-244">同様に、`MarqueeBorder`コントロール、テキストが点滅速度は、によって制御されます、`UpdatePeriod`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="41784-244">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="41784-245">`MarqueeText`コントロールもあります、`StartMarquee`と`StopMarquee`と共通のメソッド、`MarqueeBorder`コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-245">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>  
  
 <span data-ttu-id="41784-246">デザイン時に、`MarqueeControlRootDesigner`これら 2 つのコントロール型に追加することができます、`MarqueeControl`の任意の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="41784-246">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>  
  
 <span data-ttu-id="41784-247">2 つのコントロールの共通機能を考慮と呼ばれるインターフェイス`IMarqueeWidget`です。</span><span class="sxs-lookup"><span data-stu-id="41784-247">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="41784-248">これにより、`MarqueeControl`を範囲に関連する子コントロールを検出し、特別な処理を付与します。</span><span class="sxs-lookup"><span data-stu-id="41784-248">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>  
  
 <span data-ttu-id="41784-249">定期的なアニメーション機能を実装するには、使用<xref:System.ComponentModel.BackgroundWorker>オブジェクトから、<xref:System.ComponentModel?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="41784-249">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="41784-250">使って<xref:System.Windows.Forms.Timer>が、オブジェクトが多`IMarqueeWidget`オブジェクトが存在、1 つの UI スレッドがアニメーションしきれないことができません。</span><span class="sxs-lookup"><span data-stu-id="41784-250">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>  
  
#### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="41784-251">カスタム コントロールの子コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="41784-251">To create a child control for your custom control</span></span>  
  
1.  <span data-ttu-id="41784-252">項目の追加、新しいクラス、`MarqueeControlLibrary`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-252">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="41784-253">新しいソース ファイル"IMarqueeWidget"の基本の名前を付けます</span><span class="sxs-lookup"><span data-stu-id="41784-253">Give the new source file a base name of "IMarqueeWidget."</span></span>  
  
2.  <span data-ttu-id="41784-254">開く、`IMarqueeWidget`内のソース ファイル、**コード エディター**から宣言を変更して`class`に`interface`:</span><span class="sxs-lookup"><span data-stu-id="41784-254">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]  
  
3.  <span data-ttu-id="41784-255">次のコードを追加、 `IMarqueeWidget` 2 つのメソッドと marquee アニメーションを操作するプロパティを公開するインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="41784-255">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]  
  
4.  <span data-ttu-id="41784-256">新しい**カスタム コントロールの**項目を`MarqueeControlLibrary`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-256">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="41784-257">新しいソース ファイル「ただし」の基本の名前を付けます</span><span class="sxs-lookup"><span data-stu-id="41784-257">Give the new source file a base name of "MarqueeText."</span></span>  
  
5.  <span data-ttu-id="41784-258">ドラッグ、<xref:System.ComponentModel.BackgroundWorker>のコンポーネント、**ツールボックス**上に、`MarqueeText`コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-258">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="41784-259">このコンポーネントを許可するが、`MarqueeText`自体を非同期的に更新するコントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-259">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>  
  
6.  <span data-ttu-id="41784-260">[プロパティ] ウィンドウで、設定、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの`WorkerReportsProgess`と<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="41784-260">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgess` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="41784-261">これらの設定により、<xref:System.ComponentModel.BackgroundWorker>を定期的に発生させるコンポーネント、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントと非同期更新をキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="41784-261">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="41784-262">詳細については、次を参照してください。 [BackgroundWorker コンポーネント](../../../../docs/framework/winforms/controls/backgroundworker-component.md)です。</span><span class="sxs-lookup"><span data-stu-id="41784-262">For more information, see [BackgroundWorker Component](../../../../docs/framework/winforms/controls/backgroundworker-component.md).</span></span>  
  
7.  <span data-ttu-id="41784-263">開く、`MarqueeText`内のソース ファイル、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="41784-263">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="41784-264">ファイルの上部には、次の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="41784-264">At the top of the file, import the following namespaces:</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]  
  
8.  <span data-ttu-id="41784-265">宣言を変更する`MarqueeText`から継承する<xref:System.Windows.Forms.Label>を実装して、`IMarqueeWidget`インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="41784-265">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]  
  
9. <span data-ttu-id="41784-266">公開されたプロパティに対応するインスタンス変数を宣言し、コンス トラクターで初期化します。</span><span class="sxs-lookup"><span data-stu-id="41784-266">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="41784-267">`isLit`フィールドかどうかをテキストで指定された色で描画する、`LightColor`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="41784-267">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]  
  
10. <span data-ttu-id="41784-268">`IMarqueeWidget` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="41784-268">Implement the `IMarqueeWidget` interface.</span></span>  
  
     <span data-ttu-id="41784-269">`StartMarquee`と`StopMarquee`メソッドを呼び出し、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>と<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>メソッドを開始し、アニメーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="41784-269">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>  
  
     <span data-ttu-id="41784-270"><xref:System.ComponentModel.CategoryAttribute.Category%2A>と<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>属性に適用されます、 `UpdatePeriod` 「範囲」と呼ばれる [プロパティ] ウィンドウのカスタム セクションに表示されるようにプロパティ</span><span class="sxs-lookup"><span data-stu-id="41784-270">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]  
  
11. <span data-ttu-id="41784-271">プロパティ アクセサーを実装します。</span><span class="sxs-lookup"><span data-stu-id="41784-271">Implement the property accessors.</span></span> <span data-ttu-id="41784-272">クライアントに 2 つのプロパティを公開する:`LightColor`と`DarkColor`です。</span><span class="sxs-lookup"><span data-stu-id="41784-272">You will expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="41784-273"><xref:System.ComponentModel.CategoryAttribute.Category%2A>と<xref:System.ComponentModel.BrowsableAttribute.Browsable%2A>属性は、「範囲」と呼ばれる [プロパティ] ウィンドウのカスタムのセクションでプロパティが表示されるので、これらのプロパティに適用されます</span><span class="sxs-lookup"><span data-stu-id="41784-273">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]  
  
12. <span data-ttu-id="41784-274">ハンドラーを実装、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。</span><span class="sxs-lookup"><span data-stu-id="41784-274">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>  
  
     <span data-ttu-id="41784-275"><xref:System.ComponentModel.BackgroundWorker.DoWork>ミリ秒で指定された数のイベント ハンドラーがスリープ状態`UpdatePeriod`を生成し、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントを呼び出すことによって、コードがアニメーションを停止するまで<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>です。</span><span class="sxs-lookup"><span data-stu-id="41784-275">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>  
  
     <span data-ttu-id="41784-276"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント ハンドラーは、テキストの点滅の外観、明暗の状態を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="41784-276">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]  
  
13. <span data-ttu-id="41784-277">上書き、<xref:System.Windows.Forms.Control.OnPaint%2A>アニメーションを有効にするメソッド。</span><span class="sxs-lookup"><span data-stu-id="41784-277">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]  
  
14. <span data-ttu-id="41784-278">F6 キーを押してソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="41784-278">Press F6 to build the solution.</span></span>  
  
## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="41784-279">MarqueeBorder 子コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-279">Create the MarqueeBorder Child Control</span></span>  
 <span data-ttu-id="41784-280">`MarqueeBorder`コントロールがやや高度な`MarqueeText`コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-280">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="41784-281">その他のプロパティとでのアニメーションがある、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは複雑です。</span><span class="sxs-lookup"><span data-stu-id="41784-281">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="41784-282">原則として、非常に似ていますが、`MarqueeText`コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-282">In principle, it is quite similar to the `MarqueeText` control.</span></span>  
  
 <span data-ttu-id="41784-283">`MarqueeBorder`コントロールで子コントロールを持つことができます、注意する必要がある<xref:System.Windows.Forms.Control.Layout>イベント。</span><span class="sxs-lookup"><span data-stu-id="41784-283">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>  
  
#### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="41784-284">MarqueeBorder コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="41784-284">To create the MarqueeBorder control</span></span>  
  
1.  <span data-ttu-id="41784-285">新しい**カスタム コントロールの**項目を`MarqueeControlLibrary`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-285">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="41784-286">新しいソース ファイル"MarqueeBorder"の基本の名前を付けます</span><span class="sxs-lookup"><span data-stu-id="41784-286">Give the new source file a base name of "MarqueeBorder."</span></span>  
  
2.  <span data-ttu-id="41784-287">ドラッグ、<xref:System.ComponentModel.BackgroundWorker>のコンポーネント、**ツールボックス**上に、`MarqueeBorder`コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-287">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="41784-288">このコンポーネントを許可するが、`MarqueeBorder`自体を非同期的に更新するコントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-288">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>  
  
3.  <span data-ttu-id="41784-289">[プロパティ] ウィンドウで、設定、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの`WorkerReportsProgess`と<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="41784-289">In the Properties window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgess` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span> <span data-ttu-id="41784-290">これらの設定により、<xref:System.ComponentModel.BackgroundWorker>を定期的に発生させるコンポーネント、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントと非同期更新をキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="41784-290">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="41784-291">詳細については、次を参照してください。 [BackgroundWorker コンポーネント](../../../../docs/framework/winforms/controls/backgroundworker-component.md)です。</span><span class="sxs-lookup"><span data-stu-id="41784-291">For more information, see [BackgroundWorker Component](../../../../docs/framework/winforms/controls/backgroundworker-component.md).</span></span>  
  
4.  <span data-ttu-id="41784-292">[プロパティ] ウィンドウで、イベント ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="41784-292">In the Properties window, click the Events button.</span></span> <span data-ttu-id="41784-293">ハンドラーのアタッチ、<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。</span><span class="sxs-lookup"><span data-stu-id="41784-293">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>  
  
5.  <span data-ttu-id="41784-294">開く、`MarqueeBorder`内のソース ファイル、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="41784-294">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="41784-295">ファイルの上部には、次の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="41784-295">At the top of the file, import the following namespaces:</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]  
  
6.  <span data-ttu-id="41784-296">宣言を変更する`MarqueeBorder`から継承する<xref:System.Windows.Forms.Panel>を実装して、`IMarqueeWidget`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="41784-296">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]  
  
7.  <span data-ttu-id="41784-297">管理するための 2 つの列挙型を宣言、`MarqueeBorder`コントロールの状態:`MarqueeSpinDirection`をライト""を中心として回転、境界線の方向を決めると`MarqueeLightShape`、(四角形または循環) のライトの形状を決定します。</span><span class="sxs-lookup"><span data-stu-id="41784-297">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="41784-298">配置する前にこれらの宣言、`MarqueeBorder`クラス宣言します。</span><span class="sxs-lookup"><span data-stu-id="41784-298">Place these declarations before the `MarqueeBorder` class declaration.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]  
  
8.  <span data-ttu-id="41784-299">公開されたプロパティに対応するインスタンス変数を宣言し、コンス トラクターで初期化します。</span><span class="sxs-lookup"><span data-stu-id="41784-299">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]  
  
9. <span data-ttu-id="41784-300">`IMarqueeWidget` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="41784-300">Implement the `IMarqueeWidget` interface.</span></span>  
  
     <span data-ttu-id="41784-301">`StartMarquee`と`StopMarquee`メソッドを呼び出し、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>と<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>メソッドを開始し、アニメーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="41784-301">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>  
  
     <span data-ttu-id="41784-302">`MarqueeBorder`コントロールで子コントロールを含めることができます、`StartMarquee`メソッドは、すべての子コントロールと呼び出しを列挙します。`StartMarquee`を実装するもので`IMarqueeWidget`です。</span><span class="sxs-lookup"><span data-stu-id="41784-302">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="41784-303">`StopMarquee`メソッドのような実装があります。</span><span class="sxs-lookup"><span data-stu-id="41784-303">The `StopMarquee` method has a similar implementation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]  
  
10. <span data-ttu-id="41784-304">プロパティ アクセサーを実装します。</span><span class="sxs-lookup"><span data-stu-id="41784-304">Implement the property accessors.</span></span> <span data-ttu-id="41784-305">`MarqueeBorder`コントロールの外観を制御するためのいくつかのプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="41784-305">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]  
  
11. <span data-ttu-id="41784-306">ハンドラーを実装、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント。</span><span class="sxs-lookup"><span data-stu-id="41784-306">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>  
  
     <span data-ttu-id="41784-307"><xref:System.ComponentModel.BackgroundWorker.DoWork>ミリ秒で指定された数のイベント ハンドラーがスリープ状態`UpdatePeriod`を生成し、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントを呼び出すことによって、コードがアニメーションを停止するまで<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>です。</span><span class="sxs-lookup"><span data-stu-id="41784-307">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>  
  
     <span data-ttu-id="41784-308"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント ハンドラーは、"base"、元は、他のライトの明/暗状態を判断、淡色テーマと呼び出しの位置をインクリメント、<xref:System.Windows.Forms.Control.Refresh%2A>メソッドを呼び出すと、コントロールを再描画します。</span><span class="sxs-lookup"><span data-stu-id="41784-308">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]  
  
12. <span data-ttu-id="41784-309">ヘルパー メソッドを実装する`IsLit`と`DrawLight`です。</span><span class="sxs-lookup"><span data-stu-id="41784-309">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>  
  
     <span data-ttu-id="41784-310">`IsLit`メソッドは、指定した位置にある光の色を決定します。</span><span class="sxs-lookup"><span data-stu-id="41784-310">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="41784-311">によって指定された色で描画されます「が点灯している」ライト、`LightColor`プロパティ、および [ダーク] にあるものがで指定された色で描画された、`DarkColor`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="41784-311">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>  
  
     <span data-ttu-id="41784-312">`DrawLight`メソッドは適切な色、形状、および位置を使用して、ライトを描画します。</span><span class="sxs-lookup"><span data-stu-id="41784-312">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]  
  
13. <span data-ttu-id="41784-313">上書き、<xref:System.Windows.Forms.Control.OnLayout%2A>と<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="41784-313">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>  
  
     <span data-ttu-id="41784-314"><xref:System.Windows.Forms.Control.OnPaint%2A>メソッドは、描画の端に沿ってライト、`MarqueeBorder`コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-314">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>  
  
     <span data-ttu-id="41784-315"><xref:System.Windows.Forms.Control.OnPaint%2A>メソッドの大きさによって異なります、`MarqueeBorder`コントロール、レイアウトが変更されたときに呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="41784-315">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="41784-316">そのため、オーバーライド<xref:System.Windows.Forms.Control.OnLayout%2A>を呼び出すと<xref:System.Windows.Forms.Control.Refresh%2A>です。</span><span class="sxs-lookup"><span data-stu-id="41784-316">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]  
  
## <a name="creating-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="41784-317">シャドウとフィルターのプロパティにカスタム デザイナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-317">Creating a Custom Designer to Shadow and Filter Properties</span></span>  
 <span data-ttu-id="41784-318">`MarqueeControlRootDesigner`クラスがルート デザイナーの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="41784-318">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="41784-319">動作するこのデザイナーに加え、 `MarqueeControl`、具体的には関連付けられているカスタム デザイナーが必要になります、`MarqueeBorder`コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-319">In addition to this designer, which operates on the `MarqueeControl`, you will need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="41784-320">このデザイナーは、カスタム ルート デザイナーのコンテキストで適切なカスタム動作を提供します。</span><span class="sxs-lookup"><span data-stu-id="41784-320">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>  
  
 <span data-ttu-id="41784-321">具体的には、 `MarqueeBorderDesigner` 「シャドウ」とに特定のプロパティをフィルター処理は、`MarqueeBorder`コントロール、デザイン環境との相互作用を変更します。</span><span class="sxs-lookup"><span data-stu-id="41784-321">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>  
  
 <span data-ttu-id="41784-322">「シャドウ」と呼ばれますが、コンポーネントのプロパティ アクセサーの呼び出しをインターセプトし、</span><span class="sxs-lookup"><span data-stu-id="41784-322">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="41784-323">によって、デザイナーは、ユーザーによって設定された値を追跡して、必要に応じてその値を渡すように設計されているコンポーネントにします。</span><span class="sxs-lookup"><span data-stu-id="41784-323">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>  
  
 <span data-ttu-id="41784-324">この例で、<xref:System.Windows.Forms.Control.Visible%2A>と<xref:System.Windows.Forms.Control.Enabled%2A>でプロパティをシャドウは、`MarqueeBorderDesigner`からユーザーを防ぐことが、`MarqueeBorder`コントロールを非表示またはデザイン時に無効です。</span><span class="sxs-lookup"><span data-stu-id="41784-324">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>  
  
 <span data-ttu-id="41784-325">デザイナーは、追加し、プロパティを削除することができますもできます。</span><span class="sxs-lookup"><span data-stu-id="41784-325">Designers can also add and remove properties.</span></span> <span data-ttu-id="41784-326">この例で、<xref:System.Windows.Forms.Control.Padding%2A>ためにそのプロパティが、デザイン時に削除された、`MarqueeBorder`コントロールで指定された光源のサイズに基づいての余白をプログラムで設定する、`LightSize`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="41784-326">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>  
  
 <span data-ttu-id="41784-327">基本クラス`MarqueeBorderDesigner`は<xref:System.ComponentModel.Design.ComponentDesigner>属性、プロパティ、およびデザイン時にコントロールによって公開されているイベントに変更できるメソッドを持ちます。</span><span class="sxs-lookup"><span data-stu-id="41784-327">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>  
  
-   <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>  
  
 <span data-ttu-id="41784-328">これらのメソッドを使用して、コンポーネントのパブリック インターフェイスを変更する場合は、これらの規則を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="41784-328">When changing the public interface of a component using these methods, you must follow these rules:</span></span>  
  
-   <span data-ttu-id="41784-329">項目の追加または削除、`PreFilter`メソッドにのみ</span><span class="sxs-lookup"><span data-stu-id="41784-329">Add or remove items in the `PreFilter` methods only</span></span>  
  
-   <span data-ttu-id="41784-330">既存の項目を変更、`PostFilter`メソッドにのみ</span><span class="sxs-lookup"><span data-stu-id="41784-330">Modify existing items in the `PostFilter` methods only</span></span>  
  
-   <span data-ttu-id="41784-331">基本実装を最初に呼び出す常に、`PreFilter`メソッド</span><span class="sxs-lookup"><span data-stu-id="41784-331">Always call the base implementation first in the `PreFilter` methods</span></span>  
  
-   <span data-ttu-id="41784-332">基本実装を最後呼び出す常に、`PostFilter`メソッド</span><span class="sxs-lookup"><span data-stu-id="41784-332">Always call the base implementation last in the `PostFilter` methods</span></span>  
  
 <span data-ttu-id="41784-333">これらの規則に従うことにより、デザイン時環境のすべてのデザイナーのように設計されているすべてのコンポーネントの一貫した表示できます。</span><span class="sxs-lookup"><span data-stu-id="41784-333">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>  
  
 <span data-ttu-id="41784-334"><xref:System.ComponentModel.Design.ComponentDesigner>クラスが特定のインスタンス変数を作成する必要がなくなるが影付きのプロパティの値を管理するためのディクショナリを提供します。</span><span class="sxs-lookup"><span data-stu-id="41784-334">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>  
  
#### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="41784-335">シャドウとフィルターのプロパティにカスタム デザイナーを作成するには</span><span class="sxs-lookup"><span data-stu-id="41784-335">To create a custom designer to shadow and filter properties</span></span>  
  
1.  <span data-ttu-id="41784-336">右クリックし、**デザイン**フォルダーと、新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="41784-336">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="41784-337">ソース ファイルの"MarqueeBorderDesigner"ベースの名前を付けます</span><span class="sxs-lookup"><span data-stu-id="41784-337">Give the source file a base name of "MarqueeBorderDesigner."</span></span>  
  
2.  <span data-ttu-id="41784-338">開く、`MarqueeBorderDesigner`内のソース ファイル、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="41784-338">Open the `MarqueeBorderDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="41784-339">ファイルの上部には、次の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="41784-339">At the top of the file, import the following namespaces:</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]  
  
3.  <span data-ttu-id="41784-340">宣言を変更する`MarqueeBorderDesigner`から継承する<xref:System.Windows.Forms.Design.ParentControlDesigner>です。</span><span class="sxs-lookup"><span data-stu-id="41784-340">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>  
  
     <span data-ttu-id="41784-341">`MarqueeBorder`コントロールで子コントロールを含めることができます`MarqueeBorderDesigner`から継承<xref:System.Windows.Forms.Design.ParentControlDesigner>親と子の対話を処理します。</span><span class="sxs-lookup"><span data-stu-id="41784-341">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]  
  
4.  <span data-ttu-id="41784-342">基本実装をオーバーライド<xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>です。</span><span class="sxs-lookup"><span data-stu-id="41784-342">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]  
  
5.  <span data-ttu-id="41784-343"><xref:System.Windows.Forms.Control.Enabled%2A> プロパティと <xref:System.Windows.Forms.Control.Visible%2A> プロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="41784-343">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="41784-344">これらの実装では、コントロールのプロパティをシャドウします。</span><span class="sxs-lookup"><span data-stu-id="41784-344">These implementations shadow the control's properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]  
  
## <a name="handling-component-changes"></a><span data-ttu-id="41784-345">コンポーネントの変更の処理</span><span class="sxs-lookup"><span data-stu-id="41784-345">Handling Component Changes</span></span>  
 <span data-ttu-id="41784-346">`MarqueeControlRootDesigner`クラスは、カスタムのデザイン時のエクスペリエンスを提供、`MarqueeControl`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="41784-346">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="41784-347">デザイン時の機能の大部分がから継承されます、<xref:System.Windows.Forms.Design.DocumentDesigner>クラス以外の特定の 2 つのカスタマイズを実装するコードは、: コンポーネントの変更を処理して、デザイナー動詞を追加します。</span><span class="sxs-lookup"><span data-stu-id="41784-347">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class; your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>  
  
 <span data-ttu-id="41784-348">ユーザー設計としてその`MarqueeControl`、インスタンスのルート デザイナーに変更の追跡は、`MarqueeControl`とその子コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-348">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="41784-349">デザイン時環境は、便利なサービスを提供<xref:System.ComponentModel.Design.IComponentChangeService>コンポーネントの状態に変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="41784-349">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>  
  
 <span data-ttu-id="41784-350">環境を照会することによってこのサービスへの参照を取得する、<xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="41784-350">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="41784-351">デザイナーがのハンドラーをアタッチできますクエリが成功した場合、<xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged>イベントし、デザイン時に一貫性のある状態を維持するために必要なタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="41784-351">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>  
  
 <span data-ttu-id="41784-352">場合、`MarqueeControlRootDesigner`呼び出しは、クラス、<xref:System.Windows.Forms.Control.Refresh%2A>メソッドごとに`IMarqueeWidget`オブジェクトに含まれる、`MarqueeControl`です。</span><span class="sxs-lookup"><span data-stu-id="41784-352">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="41784-353">これにより、`IMarqueeWidget`プロパティがその親のような場合に適切に再描画するオブジェクト<xref:System.Windows.Forms.Control.Size%2A>変更されます。</span><span class="sxs-lookup"><span data-stu-id="41784-353">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>  
  
#### <a name="to-handle-component-changes"></a><span data-ttu-id="41784-354">コンポーネントの変更を処理するには</span><span class="sxs-lookup"><span data-stu-id="41784-354">To handle component changes</span></span>  
  
1.  <span data-ttu-id="41784-355">開く、`MarqueeControlRootDesigner`内のソース ファイル、**コード エディター**をオーバーライドし、<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="41784-355">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="41784-356">基本実装を呼び出す<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>クエリを実行し、<xref:System.ComponentModel.Design.IComponentChangeService>です。</span><span class="sxs-lookup"><span data-stu-id="41784-356">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]  
  
2.  <span data-ttu-id="41784-357">実装、<xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="41784-357">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="41784-358">テストの送信側のコンポーネントの種類である場合と、 `IMarqueeWidget`、呼び出すその<xref:System.Windows.Forms.Control.Refresh%2A>メソッド。</span><span class="sxs-lookup"><span data-stu-id="41784-358">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]  
  
## <a name="adding-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="41784-359">カスタム デザイナー動詞を追加します。</span><span class="sxs-lookup"><span data-stu-id="41784-359">Adding Designer Verbs to your Custom Designer</span></span>  
 <span data-ttu-id="41784-360">デザイナー動詞は、イベント ハンドラーにリンクされているメニュー コマンドです。</span><span class="sxs-lookup"><span data-stu-id="41784-360">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="41784-361">デザイナー動詞は、デザイン時コンポーネントのショートカット メニューに追加されます。</span><span class="sxs-lookup"><span data-stu-id="41784-361">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="41784-362">詳細については、「<xref:System.ComponentModel.Design.DesignerVerb>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41784-362">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>  
  
 <span data-ttu-id="41784-363">2 つのデザイナー動詞は、デザイナーに追加:**テストの実行**と**テストの停止**です。</span><span class="sxs-lookup"><span data-stu-id="41784-363">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="41784-364">これらの動詞には、実行時の動作を表示することが、`MarqueeControl`デザイン時にします。</span><span class="sxs-lookup"><span data-stu-id="41784-364">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="41784-365">これらの動詞に追加されます、`MarqueeControlRootDesigner`です。</span><span class="sxs-lookup"><span data-stu-id="41784-365">These verbs will be added to the `MarqueeControlRootDesigner`.</span></span>  
  
 <span data-ttu-id="41784-366">ときに**テストの実行**が呼び出されると、動詞のイベント ハンドラーを呼び出す、`StartMarquee`メソッドを`MarqueeControl`です。</span><span class="sxs-lookup"><span data-stu-id="41784-366">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="41784-367">ときに**テストの停止**が呼び出されると、動詞のイベント ハンドラーを呼び出す、`StopMarquee`メソッドを`MarqueeControl`です。</span><span class="sxs-lookup"><span data-stu-id="41784-367">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="41784-368">実装、`StartMarquee`と`StopMarquee`メソッドを実装するコンテナー内のコントロールでこれらのメソッドを呼び出す`IMarqueeWidget`すべて含まれている、`IMarqueeWidget`コントロールも、テストに参加します。</span><span class="sxs-lookup"><span data-stu-id="41784-368">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>  
  
#### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="41784-369">デザイナー動詞をカスタム デザイナーに追加するには</span><span class="sxs-lookup"><span data-stu-id="41784-369">To add designer verbs to your custom designers</span></span>  
  
1.  <span data-ttu-id="41784-370">`MarqueeControlRootDesigner`クラス、という名前のイベント ハンドラー追加`OnVerbRunTest`と`OnVerbStopTest`です。</span><span class="sxs-lookup"><span data-stu-id="41784-370">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]  
  
2.  <span data-ttu-id="41784-371">これらのイベント ハンドラーを対応するデザイナー動詞に接続します。</span><span class="sxs-lookup"><span data-stu-id="41784-371">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="41784-372">`MarqueeControlRootDesigner`継承、<xref:System.ComponentModel.Design.DesignerVerbCollection>その基本クラスからです。</span><span class="sxs-lookup"><span data-stu-id="41784-372">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="41784-373">2 つ作成する新しい<xref:System.ComponentModel.Design.DesignerVerb>内のこのコレクションに追加して、オブジェクト、<xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="41784-373">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]  
  
## <a name="creating-a-custom-uitypeeditor"></a><span data-ttu-id="41784-374">カスタム</span><span class="sxs-lookup"><span data-stu-id="41784-374">Creating a Custom UITypeEditor</span></span>  
 <span data-ttu-id="41784-375">ユーザーのカスタム設計時の操作を作成するときに、[プロパティ] ウィンドウとカスタム操作を作成することが望ましいは多くの場合です。</span><span class="sxs-lookup"><span data-stu-id="41784-375">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="41784-376">これを行うに作成することで、<xref:System.Drawing.Design.UITypeEditor>です。</span><span class="sxs-lookup"><span data-stu-id="41784-376">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span> <span data-ttu-id="41784-377">詳細については、次を参照してください。[する方法: UI 型エディターを作成する](http://msdn.microsoft.com/library/292c6e33-8d85-4012-9b51-05835a6f6dfd)です。</span><span class="sxs-lookup"><span data-stu-id="41784-377">For more information, see [How to: Create a UI Type Editor](http://msdn.microsoft.com/library/292c6e33-8d85-4012-9b51-05835a6f6dfd).</span></span>  
  
 <span data-ttu-id="41784-378">`MarqueeBorder`コントロールのプロパティ ウィンドウでいくつかのプロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="41784-378">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="41784-379">これらのプロパティの 2 つの`MarqueeSpinDirection`と`MarqueeLightShape`列挙体によって表されます。</span><span class="sxs-lookup"><span data-stu-id="41784-379">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="41784-380">UI 型エディターの使用方法を説明する、`MarqueeLightShape`プロパティが関連付けられている必要がある<xref:System.Drawing.Design.UITypeEditor>クラスです。</span><span class="sxs-lookup"><span data-stu-id="41784-380">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>  
  
#### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="41784-381">カスタムの UI 型エディターを作成するには</span><span class="sxs-lookup"><span data-stu-id="41784-381">To create a custom UI type editor</span></span>  
  
1.  <span data-ttu-id="41784-382">開く、`MarqueeBorder`内のソース ファイル、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="41784-382">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="41784-383">定義で、`MarqueeBorder`クラスと呼ばれるクラスを宣言`LightShapeEditor`から派生した<xref:System.Drawing.Design.UITypeEditor>です。</span><span class="sxs-lookup"><span data-stu-id="41784-383">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]  
  
3.  <span data-ttu-id="41784-384">宣言、<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>インスタンス変数と呼ばれる`editorService`です。</span><span class="sxs-lookup"><span data-stu-id="41784-384">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]  
  
4.  <span data-ttu-id="41784-385"><xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="41784-385">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="41784-386">この実装を返します<xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>、デザイン環境を表示する方法を指示する、`LightShapeEditor`です。</span><span class="sxs-lookup"><span data-stu-id="41784-386">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]  
  
5.  <span data-ttu-id="41784-387"><xref:System.Drawing.Design.UITypeEditor.EditValue%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="41784-387">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="41784-388">この実装は、デザイン環境、<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-388">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="41784-389">成功すると、作成、`LightShapeSelectionControl`です。</span><span class="sxs-lookup"><span data-stu-id="41784-389">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="41784-390"><xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A>を開始するメソッドが呼び出され、`LightShapeEditor`です。</span><span class="sxs-lookup"><span data-stu-id="41784-390">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="41784-391">この呼び出しからの戻り値は、デザイン環境に返されます。</span><span class="sxs-lookup"><span data-stu-id="41784-391">The return value from this invocation is returned to the design environment.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]  
  
## <a name="creating-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="41784-392">カスタムのビュー コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="41784-392">Creating a View Control for your Custom UITypeEditor</span></span>  
  
1.  <span data-ttu-id="41784-393">`MarqueeLightShape`プロパティには、ライトの図形の 2 種類がサポートしています:`Square`と`Circle`です。</span><span class="sxs-lookup"><span data-stu-id="41784-393">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="41784-394">[プロパティ] ウィンドウで、これらの値をグラフィカルに表示するためだけに使用するカスタム コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="41784-394">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="41784-395">このカスタム コントロールで使用される、<xref:System.Drawing.Design.UITypeEditor>プロパティ ウィンドウと対話します。</span><span class="sxs-lookup"><span data-stu-id="41784-395">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>  
  
#### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="41784-396">カスタム UI 型エディターのビュー コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="41784-396">To create a view control for your custom UI type editor</span></span>  
  
1.  <span data-ttu-id="41784-397">新しい<xref:System.Windows.Forms.UserControl>項目を`MarqueeControlLibrary`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-397">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="41784-398">新しいソース ファイル"LightShapeSelectionControl"の基本の名前を付けます</span><span class="sxs-lookup"><span data-stu-id="41784-398">Give the new source file a base name of "LightShapeSelectionControl."</span></span>  
  
2.  <span data-ttu-id="41784-399">2 つをドラッグして<xref:System.Windows.Forms.Panel>から制御、**ツールボックス**上に、`LightShapeSelectionControl`です。</span><span class="sxs-lookup"><span data-stu-id="41784-399">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="41784-400">名前を付けます`squarePanel`と`circlePanel`です。</span><span class="sxs-lookup"><span data-stu-id="41784-400">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="41784-401">サイド バイ サイドそれらを配置します。</span><span class="sxs-lookup"><span data-stu-id="41784-401">Arrange them side by side.</span></span> <span data-ttu-id="41784-402">設定、<xref:System.Windows.Forms.Control.Size%2A>両方のプロパティ<xref:System.Windows.Forms.Panel>コントロールを (60、60)。</span><span class="sxs-lookup"><span data-stu-id="41784-402">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to (60, 60).</span></span> <span data-ttu-id="41784-403">設定、<xref:System.Windows.Forms.Control.Location%2A>のプロパティ、`squarePanel`に制御を (8, 10)。</span><span class="sxs-lookup"><span data-stu-id="41784-403">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to (8, 10).</span></span> <span data-ttu-id="41784-404">設定、<xref:System.Windows.Forms.Control.Location%2A>のプロパティ、`circlePanel`に制御を (80, 10)。</span><span class="sxs-lookup"><span data-stu-id="41784-404">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to (80, 10).</span></span> <span data-ttu-id="41784-405">最後に、設定、<xref:System.Windows.Forms.Control.Size%2A>のプロパティ、`LightShapeSelectionControl`に (150、80)。</span><span class="sxs-lookup"><span data-stu-id="41784-405">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to (150, 80).</span></span>  
  
3.  <span data-ttu-id="41784-406">開く、`LightShapeSelectionControl`内のソース ファイル、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="41784-406">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="41784-407">ファイルの上部には、インポート、<xref:System.Windows.Forms.Design?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="41784-407">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>  
  
```vb  
Imports System.Windows.Forms.Design  
```  
  
```csharp  
using System.Windows.Forms.Design;  
```  
  
1.  <span data-ttu-id="41784-408">実装<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー、`squarePanel`と`circlePanel`コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-408">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="41784-409">これらのメソッドを呼び出す<xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>カスタムを終了する<xref:System.Drawing.Design.UITypeEditor>セッションを編集します。</span><span class="sxs-lookup"><span data-stu-id="41784-409">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]  
  
2.  <span data-ttu-id="41784-410">宣言、<xref:System.Windows.Forms.Design.IWindowsFormsEditorService>インスタンス変数と呼ばれる`editorService`です。</span><span class="sxs-lookup"><span data-stu-id="41784-410">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>  
  
```vb  
Private editorService As IWindowsFormsEditorService  
```  
  
```csharp  
private IWindowsFormsEditorService editorService;  
```  
  
1.  <span data-ttu-id="41784-411">宣言、`MarqueeLightShape`インスタンス変数と呼ばれる`lightShapeValue`です。</span><span class="sxs-lookup"><span data-stu-id="41784-411">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]  
  
2.  <span data-ttu-id="41784-412">`LightShapeSelectionControl`コンス トラクター、アタッチ、<xref:System.Windows.Forms.Control.Click>へのイベント ハンドラー、`squarePanel`と`circlePanel`コントロールの<xref:System.Windows.Forms.Control.Click>イベント。</span><span class="sxs-lookup"><span data-stu-id="41784-412">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="41784-413">また、割り当てをコンス トラクター オーバー ロードを定義、`MarqueeLightShape`デザイン環境から値、`lightShapeValue`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="41784-413">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]  
  
3.  <span data-ttu-id="41784-414"><xref:System.ComponentModel.Component.Dispose%2A>メソッド、デタッチ、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="41784-414">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]  
  
4.  <span data-ttu-id="41784-415">**ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="41784-415">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="41784-416">ファイルを開き、LightShapeSelectionControl.Designer.cs または LightShapeSelectionControl.Designer.vb の既定の定義を削除、<xref:System.ComponentModel.Component.Dispose%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="41784-416">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>  
  
5.  <span data-ttu-id="41784-417">`LightShape` プロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="41784-417">Implement the `LightShape` property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]  
  
6.  <span data-ttu-id="41784-418"><xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="41784-418">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="41784-419">この実装は、塗りつぶされた四角形と円を描画します。</span><span class="sxs-lookup"><span data-stu-id="41784-419">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="41784-420">また、どちらか 1 つの図形の周囲に罫線を描画することによって、選択した値を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="41784-420">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]  
  
## <a name="testing-your-custom-control-in-the-designer"></a><span data-ttu-id="41784-421">デザイナーでカスタム コントロールのテスト</span><span class="sxs-lookup"><span data-stu-id="41784-421">Testing your Custom Control in the Designer</span></span>  
 <span data-ttu-id="41784-422">この時点では、ビルドすることができます、`MarqueeControlLibrary`プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="41784-422">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="41784-423">継承されるコントロールを作成することで実装をテスト、`MarqueeControl`クラスおよびフォーム上で使用します。</span><span class="sxs-lookup"><span data-stu-id="41784-423">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>  
  
#### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="41784-424">カスタム MarqueeControl 実装を作成するには</span><span class="sxs-lookup"><span data-stu-id="41784-424">To create a custom MarqueeControl implementation</span></span>  
  
1.  <span data-ttu-id="41784-425">Windows フォーム デザイナーで `DemoMarqueeControl` を開きます。</span><span class="sxs-lookup"><span data-stu-id="41784-425">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="41784-426">このインスタンスを作成、`DemoMarqueeControl`を入力し、それのインスタンスの表示、`MarqueeControlRootDesigner`型です。</span><span class="sxs-lookup"><span data-stu-id="41784-426">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>  
  
2.  <span data-ttu-id="41784-427">**ツールボックス**を開き、**にコンポーネント**タブです。表示されます、`MarqueeBorder`と`MarqueeText`コントロールの選択に使用できます。</span><span class="sxs-lookup"><span data-stu-id="41784-427">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>  
  
3.  <span data-ttu-id="41784-428">インスタンスをドラッグして、`MarqueeBorder`コントロールを`DemoMarqueeControl`デザイン サーフェイスです。</span><span class="sxs-lookup"><span data-stu-id="41784-428">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="41784-429">このドッキング`MarqueeBorder`コントロールを親コントロールです。</span><span class="sxs-lookup"><span data-stu-id="41784-429">Dock this `MarqueeBorder` control to the parent control.</span></span>  
  
4.  <span data-ttu-id="41784-430">インスタンスをドラッグして、`MarqueeText`コントロールを`DemoMarqueeControl`デザイン サーフェイスです。</span><span class="sxs-lookup"><span data-stu-id="41784-430">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>  
  
5.  <span data-ttu-id="41784-431">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="41784-431">Build the solution.</span></span>  
  
6.  <span data-ttu-id="41784-432">右クリックし、`DemoMarqueeControl`ショートカット メニューを選択し、**テストの実行**アニメーションを開始するにはオプションです。</span><span class="sxs-lookup"><span data-stu-id="41784-432">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="41784-433">をクリックして**テストの停止**アニメーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="41784-433">Click **Stop Test** to stop the animation.</span></span>  
  
7.  <span data-ttu-id="41784-434">開いている**Form1**デザイン ビューでします。</span><span class="sxs-lookup"><span data-stu-id="41784-434">Open **Form1** in Design view.</span></span>  
  
8.  <span data-ttu-id="41784-435">2 つの配置<xref:System.Windows.Forms.Button>フォーム上のコントロールです。</span><span class="sxs-lookup"><span data-stu-id="41784-435">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="41784-436">名前を付けます`startButton`と`stopButton`、し、変更、<xref:System.Windows.Forms.Control.Text%2A>プロパティ値を**開始**と**停止**、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="41784-436">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>  
  
9. <span data-ttu-id="41784-437">実装<xref:System.Windows.Forms.Control.Click>両方のイベント ハンドラー<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="41784-437">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>  
  
10. <span data-ttu-id="41784-438">**ツールボックス**を開き、**ためコンポーネント**タブです。表示されます、`DemoMarqueeControl`選択に使用できます。</span><span class="sxs-lookup"><span data-stu-id="41784-438">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>  
  
11. <span data-ttu-id="41784-439">インスタンスをドラッグ`DemoMarqueeControl`上に、 **Form1**デザイン サーフェイスです。</span><span class="sxs-lookup"><span data-stu-id="41784-439">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>  
  
12. <span data-ttu-id="41784-440"><xref:System.Windows.Forms.Control.Click>イベント ハンドラーを呼び出す、`Start`と`Stop`のメソッド、`DemoMarqueeControl`です。</span><span class="sxs-lookup"><span data-stu-id="41784-440">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>  
  
```vb  
Private Sub startButton_Click(sender As Object, e As System.EventArgs)  
    Me.demoMarqueeControl1.Start()  
End Sub 'startButton_Click  
  
Private Sub stopButton_Click(sender As Object, e As System.EventArgs)  
Me.demoMarqueeControl1.Stop()  
End Sub 'stopButton_Click  
```  
  
```csharp  
private void startButton_Click(object sender, System.EventArgs e)  
{  
    this.demoMarqueeControl1.Start();  
}  
  
private void stopButton_Click(object sender, System.EventArgs e)  
{  
    this.demoMarqueeControl1.Stop();  
}  
```  
  
1.  <span data-ttu-id="41784-441">設定、`MarqueeControlTest`プロジェクトをスタートアップ プロジェクトとして使用し、実行します。</span><span class="sxs-lookup"><span data-stu-id="41784-441">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="41784-442">表示するフォームが表示されます、`DemoMarqueeControl`です。</span><span class="sxs-lookup"><span data-stu-id="41784-442">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="41784-443">クリックして、**開始**アニメーションを開始するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="41784-443">Click the **Start** button to start the animation.</span></span> <span data-ttu-id="41784-444">テキストが点滅し、光が境界線を移動するはずです。</span><span class="sxs-lookup"><span data-stu-id="41784-444">You should see the text flashing and the lights moving around the border.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="41784-445">次の手順</span><span class="sxs-lookup"><span data-stu-id="41784-445">Next Steps</span></span>  
 <span data-ttu-id="41784-446">`MarqueeControlLibrary`カスタム コントロールと関連付けられたデザイナーの単純な実装を示します。</span><span class="sxs-lookup"><span data-stu-id="41784-446">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="41784-447">いくつかの方法で行うと、このサンプルがより高度です。</span><span class="sxs-lookup"><span data-stu-id="41784-447">You can make this sample more sophisticated in several ways:</span></span>  
  
-   <span data-ttu-id="41784-448">プロパティ値を変更、`DemoMarqueeControl`デザイナーでします。</span><span class="sxs-lookup"><span data-stu-id="41784-448">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="41784-449">さらに追加`MarqueBorder`を制御し、入れ子になった効果を作成するには、その親インスタンス内にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="41784-449">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="41784-450">さまざまな設定と実験、`UpdatePeriod`と光に関連するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="41784-450">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>  
  
-   <span data-ttu-id="41784-451">独自の実装を作成`IMarqueeWidget`です。</span><span class="sxs-lookup"><span data-stu-id="41784-451">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="41784-452">複数のイメージで、点滅"またはアニメーション化されたサインインを作成することなど。</span><span class="sxs-lookup"><span data-stu-id="41784-452">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>  
  
-   <span data-ttu-id="41784-453">さらに、デザイン時のエクスペリエンスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="41784-453">Further customize the design-time experience.</span></span> <span data-ttu-id="41784-454">多くのプロパティをシャドウを試して<xref:System.Windows.Forms.Control.Enabled%2A>と<xref:System.Windows.Forms.Control.Visible%2A>、し、新しいプロパティを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="41784-454">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="41784-455">子コントロールのドッキングなどの一般的なタスクを簡略化する新しいデザイナー動詞を追加します。</span><span class="sxs-lookup"><span data-stu-id="41784-455">Add new designer verbs to simplify common tasks like docking child controls.</span></span>  
  
-   <span data-ttu-id="41784-456">ライセンス、`MarqueeControl`です。</span><span class="sxs-lookup"><span data-stu-id="41784-456">License the `MarqueeControl`.</span></span> <span data-ttu-id="41784-457">詳細については、次を参照してください。[する方法: ライセンス コンポーネントやコントロール](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)です。</span><span class="sxs-lookup"><span data-stu-id="41784-457">For more information, see [How to: License Components and Controls](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57).</span></span>  
  
-   <span data-ttu-id="41784-458">コントロールをシリアル化する方法と、それらのコードを生成する方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="41784-458">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="41784-459">詳細については、次を参照してください。[動的ソース コードの生成とコンパイル](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)です。</span><span class="sxs-lookup"><span data-stu-id="41784-459">For more information, see [Dynamic Source Code Generation and Compilation](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41784-460">参照</span><span class="sxs-lookup"><span data-stu-id="41784-460">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <xref:System.Windows.Forms.Design.ParentControlDesigner>  
 <xref:System.Windows.Forms.Design.DocumentDesigner>  
 <xref:System.ComponentModel.Design.IRootDesigner>  
 <xref:System.ComponentModel.Design.DesignerVerb>  
 <xref:System.Drawing.Design.UITypeEditor>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [<span data-ttu-id="41784-461">方法: デザイン時機能を活用した Windows フォーム コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="41784-461">How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features</span></span>](http://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)  
 [<span data-ttu-id="41784-462">デザイン時サポートの拡張</span><span class="sxs-lookup"><span data-stu-id="41784-462">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [<span data-ttu-id="41784-463">カスタム デザイナー</span><span class="sxs-lookup"><span data-stu-id="41784-463">Custom Designers</span></span>](http://msdn.microsoft.com/library/ca11988e-d38e-44d8-a05d-71362ae7844d)  
 [<span data-ttu-id="41784-464">.NET 図形ライブラリ: サンプル デザイナー</span><span class="sxs-lookup"><span data-stu-id="41784-464">.NET Shape Library: A Sample Designer</span></span>](http://windowsforms.net/articles/shapedesigner.aspx)
