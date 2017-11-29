---
title: "チュートリアル : ハイブリッド アプリケーションのローカライズ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e1425eafd0f1663aaf82185e0f32bf2a3bea509
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="83089-102">チュートリアル : ハイブリッド アプリケーションのローカライズ</span><span class="sxs-lookup"><span data-stu-id="83089-102">Walkthrough: Localizing a Hybrid Application</span></span>
<span data-ttu-id="83089-103">このチュートリアルでは、ローカライズする方法について[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内の要素、 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-ベースのハイブリッド アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="83089-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>  
  
 <span data-ttu-id="83089-104">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="83089-104">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="83089-105">作成する、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ホスト プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="83089-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>  
  
-   <span data-ttu-id="83089-106">ローカライズ可能なコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="83089-106">Adding localizable content.</span></span>  
  
-   <span data-ttu-id="83089-107">ローカリゼーションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="83089-107">Enabling localization.</span></span>  
  
-   <span data-ttu-id="83089-108">リソース識別子を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="83089-108">Assigning resource identifiers.</span></span>  
  
-   <span data-ttu-id="83089-109">LocBaml ツールを使用して、サテライト アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="83089-109">Using the LocBaml tool to produce a satellite assembly.</span></span>  
  
 <span data-ttu-id="83089-110">このチュートリアルでタスクの完全なコードについては、次を参照してください。[ハイブリッド アプリケーションのサンプルのローカライズ](http://go.microsoft.com/fwlink/?LinkID=160015)です。</span><span class="sxs-lookup"><span data-stu-id="83089-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](http://go.microsoft.com/fwlink/?LinkID=160015).</span></span>  
  
 <span data-ttu-id="83089-111">完了したら、ローカライズされたハイブリッド アプリケーションがあります。</span><span class="sxs-lookup"><span data-stu-id="83089-111">When you are finished, you will have a localized hybrid application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="83089-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="83089-112">Prerequisites</span></span>  
 <span data-ttu-id="83089-113">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="83089-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]<span data-ttu-id="83089-114">。</span><span class="sxs-lookup"><span data-stu-id="83089-114">.</span></span>  
  
## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="83089-115">Windows フォーム ホスト プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="83089-115">Creating the Windows Forms Host Project</span></span>  
 <span data-ttu-id="83089-116">作成するには、まず、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]アプリケーション プロジェクトを追加、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカライズはコンテンツを持つ要素。</span><span class="sxs-lookup"><span data-stu-id="83089-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>  
  
#### <a name="to-create-the-host-project"></a><span data-ttu-id="83089-117">ホスト プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="83089-117">To create the host project</span></span>  
  
1.  <span data-ttu-id="83089-118">という名前の WPF アプリケーション プロジェクトを作成する`LocalizingWpfInWf`です。</span><span class="sxs-lookup"><span data-stu-id="83089-118">Create a WPF Application project named `LocalizingWpfInWf`.</span></span> <span data-ttu-id="83089-119">詳細については、「 [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83089-119">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="83089-120">追加、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>と呼ばれる要素`SimpleControl`をプロジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="83089-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>  
  
3.  <span data-ttu-id="83089-121">使用して、<xref:System.Windows.Forms.Integration.ElementHost>コントロールを配置する、`SimpleControl`フォーム上の要素。</span><span class="sxs-lookup"><span data-stu-id="83089-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="83089-122">詳細については、次を参照してください。[チュートリアル: Windows フォームの 3-D WPF 複合コントロールをホストしている](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="83089-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>  
  
## <a name="adding-localizable-content"></a><span data-ttu-id="83089-123">ローカライズ可能なコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="83089-123">Adding Localizable Content</span></span>  
 <span data-ttu-id="83089-124">次に、追加する、[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コントロールにラベルを付けるし、設定、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素のコンテンツをローカライズ可能な文字列。</span><span class="sxs-lookup"><span data-stu-id="83089-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>  
  
#### <a name="to-add-localizable-content"></a><span data-ttu-id="83089-125">ローカライズ可能なコンテンツを追加するには</span><span class="sxs-lookup"><span data-stu-id="83089-125">To add localizable content</span></span>  
  
1.  <span data-ttu-id="83089-126">ソリューション エクスプ ローラーで、 **SimpleControl.xaml**で開く、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="83089-126">In Solution Explorer, double-click **SimpleControl.xaml** to open it in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
2.  <span data-ttu-id="83089-127">コンテンツを設定、<xref:System.Windows.Controls.Button>次のコードを使用して制御します。</span><span class="sxs-lookup"><span data-stu-id="83089-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>  
  
     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]  
  
3.  <span data-ttu-id="83089-128">ソリューション エクスプ ローラーで、 **Form1**を Windows フォーム デザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="83089-128">In Solution Explorer, double-click **Form1** to open it in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="83089-129">ツールボックスを開き をダブルクリック**ラベル**ラベル コントロールをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="83089-129">Open the Toolbox and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="83089-130"><xref:System.Windows.Forms.Control.Text%2A> プロパティの値を `"Hello"` に設定します。</span><span class="sxs-lookup"><span data-stu-id="83089-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>  
  
5.  <span data-ttu-id="83089-131">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="83089-131">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="83089-132">両方の`SimpleControl`要素、およびラベル コントロールのテキストを表示**「こんにちは」**です。</span><span class="sxs-lookup"><span data-stu-id="83089-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>  
  
## <a name="enabling-localization"></a><span data-ttu-id="83089-133">ローカリゼーションの有効化</span><span class="sxs-lookup"><span data-stu-id="83089-133">Enabling Localization</span></span>  
 <span data-ttu-id="83089-134">Windows フォーム デザイナーは、サテライト アセンブリでのローカライズを有効にするための設定を提供します。</span><span class="sxs-lookup"><span data-stu-id="83089-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>  
  
#### <a name="to-enable-localization"></a><span data-ttu-id="83089-135">ローカリゼーションを有効にするには</span><span class="sxs-lookup"><span data-stu-id="83089-135">To enable localization</span></span>  
  
1.  <span data-ttu-id="83089-136">ソリューション エクスプ ローラーで、 **Form1.cs**を Windows フォーム デザイナーで開きます。</span><span class="sxs-lookup"><span data-stu-id="83089-136">In Solution Explorer, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="83089-137">[プロパティ] ウィンドウで、フォームの値を設定**Localizable**プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="83089-137">In the Properties window, set the value of the form's **Localizable** property to `true`.</span></span>  
  
3.  <span data-ttu-id="83089-138">[プロパティ] ウィンドウ内の値を設定、**言語**プロパティを**スペイン語 (スペイン)**です。</span><span class="sxs-lookup"><span data-stu-id="83089-138">In the Properties window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>  
  
4.  <span data-ttu-id="83089-139">Windows フォーム デザイナーでは、ラベル コントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="83089-139">In the Windows Forms Designer, select the label control.</span></span>  
  
5.  <span data-ttu-id="83089-140">[プロパティ] ウィンドウ内の値を設定、<xref:System.Windows.Forms.Control.Text%2A>プロパティを`"Hola"`です。</span><span class="sxs-lookup"><span data-stu-id="83089-140">In the Properties window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>  
  
     <span data-ttu-id="83089-141">Form1.es ES.resx をという名前の新しいリソース ファイルがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="83089-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>  
  
6.  <span data-ttu-id="83089-142">ソリューション エクスプ ローラーで右クリック**Form1.cs**  をクリック**コードの表示**コード エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="83089-142">In Solution Explorer, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>  
  
7.  <span data-ttu-id="83089-143">次のコードをコピー、`Form1`への呼び出しの前のコンス トラクター`InitializeComponent`です。</span><span class="sxs-lookup"><span data-stu-id="83089-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>  
  
     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]  
  
8.  <span data-ttu-id="83089-144">ソリューション エクスプ ローラーで右クリック**LocalizingWpfInWf**  をクリック**プロジェクトのアンロード**です。</span><span class="sxs-lookup"><span data-stu-id="83089-144">In Solution Explorer, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>  
  
     <span data-ttu-id="83089-145">プロジェクト名のラベルは**(使用不可)**です。</span><span class="sxs-lookup"><span data-stu-id="83089-145">The project name is labeled **(unavailable)**.</span></span>  
  
9. <span data-ttu-id="83089-146">右クリック**LocalizingWpfInWf**、 をクリック**編集 LocalizingWpfInWf.csproj**です。</span><span class="sxs-lookup"><span data-stu-id="83089-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>  
  
     <span data-ttu-id="83089-147">プロジェクト ファイルがコード エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="83089-147">The project file opens in the Code Editor.</span></span>  
  
10. <span data-ttu-id="83089-148">最初に、次の行をコピー`PropertyGroup`プロジェクト ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="83089-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>  
  
    ```xml  
    <UICulture>en-US</UICulture>   
    ```  
  
11. <span data-ttu-id="83089-149">プロジェクト ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="83089-149">Save the project file and close it.</span></span>  
  
12. <span data-ttu-id="83089-150">ソリューション エクスプ ローラーで右クリック**LocalizingWpfInWf**  をクリック**プロジェクトの再読み込み**です。</span><span class="sxs-lookup"><span data-stu-id="83089-150">In Solution Explorer, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>  
  
## <a name="assigning-resource-identifiers"></a><span data-ttu-id="83089-151">リソース識別子を割り当てる</span><span class="sxs-lookup"><span data-stu-id="83089-151">Assigning Resource Identifiers</span></span>  
 <span data-ttu-id="83089-152">リソース識別子を使用して、リソース アセンブリに、ローカライズ可能なコンテンツをマップできます。</span><span class="sxs-lookup"><span data-stu-id="83089-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="83089-153">MsBuild.exe アプリケーションを指定するときに自動的にリソース識別子を割り当てます、`updateuid`オプション。</span><span class="sxs-lookup"><span data-stu-id="83089-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>  
  
#### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="83089-154">リソース識別子を割り当てる</span><span class="sxs-lookup"><span data-stu-id="83089-154">To assign resource identifiers</span></span>  
  
1.  <span data-ttu-id="83089-155">[スタート] メニューから開きます、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]コマンド プロンプトです。</span><span class="sxs-lookup"><span data-stu-id="83089-155">From the Start Menu, open the [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] Command Prompt.</span></span>  
  
