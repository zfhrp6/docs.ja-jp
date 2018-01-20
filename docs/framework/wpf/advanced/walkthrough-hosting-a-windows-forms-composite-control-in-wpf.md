---
title: "チュートリアル: WPF での Windows フォーム複合コントロールのホスト"
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
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f332461bd5abb5e3fca705a8a5fd363c3d33296
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="51df3-102">チュートリアル: WPF での Windows フォーム複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="51df3-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="51df3-103"> は、アプリケーションの作成に適した環境を提供します。</span><span class="sxs-lookup"><span data-stu-id="51df3-103"> provides a rich environment for creating applications.</span></span> <span data-ttu-id="51df3-104">ただしがある場合、かなりの投資[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]コード、だということには、少なくともを再利用すると効率的では、そのコードの一部、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションではなく最初から書き換えをします。</span><span class="sxs-lookup"><span data-stu-id="51df3-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="51df3-105">最も一般的なシナリオは、既存のある場合[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="51df3-105">The most common scenario is when you have existing [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] controls.</span></span> <span data-ttu-id="51df3-106">場合によっては、するがありますいないでもこれらのコントロールのソース コードへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="51df3-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="51df3-107">このようなコントロールをホストするため、簡単な手順を提供する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="51df3-107"> provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="51df3-108">たとえば、使用することができます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、特殊なをホストしているときに、プログラミングのほとんどの<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="51df3-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="51df3-109">このチュートリアル手順を説明してアプリケーションをホストする、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]複合コントロールでのデータ入力を実行する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="51df3-109">This walkthrough steps you through an application that hosts a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="51df3-110">複合コントロールは DLL にパッケージ化されています。</span><span class="sxs-lookup"><span data-stu-id="51df3-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="51df3-111">この一般的な手順は、より複雑なアプリケーションやコントロールに拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="51df3-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="51df3-112">このチュートリアルは、外観と機能をほぼ同一である[チュートリアル: Windows フォームで WPF 複合コントロールをホストしている](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="51df3-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="51df3-113">主な違いは、ホストする側とされる側が逆であることです。</span><span class="sxs-lookup"><span data-stu-id="51df3-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="51df3-114">このチュートリアルは、2 つのセクションに分かれています。</span><span class="sxs-lookup"><span data-stu-id="51df3-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="51df3-115">最初のセクションの実装をについて簡単に説明する、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]複合コントロール。</span><span class="sxs-lookup"><span data-stu-id="51df3-115">The first section briefly describes the implementation of the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control.</span></span> <span data-ttu-id="51df3-116">2 番目のセクションで詳しく複合コントロールをホストする方法について説明します、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション、コントロールからイベントを受け取るし、コントロールのプロパティの一部にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="51df3-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="51df3-117">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="51df3-117">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="51df3-118">Windows フォームの複合コントロールを実装します。</span><span class="sxs-lookup"><span data-stu-id="51df3-118">Implementing the Windows Forms composite control.</span></span>  
  
-   <span data-ttu-id="51df3-119">WPF のホスト アプリケーションを実装します。</span><span class="sxs-lookup"><span data-stu-id="51df3-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="51df3-120">このチュートリアルでタスクの完全なコードについては、次を参照してください。 [WPF サンプルでは、Windows フォームの複合コントロールをホストしている](http://go.microsoft.com/fwlink/?LinkID=159999)です。</span><span class="sxs-lookup"><span data-stu-id="51df3-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="51df3-121">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="51df3-121">Prerequisites</span></span>  
 <span data-ttu-id="51df3-122">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="51df3-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="51df3-123">。</span><span class="sxs-lookup"><span data-stu-id="51df3-123">.</span></span>  
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="51df3-124">Windows フォームの複合コントロールを実装します。</span><span class="sxs-lookup"><span data-stu-id="51df3-124">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="51df3-125">[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]この例で使用される複合コントロールは、単純なデータ エントリ フォーム。</span><span class="sxs-lookup"><span data-stu-id="51df3-125">The [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="51df3-126">このフォームは、ユーザーの名前とアドレスを受け取りし、カスタム イベントを使用してホストにその情報を返します。</span><span class="sxs-lookup"><span data-stu-id="51df3-126">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="51df3-127">次の図はレンダリングされたコントロールを示しています。</span><span class="sxs-lookup"><span data-stu-id="51df3-127">The following illustration shows the rendered control.</span></span>  
  
 <span data-ttu-id="51df3-128">![単純な Windows フォーム コントロールの](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span><span class="sxs-lookup"><span data-stu-id="51df3-128">![Simple Windows Forms control](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span></span>  
<span data-ttu-id="51df3-129">Windows フォームの複合コントロール</span><span class="sxs-lookup"><span data-stu-id="51df3-129">Windows Forms composite control</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="51df3-130">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="51df3-130">Creating the Project</span></span>  
 <span data-ttu-id="51df3-131">プロジェクトを開始するには</span><span class="sxs-lookup"><span data-stu-id="51df3-131">To start the project:</span></span>  
  
1.  <span data-ttu-id="51df3-132">起動[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、開き、**新しいプロジェクト** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="51df3-132">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="51df3-133">[ウィンドウ] カテゴリの選択、 **Windows フォーム コントロール ライブラリ**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="51df3-133">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3.  <span data-ttu-id="51df3-134">新しいプロジェクトに `MyControls` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="51df3-134">Name the new project `MyControls`.</span></span>  
  
4.  <span data-ttu-id="51df3-135">場所についてを指定して、簡単に名前付きのトップレベルのフォルダーなど`WpfHostingWindowsFormsControl`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-135">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="51df3-136">このフォルダーには後でホスト アプリケーションも配置します。</span><span class="sxs-lookup"><span data-stu-id="51df3-136">Later, you will put the host application in this folder.</span></span>  
  
5.  <span data-ttu-id="51df3-137">をクリックして**OK**プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="51df3-137">Click **OK** to create the project.</span></span> <span data-ttu-id="51df3-138">既定のプロジェクトには、という名前の 1 つのコントロールが含まれています。`UserControl1`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-138">The default project contains a single control named `UserControl1`.</span></span>  
  
6.  <span data-ttu-id="51df3-139">ソリューション エクスプ ローラーで、名前を変更`UserControl1`に`MyControl1`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-139">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="51df3-140">プロジェクトは、以下のシステム DLL を参照している必要があります。</span><span class="sxs-lookup"><span data-stu-id="51df3-140">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="51df3-141">既定で含まれていないこれらの Dll のいずれかの場合は、プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="51df3-141">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
-   <span data-ttu-id="51df3-142">システム</span><span class="sxs-lookup"><span data-stu-id="51df3-142">System</span></span>  
  
-   <span data-ttu-id="51df3-143">System.Data</span><span class="sxs-lookup"><span data-stu-id="51df3-143">System.Data</span></span>  
  
-   <span data-ttu-id="51df3-144">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="51df3-144">System.Drawing</span></span>  
  
-   <span data-ttu-id="51df3-145">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="51df3-145">System.Windows.Forms</span></span>  
  
-   <span data-ttu-id="51df3-146">System.Xml</span><span class="sxs-lookup"><span data-stu-id="51df3-146">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="51df3-147">フォームへのコントロールの追加</span><span class="sxs-lookup"><span data-stu-id="51df3-147">Adding Controls to the Form</span></span>  
 <span data-ttu-id="51df3-148">フォームにコントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="51df3-148">To add controls to the form:</span></span>  
  
-   <span data-ttu-id="51df3-149">開いている`MyControl1`デザイナーでします。</span><span class="sxs-lookup"><span data-stu-id="51df3-149">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="51df3-150">5 個追加<xref:System.Windows.Forms.Label>コントロールとそれに対応する<xref:System.Windows.Forms.TextBox>コントロール、サイズ設定およびフォームで、前の図のように配置されます。</span><span class="sxs-lookup"><span data-stu-id="51df3-150">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="51df3-151">この例で、<xref:System.Windows.Forms.TextBox>コントロールの名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="51df3-151">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 <span data-ttu-id="51df3-152">2 つ追加<xref:System.Windows.Forms.Button>ラベル コントロール**OK**と**キャンセル**です。</span><span class="sxs-lookup"><span data-stu-id="51df3-152">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="51df3-153">ボタン名は、例では、`btnOK`と`btnCancel`、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="51df3-153">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="51df3-154">サポート コードの実装</span><span class="sxs-lookup"><span data-stu-id="51df3-154">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="51df3-155">コード ビューで、フォームを開きます。</span><span class="sxs-lookup"><span data-stu-id="51df3-155">Open the form in code view.</span></span> <span data-ttu-id="51df3-156">コントロールがそのホストにカスタムを発生させることによって、収集したデータを返します`OnButtonClick`イベント。</span><span class="sxs-lookup"><span data-stu-id="51df3-156">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="51df3-157">データは、イベント引数オブジェクトに含まれます。</span><span class="sxs-lookup"><span data-stu-id="51df3-157">The data is contained in the event argument object.</span></span> <span data-ttu-id="51df3-158">次のコードは、イベントおよびデリゲートの宣言を示しています。</span><span class="sxs-lookup"><span data-stu-id="51df3-158">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="51df3-159">`MyControl1` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="51df3-159">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 <span data-ttu-id="51df3-160">`MyControlEventArgs`クラスには、ホストに返される情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="51df3-160">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>  
  
 <span data-ttu-id="51df3-161">フォームに次のクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="51df3-161">Add the following class to the form.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 <span data-ttu-id="51df3-162">ユーザーがクリックしたとき、 **[ok]**または**キャンセル**ボタン、<xref:System.Windows.Forms.Control.Click>イベント ハンドラーを作成、`MyControlEventArgs`データを格納しているオブジェクトを生成し、`OnButtonClick`イベント。</span><span class="sxs-lookup"><span data-stu-id="51df3-162">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="51df3-163">2 つのハンドラーの唯一の違いは、イベント引数の`IsOK`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="51df3-163">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="51df3-164">このプロパティは、ホストがクリックしてされたボタンを決定できます。</span><span class="sxs-lookup"><span data-stu-id="51df3-164">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="51df3-165">設定されている`true`の**[ok]**ボタン、および`false`の**キャンセル**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51df3-165">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="51df3-166">次のコードは、次の 2 つのボタン ハンドラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="51df3-166">The following code shows the two button handlers.</span></span>  
  
 <span data-ttu-id="51df3-167">`MyControl1` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="51df3-167">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="51df3-168">アセンブリに厳密な名前を付けると、アセンブリのビルド</span><span class="sxs-lookup"><span data-stu-id="51df3-168">Giving the Assembly a Strong Name and Building the Assembly</span></span>  
 <span data-ttu-id="51df3-169">このアセンブリによって参照されていること、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション、厳密な名前を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="51df3-169">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="51df3-170">厳密な名前を作成するに Sn.exe のキー ファイルを作成し、プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="51df3-170">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>  
  
1.  <span data-ttu-id="51df3-171">[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="51df3-171">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="51df3-172">これを行うには、をクリックして、**開始**メニューをクリックして**すべてプログラム/Microsoft Visual Studio 2010 または Visual Studio Tools と Visual Studio コマンド プロンプト**です。</span><span class="sxs-lookup"><span data-stu-id="51df3-172">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="51df3-173">これは、カスタマイズされた環境変数とコンソール ウィンドウを起動します。</span><span class="sxs-lookup"><span data-stu-id="51df3-173">This launches a console window with customized environment variables.</span></span>  
  
2.  <span data-ttu-id="51df3-174">コマンド プロンプトを使用して、`cd`コマンドをプロジェクト フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="51df3-174">At the command prompt, use the `cd` command to go to your project folder.</span></span>  
  
3.  <span data-ttu-id="51df3-175">次のコマンドを実行して MyControls.snk をという名前のキー ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="51df3-175">Generate a key file named MyControls.snk by running the following command.</span></span>  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  <span data-ttu-id="51df3-176">キー ファイルをプロジェクトに含める、ソリューション エクスプ ローラーでプロジェクト名を右クリックし、をクリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="51df3-176">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="51df3-177">プロジェクト デザイナーで、をクリックして、**署名**] タブで、[、**アセンブリに署名**チェック ボックスをオンし、キー ファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="51df3-177">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>  
  
5.  <span data-ttu-id="51df3-178">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="51df3-178">Build the solution.</span></span> <span data-ttu-id="51df3-179">ビルドでは、MyControls.dll という名前の DLL が生成されます。</span><span class="sxs-lookup"><span data-stu-id="51df3-179">The build will produce a DLL named MyControls.dll.</span></span>  
  
## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="51df3-180">WPF のホスト アプリケーションの実装</span><span class="sxs-lookup"><span data-stu-id="51df3-180">Implementing the WPF Host Application</span></span>  
 <span data-ttu-id="51df3-181">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ホスト アプリケーションで使用する、<xref:System.Windows.Forms.Integration.WindowsFormsHost>コントロールをホストに`MyControl1`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-181">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="51df3-182">アプリケーションのハンドル、`OnButtonClick`コントロールからデータを受信するイベントです。</span><span class="sxs-lookup"><span data-stu-id="51df3-182">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="51df3-183">さらから、コントロールのプロパティの一部を変更するためのオプション ボタンのコレクション、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="51df3-183">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="51df3-184">次の図は、完成したアプリケーションを示します。</span><span class="sxs-lookup"><span data-stu-id="51df3-184">The following illustration shows the finished application.</span></span>  
  
 <span data-ttu-id="51df3-185">![WPF ページに埋め込まれたコントロール](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span><span class="sxs-lookup"><span data-stu-id="51df3-185">![A control embedded in a WPF page](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span></span>  
<span data-ttu-id="51df3-186">完全なアプリケーションでは、コントロールを表示する WPF アプリケーションに埋め込まれています。</span><span class="sxs-lookup"><span data-stu-id="51df3-186">The complete application, showing the control embedded in the WPF application</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="51df3-187">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="51df3-187">Creating the Project</span></span>  
 <span data-ttu-id="51df3-188">プロジェクトを開始するには</span><span class="sxs-lookup"><span data-stu-id="51df3-188">To start the project:</span></span>  
  
1.  <span data-ttu-id="51df3-189">開いている[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]を選択して**新しいプロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="51df3-189">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>  
  
2.  <span data-ttu-id="51df3-190">[ウィンドウ] カテゴリの選択、 **WPF アプリケーション**テンプレート。</span><span class="sxs-lookup"><span data-stu-id="51df3-190">In the Window category, select the **WPF Application** template.</span></span>
  
3.  <span data-ttu-id="51df3-191">新しいプロジェクトに `WpfHost` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="51df3-191">Name the new project `WpfHost`.</span></span>  
  
4.  <span data-ttu-id="51df3-192">配置場所として、MyControls の配置先と同じ最上位フォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="51df3-192">For the location, specify the same top-level folder that contains the MyControls project.</span></span>  
  
5.  <span data-ttu-id="51df3-193">をクリックして**OK**プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="51df3-193">Click **OK** to create the project.</span></span>  
  
 <span data-ttu-id="51df3-194">含む DLL への参照を追加する必要があります`MyControl1`およびその他のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="51df3-194">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>  
  
1.  <span data-ttu-id="51df3-195">ソリューション エクスプ ローラーでプロジェクト名を右クリックし **参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="51df3-195">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="51df3-196">クリックして、**参照**タブをクリックし、MyControls.dll を含まれているフォルダーを参照します。</span><span class="sxs-lookup"><span data-stu-id="51df3-196">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="51df3-197">このチュートリアルの場合は、MyControls\bin\Debug フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="51df3-197">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="51df3-198">MyControls.dll を選択し、クリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="51df3-198">Select MyControls.dll, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="51df3-199">WindowsFormsIntegration.dll と呼ばれる WindowsFormsIntegration アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="51df3-199">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
### <a name="implementing-the-basic-layout"></a><span data-ttu-id="51df3-200">基本的なレイアウトを実装します。</span><span class="sxs-lookup"><span data-stu-id="51df3-200">Implementing the Basic Layout</span></span>  
 <span data-ttu-id="51df3-201">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] MainWindow.xaml で、ホストのアプリケーションを実装します。</span><span class="sxs-lookup"><span data-stu-id="51df3-201">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="51df3-202">このファイルを含む[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]レイアウトを定義しをホストするマークアップを[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]コントロール。</span><span class="sxs-lookup"><span data-stu-id="51df3-202">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control.</span></span> <span data-ttu-id="51df3-203">アプリケーションは、3 つの領域に分かれています。</span><span class="sxs-lookup"><span data-stu-id="51df3-203">The application is divided into three regions:</span></span>  
  
-   <span data-ttu-id="51df3-204">**コントロール プロパティ**パネルで、ホストされるコントロールのさまざまなプロパティを変更に使用できるオプション ボタンのコレクションを格納します。</span><span class="sxs-lookup"><span data-stu-id="51df3-204">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>  
  
-   <span data-ttu-id="51df3-205">**コントロールからのデータ**パネルで、いくつか示します<xref:System.Windows.Controls.TextBlock>ホストされるコントロールからデータを表示する要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="51df3-205">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>  
  
-   <span data-ttu-id="51df3-206">ホストされるコントロール自体です。</span><span class="sxs-lookup"><span data-stu-id="51df3-206">The hosted control itself.</span></span>  
  
 <span data-ttu-id="51df3-207">次の XAML では、基本的なレイアウトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="51df3-207">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="51df3-208">必要なマークアップをホストに`MyControl1`はからこの例では、省略されたものの、後で説明されています。</span><span class="sxs-lookup"><span data-stu-id="51df3-208">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>  
  
 <span data-ttu-id="51df3-209">次の MainWindow.xaml で XAML に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="51df3-209">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="51df3-210">Visual Basic を使用している場合にクラスを変更`x:Class="MainWindow"`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-210">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 <span data-ttu-id="51df3-211">最初の<xref:System.Windows.Controls.StackPanel>要素には、複数のセットが含まれています。<xref:System.Windows.Controls.RadioButton>ホストされるコントロールのさまざまな既定のプロパティを変更することができるようにするコントロール。</span><span class="sxs-lookup"><span data-stu-id="51df3-211">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="51df3-212">後に、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素、どのホスト`MyControl1`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-212">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="51df3-213">最終的な<xref:System.Windows.Controls.StackPanel>要素では、いくつか含まれています<xref:System.Windows.Controls.TextBlock>ホストされるコントロールによって返されるデータを表示する要素。</span><span class="sxs-lookup"><span data-stu-id="51df3-213">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="51df3-214">要素の順序と<xref:System.Windows.Controls.DockPanel.Dock%2A>と<xref:System.Windows.FrameworkElement.Height%2A>属性の設定は、ギャップや歪みなしで、ウィンドウにホストされるコントロールを埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="51df3-214">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>  
  
#### <a name="hosting-the-control"></a><span data-ttu-id="51df3-215">コントロールをホストしています。</span><span class="sxs-lookup"><span data-stu-id="51df3-215">Hosting the Control</span></span>  
 <span data-ttu-id="51df3-216">次の編集したバージョン以前の XAML のについて重点的に必要な要素をホストに`MyControl1`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-216">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 <span data-ttu-id="51df3-217">`xmlns`名前空間のマッピング属性への参照を作成する、`MyControls`ホストされるコントロールを含む名前空間です。</span><span class="sxs-lookup"><span data-stu-id="51df3-217">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="51df3-218">このマッピングを使用すると、表す`MyControl1`で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]として`<mcl:MyControl1>`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-218">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>  
  
 <span data-ttu-id="51df3-219">XAML での 2 つの要素は、ホスティングを処理します。</span><span class="sxs-lookup"><span data-stu-id="51df3-219">Two elements in the XAML handle the hosting:</span></span>  
  
-   <span data-ttu-id="51df3-220">`WindowsFormsHost`表す、<xref:System.Windows.Forms.Integration.WindowsFormsHost>ホストに使用すると要素、[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]内の制御、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="51df3-220">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
-   <span data-ttu-id="51df3-221">`mcl:MyControl1`、を表す`MyControl1`、に追加、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の子のコレクション。</span><span class="sxs-lookup"><span data-stu-id="51df3-221">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="51df3-222">その結果、この[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]の一部としてコントロールを表示、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ウィンドウ、およびするが、アプリケーションからコントロールと通信できます。</span><span class="sxs-lookup"><span data-stu-id="51df3-222">As a result, this [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>  
  
### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="51df3-223">分離コード ファイルの実装</span><span class="sxs-lookup"><span data-stu-id="51df3-223">Implementing the Code-Behind File</span></span>  
 <span data-ttu-id="51df3-224">MainWindow.xaml.vb または MainWindow.xaml.cs で、分離コード ファイルには、機能を実装する手順のコードが含まれています、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]前のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="51df3-224">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="51df3-225">主要なタスクは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="51df3-225">The primary tasks are:</span></span>  
  
-   <span data-ttu-id="51df3-226">イベント ハンドラーをアタッチする`MyControl1`の`OnButtonClick`イベント。</span><span class="sxs-lookup"><span data-stu-id="51df3-226">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>  
  
-   <span data-ttu-id="51df3-227">さまざまなプロパティを変更する`MyControl1`オプション ボタンのコレクションを設定する方法に基づきます。</span><span class="sxs-lookup"><span data-stu-id="51df3-227">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>  
  
-   <span data-ttu-id="51df3-228">コントロールによって収集されたデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="51df3-228">Displaying the data collected by the control.</span></span>  
  
#### <a name="initializing-the-application"></a><span data-ttu-id="51df3-229">アプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="51df3-229">Initializing the Application</span></span>  
 <span data-ttu-id="51df3-230">ウィンドウのイベント ハンドラーの初期化コードが含まれている<xref:System.Windows.FrameworkElement.Loaded>イベントをコントロールのイベント ハンドラーをアタッチおよび`OnButtonClick`イベント。</span><span class="sxs-lookup"><span data-stu-id="51df3-230">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>  
  
 <span data-ttu-id="51df3-231">MainWindow.xaml.vb または MainWindow.xaml.cs で、次のコードを追加、`MainWindow`クラスです。</span><span class="sxs-lookup"><span data-stu-id="51df3-231">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 <span data-ttu-id="51df3-232">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]以前に追加された説明`MyControl1`を<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の子要素のコレクションをキャストすること、<xref:System.Windows.Forms.Integration.WindowsFormsHost>要素の<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>への参照を取得する`MyControl1`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-232">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="51df3-233">イベント ハンドラーをアタッチする、その参照を使用することができますし、`OnButtonClick`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-233">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>  
  
 <span data-ttu-id="51df3-234">コントロール自体への参照を提供するだけでなく<xref:System.Windows.Forms.Integration.WindowsFormsHost>は、アプリケーションから操作できるは、コントロールのプロパティの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="51df3-234">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="51df3-235">初期化コードは、後で使用するアプリケーションでのグローバル変数をプライベートにそれらの値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="51df3-235">The initialization code assigns those values to private global variables for later use in the application.</span></span>  
  
 <span data-ttu-id="51df3-236">内の型を簡単にアクセスできるように、 `MyControls` DLL、次の追加`Imports`または`using`ステートメント ファイルの先頭にします。</span><span class="sxs-lookup"><span data-stu-id="51df3-236">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="51df3-237">OnButtonClick イベントの処理</span><span class="sxs-lookup"><span data-stu-id="51df3-237">Handling the OnButtonClick Event</span></span>  
 <span data-ttu-id="51df3-238">`MyControl1`発生させる、`OnButtonClick`イベント、ユーザーがコントロールのボタンのいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51df3-238">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>  
  
 <span data-ttu-id="51df3-239">`MainWindow` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="51df3-239">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 <span data-ttu-id="51df3-240">テキスト ボックス内のデータがパック、`MyControlEventArgs`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="51df3-240">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="51df3-241">ユーザーがクリックした場合、 **OK**ボタン、イベント ハンドラーは、データを抽出し、下のパネルの表示`MyControl1`です。</span><span class="sxs-lookup"><span data-stu-id="51df3-241">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>  
  
#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="51df3-242">コントロールのプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="51df3-242">Modifying the Control’s Properties</span></span>  
 <span data-ttu-id="51df3-243"><xref:System.Windows.Forms.Integration.WindowsFormsHost>要素がいくつかのホストされるコントロールの既定のプロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="51df3-243">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="51df3-244">その結果、アプリケーションのスタイルをより厳密に一致するようにコントロールの外観を変更できます。</span><span class="sxs-lookup"><span data-stu-id="51df3-244">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="51df3-245">左側のパネルでオプション ボタンのセットには、いくつかの色とフォントのプロパティを変更するユーザーが有効にします。</span><span class="sxs-lookup"><span data-stu-id="51df3-245">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="51df3-246">ボタンの各セットのハンドラーがある、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントでは、ユーザーのオプション ボタンの選択肢を検出し、コントロールに対応するプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="51df3-246">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>  
  
 <span data-ttu-id="51df3-247">`MainWindow` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="51df3-247">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="51df3-248">アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="51df3-248">Build and run the application.</span></span> <span data-ttu-id="51df3-249">Windows フォームの複合コントロールのいくつかのテキストを追加し、クリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="51df3-249">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="51df3-250">そのテキストがラベルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="51df3-250">The text appears in the labels.</span></span> <span data-ttu-id="51df3-251">コントロールへの影響を表示する別のオプション ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="51df3-251">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51df3-252">参照</span><span class="sxs-lookup"><span data-stu-id="51df3-252">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="51df3-253">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="51df3-253">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="51df3-254">チュートリアル: WPF での Windows フォーム コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="51df3-254">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="51df3-255">チュートリアル: Windows フォームでの WPF 複合コントロールのホスト</span><span class="sxs-lookup"><span data-stu-id="51df3-255">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
