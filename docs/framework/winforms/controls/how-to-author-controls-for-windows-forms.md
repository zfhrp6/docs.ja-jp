---
title: "方法 : Windows フォームのコントロールを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 125e3f1c32c5186cce0b28aa3f8d1eff1ef95a09
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-author-controls-for-windows-forms"></a><span data-ttu-id="9c36e-102">方法 : Windows フォームのコントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="9c36e-102">How to: Author Controls for Windows Forms</span></span>
<span data-ttu-id="9c36e-103">コントロールは、ユーザーとプログラムの間のグラフィカルなリンクを表します。</span><span class="sxs-lookup"><span data-stu-id="9c36e-103">A control represents a graphical link between the user and the program.</span></span> <span data-ttu-id="9c36e-104">コントロールは、データの提供または処理、ユーザー入力の受け付け、イベントへの応答、ユーザーとアプリケーションを接続する他の任意の数の関数の実行を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9c36e-104">A control can provide or process data, accept user input, respond to events, or perform any number of other functions that connect the user and the application.</span></span> <span data-ttu-id="9c36e-105">コントロールは、基本的にグラフィカル インターフェイスを持つコンポーネントであるため、ユーザーとの対話だけでなく、コンポーネントが実行するあらゆる機能を果たします。</span><span class="sxs-lookup"><span data-stu-id="9c36e-105">Because a control is essentially a component with a graphical interface, it can serve any function that a component does, as well as provide user interaction.</span></span> <span data-ttu-id="9c36e-106">コントロールは特定の目的に使用するために作成します。コントロールの作成は、まったく別のプログラミング タスクです。</span><span class="sxs-lookup"><span data-stu-id="9c36e-106">Controls are created to serve specific purposes, and authoring controls is just another programming task.</span></span> <span data-ttu-id="9c36e-107">このことを念頭に、次の手順では、コントロールの作成手順の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="9c36e-107">With that in mind, the following steps represent an overview of the control authoring process.</span></span> <span data-ttu-id="9c36e-108">個々の手順のリンクで追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="9c36e-108">Links provide additional information on the individual steps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c36e-109">Web フォームで使用するカスタム コントロールを作成する場合は、「[カスタム ASP.NET サーバー コントロールの開発](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c36e-109">If you want to author a custom control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
>   
>  <span data-ttu-id="9c36e-110">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9c36e-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9c36e-111">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c36e-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9c36e-112">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c36e-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-author-a-control"></a><span data-ttu-id="9c36e-113">コントロールを作成するには</span><span class="sxs-lookup"><span data-stu-id="9c36e-113">To author a control</span></span>  
  
1.  <span data-ttu-id="9c36e-114">コントロールで何を実行するか、またはアプリケーション内のどのような役割を果たすかを決定します。</span><span class="sxs-lookup"><span data-stu-id="9c36e-114">Determine what you want your control to accomplish, or what part it will play in your application.</span></span> <span data-ttu-id="9c36e-115">考慮すべき要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9c36e-115">Factors to consider are:</span></span>  
  
    -   <span data-ttu-id="9c36e-116">どのようなグラフィカル インターフェイスが必要か。</span><span class="sxs-lookup"><span data-stu-id="9c36e-116">What kind of graphical interface do you need?</span></span>  
  
    -   <span data-ttu-id="9c36e-117">このコントロールでユーザーとの間で具体的にどのような対話を処理するか。</span><span class="sxs-lookup"><span data-stu-id="9c36e-117">What specific user interactions will this control handle?</span></span>  
  
    -   <span data-ttu-id="9c36e-118">必要とする機能が既存のコントロールによって提供されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="9c36e-118">Is the functionality you need provided by any existing controls?</span></span>  
  
    -   <span data-ttu-id="9c36e-119">複数の Windows フォーム コントロールを組み合わせることによって必要とする機能を実現できるかどうか。</span><span class="sxs-lookup"><span data-stu-id="9c36e-119">Can you get the functionality you need by combining several Windows Forms controls?</span></span>  
  
2.  <span data-ttu-id="9c36e-120">コントロール用にオブジェクト モデルが必要な場合は、オブジェクト モデル全体に機能を配布する方法を決定し、コントロールと下位オブジェクトの間で機能を分割します。</span><span class="sxs-lookup"><span data-stu-id="9c36e-120">If you need an object model for your control, determine how functionality will be distributed throughout the object model, and divide up functionality between the control and any subobjects.</span></span> <span data-ttu-id="9c36e-121">複合コントロールを計画している場合や、複数の機能を組み込む場合は、オブジェクト モデルが役立つ可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9c36e-121">An object model may be useful if you are planning a complex control, or want to incorporate several functionalities.</span></span>  
  
3.  <span data-ttu-id="9c36e-122">必要なコントロールの種類 (ユーザー コントロール、カスタム コントロール、継承された Windows フォーム コントロールなど) を特定します。</span><span class="sxs-lookup"><span data-stu-id="9c36e-122">Determine the type of control (for example, user control, custom control, inherited Windows Forms control) you need.</span></span> <span data-ttu-id="9c36e-123">詳細については、「[コントロールの種類に関するアドバイス](../../../../docs/framework/winforms/controls/control-type-recommendations.md)」と「[さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c36e-123">For details, see [Control Type Recommendations](../../../../docs/framework/winforms/controls/control-type-recommendations.md) and [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
4.  <span data-ttu-id="9c36e-124">機能をプロパティ、メソッド、およびコントロールとその下位オブジェクトまたは従属構造体のイベントとして表現し、適切なアクセス レベル (たとえば、public、protected など) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9c36e-124">Express functionality as properties, methods, and events of the control and its subobjects or subsidiary structures, and assign appropriate access levels (for example, public, protected, and so on).</span></span>  
  
5.  <span data-ttu-id="9c36e-125">コントロールのカスタム描画が必要な場合は、そのコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9c36e-125">If you need custom painting for your control, add code for it.</span></span> <span data-ttu-id="9c36e-126">詳細については、「[コントロールのカスタム描画およびレンダリング](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c36e-126">For details, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
6.  <span data-ttu-id="9c36e-127">コントロールから継承している場合<xref:System.Windows.Forms.UserControl>で実行されていることをコントロール プロジェクトをビルドして実行時の動作をテストすることができます、 **UserControl Test Container**です。</span><span class="sxs-lookup"><span data-stu-id="9c36e-127">If your control inherits from <xref:System.Windows.Forms.UserControl>, you can test its runtime behavior by building the control project and running it in the **UserControl Test Container**.</span></span> <span data-ttu-id="9c36e-128">詳細については、「[方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c36e-128">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
7.  <span data-ttu-id="9c36e-129">Windows アプリケーションなどの新しいプロジェクトを作成してコンテナーに配置することで、コントロールをテストしてデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="9c36e-129">You can also test and debug your control by creating a new project, such as a Windows Application, and placing it into a container.</span></span> <span data-ttu-id="9c36e-130">このプロセスは、「[チュートリアル: Visual Basic による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)」の一部として説明されています。</span><span class="sxs-lookup"><span data-stu-id="9c36e-130">This process is demonstrated as part of [Walkthrough: Authoring a Composite Control with Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).</span></span>  
  
8.  <span data-ttu-id="9c36e-131">各機能を追加するときは、テスト プロジェクトに機能を追加して新しい機能を実行します。</span><span class="sxs-lookup"><span data-stu-id="9c36e-131">As you add each feature, add features to your test project to exercise the new functionality.</span></span>  
  
9. <span data-ttu-id="9c36e-132">繰り返して、デザインを調整します。</span><span class="sxs-lookup"><span data-stu-id="9c36e-132">Repeat, refining the design.</span></span>  
  
10. <span data-ttu-id="9c36e-133">コントロールをパッケージ化してデプロイします。</span><span class="sxs-lookup"><span data-stu-id="9c36e-133">Package and deploy your control.</span></span> <span data-ttu-id="9c36e-134">詳細については、「[アプリケーション、サービス、およびコンポーネントの配置](https://msdn.microsoft.com/library/wtzawcsz)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c36e-134">For details, see [Deploying Applications, Services, and Components](https://msdn.microsoft.com/library/wtzawcsz).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c36e-135">参照</span><span class="sxs-lookup"><span data-stu-id="9c36e-135">See Also</span></span>  
 [<span data-ttu-id="9c36e-136">チュートリアル: Visual Basic による複合コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="9c36e-136">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="9c36e-137">チュートリアル: Visual Basic による Windows フォーム コントロールからの継承</span><span class="sxs-lookup"><span data-stu-id="9c36e-137">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [<span data-ttu-id="9c36e-138">方法: UserControl クラスを継承する</span><span class="sxs-lookup"><span data-stu-id="9c36e-138">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [<span data-ttu-id="9c36e-139">方法: コントロール クラスを継承する</span><span class="sxs-lookup"><span data-stu-id="9c36e-139">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [<span data-ttu-id="9c36e-140">方法: 既存の Windows フォーム コントロールから継承する</span><span class="sxs-lookup"><span data-stu-id="9c36e-140">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [<span data-ttu-id="9c36e-141">方法: UserControl の実行時の動作をテストする</span><span class="sxs-lookup"><span data-stu-id="9c36e-141">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [<span data-ttu-id="9c36e-142">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="9c36e-142">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