2.  <span data-ttu-id="83089-156">次のコマンドを使用して、ローカライズ可能なコンテンツにリソース識別子を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="83089-156">Use the following command to assign resource identifiers to your localizable content.</span></span>  
  
    ```  
    msbuild /t:updateuid LocalizingWpfInWf.csproj  
    ```  
  
3.  <span data-ttu-id="83089-157">ソリューション エクスプ ローラーで、 **SimpleControl.xaml**コード エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="83089-157">In Solution Explorer, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="83089-158">\Outputfromtestproviderdebugmode.txt、`msbuild`コマンドが追加、`Uid`すべての要素に属性します。</span><span class="sxs-lookup"><span data-stu-id="83089-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="83089-159">これには、リソース識別子の割り当てを通じてローカライズが容易になります。</span><span class="sxs-lookup"><span data-stu-id="83089-159">This facilitates localization through the assignment of resource identifiers.</span></span>  
  
     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]  
  
4.  <span data-ttu-id="83089-160">F6 キーを押してソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="83089-160">Press F6 to build the solution.</span></span>  
  
## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="83089-161">LocBaml を使用して、サテライト アセンブリを生成するには</span><span class="sxs-lookup"><span data-stu-id="83089-161">Using LocBaml to Produce a Satellite Assembly</span></span>  
 <span data-ttu-id="83089-162">リソース専用で、ローカライズされたコンテンツが格納されている*サテライト アセンブリ*です。</span><span class="sxs-lookup"><span data-stu-id="83089-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="83089-163">ローカライズされたアセンブリを生成するために、コマンド ライン ツール LocBaml.exe を使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コンテンツ。</span><span class="sxs-lookup"><span data-stu-id="83089-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>  
  
#### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="83089-164">サテライト アセンブリを生成するには</span><span class="sxs-lookup"><span data-stu-id="83089-164">To produce a satellite assembly</span></span>  
  
1.  <span data-ttu-id="83089-165">LocBaml.exe をプロジェクトの obj\Debug フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="83089-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="83089-166">詳細については、次を参照してください。[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="83089-166">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>  
  
2.  <span data-ttu-id="83089-167">コマンド プロンプト ウィンドウでは、一時ファイルにリソース文字列を抽出するのに、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="83089-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>  
  
    ```  
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv  
    ```  
  
3.  <span data-ttu-id="83089-168">Temp.csv ファイルを開きます[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]などのテキスト エディター。</span><span class="sxs-lookup"><span data-stu-id="83089-168">Open the temp.csv file with [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] or another text editor.</span></span> <span data-ttu-id="83089-169">文字列を置き換える`"Hello"`スペイン語に翻訳を`"Hola"`です。</span><span class="sxs-lookup"><span data-stu-id="83089-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>  
  
4.  <span data-ttu-id="83089-170">Temp.csv ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="83089-170">Save the temp.csv file.</span></span>  
  
5.  <span data-ttu-id="83089-171">ローカライズされたリソース ファイルを生成するのにには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="83089-171">Use the following command to generate the localized resource file.</span></span>  
  
    ```  
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES  
    ```  
  
     <span data-ttu-id="83089-172">LocalizingWpfInWf.g.es ES.resources ファイルは obj\Debug フォルダーに作成されます。</span><span class="sxs-lookup"><span data-stu-id="83089-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>  
  
6.  <span data-ttu-id="83089-173">ローカライズされたサテライト アセンブリをビルドするのにには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="83089-173">Use the following command to build the localized satellite assembly.</span></span>  
  
    ```  
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources  
    ```  
  
     <span data-ttu-id="83089-174">LocalizingWpfInWf.resources.dll ファイルは obj\Debug フォルダーに作成されます。</span><span class="sxs-lookup"><span data-stu-id="83089-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>  
  
7.  <span data-ttu-id="83089-175">LocalizingWpfInWf.resources.dll ファイルをプロジェクトの bin\Debug\es ES フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="83089-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="83089-176">既存のファイルを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="83089-176">Replace the existing file.</span></span>  
  
8.  <span data-ttu-id="83089-177">プロジェクトの bin \debug フォルダーにある LocalizingWpfInWf.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="83089-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="83089-178">アプリケーションを再構築しないまたはサテライト アセンブリが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="83089-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>  
  
     <span data-ttu-id="83089-179">アプリケーションは、英語の文字列の代わりにローカライズされた文字列を示しています。</span><span class="sxs-lookup"><span data-stu-id="83089-179">The application shows the localized strings instead of the English strings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83089-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="83089-180">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="83089-181">アプリケーションをローカライズする</span><span class="sxs-lookup"><span data-stu-id="83089-181">Localize an Application</span></span>](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)  
 [<span data-ttu-id="83089-182">チュートリアル: Windows フォームのローカリゼーション</span><span class="sxs-lookup"><span data-stu-id="83089-182">Walkthrough: Localizing Windows Forms</span></span>](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)  
 [<span data-ttu-id="83089-183">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="83089-183">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
