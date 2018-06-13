---
title: 'チュートリアル : ElementHost コントロールの別の Windows フォームへのコピーと貼り付け'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 1cce981e4cb04ab6ed6ed41e0afac0121b242761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520943"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a><span data-ttu-id="6e8d5-102">チュートリアル : ElementHost コントロールの別の Windows フォームへのコピーと貼り付け</span><span class="sxs-lookup"><span data-stu-id="6e8d5-102">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>
<span data-ttu-id="6e8d5-103">このチュートリアルでは、Windows フォーム間で Windows Presentation Foundation (WPF) コントロールをコピーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-103">This walkthrough shows you how to copy a Windows Presentation Foundation (WPF) control from one Windows Form to another.</span></span>  
  
 <span data-ttu-id="6e8d5-104">このチュートリアルでは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="6e8d5-105">プロジェクトを作成する。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-105">Create the project.</span></span>  
  
-   <span data-ttu-id="6e8d5-106">WPF コントロールをコピーする。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-106">Copy a WPF Control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e8d5-107">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6e8d5-108">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6e8d5-109">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6e8d5-110">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6e8d5-110">Prerequisites</span></span>  
 <span data-ttu-id="6e8d5-111">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="6e8d5-112">。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-112">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="6e8d5-113">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="6e8d5-113">Creating the Project</span></span>  
 <span data-ttu-id="6e8d5-114">まず、Windows フォーム プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-114">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e8d5-115">WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="6e8d5-116">プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="6e8d5-116">To create the project</span></span>  
  
-   <span data-ttu-id="6e8d5-117">Visual Basic または Visual c# のという名前で新しい Windows フォーム アプリケーション プロジェクトを作成`CopyElementHost`です。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-117">Create a new Windows Forms Application project in Visual Basic or Visual C# named `CopyElementHost`.</span></span>  
  
## <a name="copying-a-wpf-control"></a><span data-ttu-id="6e8d5-118">WPF コントロールのコピー</span><span class="sxs-lookup"><span data-stu-id="6e8d5-118">Copying a WPF Control</span></span>  
 <span data-ttu-id="6e8d5-119">プロジェクトに WPF コントロールを追加した後、プロジェクト内の他のフォームにコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-119">After you add a WPF control to the project, you can copy it to other forms in the project.</span></span>  
  
#### <a name="to-copy-a-wpf-control"></a><span data-ttu-id="6e8d5-120">WPF コントロールをコピーするには</span><span class="sxs-lookup"><span data-stu-id="6e8d5-120">To copy a WPF control</span></span>  
  
1.  <span data-ttu-id="6e8d5-121">新しい WPF <xref:System.Windows.Controls.UserControl> プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-121">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="6e8d5-122">コントロール型の既定の名前である `UserControl1.xaml` を使用します。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-122">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="6e8d5-123">詳細については、次を参照してください。[チュートリアル: 新しい WPF コンテンツの作成デザイン時に Windows フォームで](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)です。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-123">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="6e8d5-124">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-124">Build the project.</span></span>  
  
3.  <span data-ttu-id="6e8d5-125">Windows フォーム デザイナーで `Form1` を開きます。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-125">Open `Form1` in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="6e8d5-126">**ツールボックス**のインスタンスをドラッグ`UserControl1`フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-126">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="6e8d5-127">`UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-127">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
5.  <span data-ttu-id="6e8d5-128">`elementHost1` を選択して、CTRL + C キーを押してクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-128">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
6.  <span data-ttu-id="6e8d5-129">新しい Windows フォームをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-129">Add a new Windows Form to the project.</span></span> <span data-ttu-id="6e8d5-130">フォームの種類の既定の名前である `Form2` を使用します。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-130">Use the default name for the form type, `Form2`.</span></span>  
  
7.  <span data-ttu-id="6e8d5-131">Windows フォーム デザイナーで `Form2` を開いたまま、CTRL キーを押しながら V キーを押して、`elementHost1` のコピーをフォームに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-131">With `Form2` open in the Windows Forms Designer, press CTRL+V to paste a copy of `elementHost1` onto the form.</span></span>  
  
     <span data-ttu-id="6e8d5-132">`Form2` クラスのプライベート フィールドであるため、コピーしたコントロールの名前も `elementHost1` です。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-132">The copied control is also named `elementHost1`, because it is a private field of the `Form2` class.</span></span> <span data-ttu-id="6e8d5-133">`Form1` クラスの `elementHost1` には名前の競合がありません。</span><span class="sxs-lookup"><span data-stu-id="6e8d5-133">There is no name collision with the `elementHost1` in the `Form1` class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e8d5-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e8d5-134">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="6e8d5-135">移行と相互運用性</span><span class="sxs-lookup"><span data-stu-id="6e8d5-135">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="6e8d5-136">WPF コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="6e8d5-136">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="6e8d5-137">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="6e8d5-137">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
