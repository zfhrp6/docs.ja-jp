---
title: "チュートリアル: Windows フォーム アプリケーションでのデータフローの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d2775cc99020fd99d6e7d79cdf3e1ffcc3219146
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a><span data-ttu-id="e7cbb-102">チュートリアル: Windows フォーム アプリケーションでのデータフローの使用</span><span class="sxs-lookup"><span data-stu-id="e7cbb-102">Walkthrough: Using Dataflow in a Windows Forms Application</span></span>
<span data-ttu-id="e7cbb-103">このドキュメントでは、Windows フォーム アプリケーションでイメージ処理を実行する、データフロー ブロックのネットワークを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-103">This document demonstrates how to create a network of dataflow blocks that perform image processing in a Windows Forms application.</span></span>  
  
 <span data-ttu-id="e7cbb-104">この例では、指定したフォルダーからイメージ ファイルを読み込み、複合イメージを作成して、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-104">This example loads image files from the specified folder, creates a composite image, and displays the result.</span></span> <span data-ttu-id="e7cbb-105">例では、ネットワーク経由でイメージをルーティングするために、データフロー モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-105">The example uses the dataflow model to route images through the network.</span></span> <span data-ttu-id="e7cbb-106">このデータフロー モデルでは、プログラム内の独立したコンポーネント同士が、メッセージを送信することによって相互に通信します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-106">In the dataflow model, independent components of a program communicate with one another by sending messages.</span></span> <span data-ttu-id="e7cbb-107">1 つのコンポーネントがメッセージを受信すると、何らかのアクションを実行した後に、結果を別のコンポーネントに渡します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-107">When a component receives a message, it performs some action and then passes the result to another component.</span></span> <span data-ttu-id="e7cbb-108">このモデルと制御フロー モデルを比較してください。制御フロー モデルでは、アプリケーションは制御構造 (条件付きステートメントやループなど) を使用してプログラムでの操作順序を制御します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-108">Compare this with the control flow model, in which an application uses control structures, for example, conditional statements, loops, and so on, to control the order of operations in a program.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e7cbb-109">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e7cbb-109">Prerequisites</span></span>  
 <span data-ttu-id="e7cbb-110">このチュートリアルを開始する前に、「[Dataflow (データフロー)](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)」をお読みください。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-110">Read [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) before you start this walkthrough.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="e7cbb-111">TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-111">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="e7cbb-112">インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-112">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
 
  
## <a name="sections"></a><span data-ttu-id="e7cbb-113">セクション</span><span class="sxs-lookup"><span data-stu-id="e7cbb-113">Sections</span></span>  
 <span data-ttu-id="e7cbb-114">このチュートリアルは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-114">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="e7cbb-115">Windows フォーム アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="e7cbb-115">Creating the Windows Forms Application</span></span>](#winforms)  
  
-   [<span data-ttu-id="e7cbb-116">データフロー ネットワークの作成</span><span class="sxs-lookup"><span data-stu-id="e7cbb-116">Creating the Dataflow Network</span></span>](#network)  
  
-   [<span data-ttu-id="e7cbb-117">ユーザー インターフェイスへのデータフロー ネットワークの接続</span><span class="sxs-lookup"><span data-stu-id="e7cbb-117">Connecting the Dataflow Network to the User Interface</span></span>](#ui)  
  
-   [<span data-ttu-id="e7cbb-118">コード例全体</span><span class="sxs-lookup"><span data-stu-id="e7cbb-118">The Complete Example</span></span>](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a><span data-ttu-id="e7cbb-119">Windows フォーム アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="e7cbb-119">Creating the Windows Forms Application</span></span>  
 <span data-ttu-id="e7cbb-120">このセクションでは、基本的な Windows フォーム アプリケーションを作成し、メイン フォームにコントロールを追加する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-120">This section describes how to create the basic Windows Forms application and add controls to the main form.</span></span>  
  
#### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="e7cbb-121">Windows フォーム アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="e7cbb-121">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="e7cbb-122">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で、[!INCLUDE[csprcs](../../../includes/csprcs-md.md)] または Visual Basic **Windows フォーム アプリケーション** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-122">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], create a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="e7cbb-123">このドキュメントでは、プロジェクトの名前を `CompositeImages` とします。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-123">In this document, the project is named `CompositeImages`.</span></span>  
  
2.  <span data-ttu-id="e7cbb-124">メイン フォーム Form1.cs のフォーム デザイナーで (の Form1.vb [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])、追加、<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-124">On the form designer for the main form, Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="e7cbb-125">追加、<xref:System.Windows.Forms.ToolStripButton>コントロールを<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-125">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="e7cbb-126">設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>と<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを**フォルダーを選択**です。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-126">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Choose Folder**.</span></span>  
  
4.  <span data-ttu-id="e7cbb-127">1 秒あたりの追加<xref:System.Windows.Forms.ToolStripButton>コントロールを<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-127">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="e7cbb-128">設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>、<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを**キャンセル**、および<xref:System.Windows.Forms.ToolStripItem.Enabled%2A>プロパティを`False`です。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-128">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="e7cbb-129">追加、<xref:System.Windows.Forms.PictureBox>メイン フォームにオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-129">Add a <xref:System.Windows.Forms.PictureBox> object to the main form.</span></span> <span data-ttu-id="e7cbb-130"><xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill> に設定します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-130">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a><span data-ttu-id="e7cbb-131">データフロー ネットワークの作成</span><span class="sxs-lookup"><span data-stu-id="e7cbb-131">Creating the Dataflow Network</span></span>  
 <span data-ttu-id="e7cbb-132">このセクションでは、イメージ処理を実行するデータフロー ネットワークを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-132">This section describes how to create the dataflow network that performs image processing.</span></span>  
  
#### <a name="to-create-the-dataflow-network"></a><span data-ttu-id="e7cbb-133">データフロー ネットワークを作成するには</span><span class="sxs-lookup"><span data-stu-id="e7cbb-133">To Create the Dataflow Network</span></span>  
  
1.  <span data-ttu-id="e7cbb-134">System.Threading.Tasks.Dataflow.dll への参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-134">Add a reference to System.Threading.Tasks.Dataflow.dll to your project.</span></span>  
  
2.  <span data-ttu-id="e7cbb-135">Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では Form1.vb) に次の `using` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `Using`) ステートメントが含まれることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-135">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` (`Using` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) statements:</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  <span data-ttu-id="e7cbb-136">`Form1` クラスに次のデータ メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-136">Add the following data members to the `Form1` class:</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  <span data-ttu-id="e7cbb-137">次の `CreateImageProcessingNetwork` メソッドを `Form1` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-137">Add the following method, `CreateImageProcessingNetwork`, to the `Form1` class.</span></span> <span data-ttu-id="e7cbb-138">このメソッドによって、イメージ処理ネットワークが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-138">This method creates the image processing network.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  <span data-ttu-id="e7cbb-139">`LoadBitmaps` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-139">Implement the `LoadBitmaps` method.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  <span data-ttu-id="e7cbb-140">`CreateCompositeBitmap` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-140">Implement the `CreateCompositeBitmap` method.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  <span data-ttu-id="e7cbb-141">C# バージョンの`CreateCompositeBitmap`メソッドでは、ポインターを使用して効率的に処理を有効にする、<xref:System.Drawing.Bitmap?displayProperty=nameWithType>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-141">The C# version of the `CreateCompositeBitmap` method uses pointers to enable efficient processing of the <xref:System.Drawing.Bitmap?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="e7cbb-142">したがって、[unsafe](~/docs/csharp/language-reference/keywords/unsafe.md) キーワードを使用するために、プロジェクト内の **[アンセーフ コードの許可]** オプションを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-142">Therefore, you must enable the **Allow unsafe code** option in your project in order to use the [unsafe](~/docs/csharp/language-reference/keywords/unsafe.md) keyword.</span></span> <span data-ttu-id="e7cbb-143">アンセーフ コードを有効にする方法について、[!INCLUDE[csprcs](../../../includes/csprcs-md.md)]プロジェクトで、[ビルド ページ、プロジェクト デザイナー (c#)] を参照してください https://msdn.microsoft.com/library/kb4wyys2)。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-143">For more information about how to enable unsafe code in a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] project, see [Build Page, Project Designer (C#)]https://msdn.microsoft.com/library/kb4wyys2).</span></span>  
  
 <span data-ttu-id="e7cbb-144">ネットワークのメンバーを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-144">The following table describes the members of the network.</span></span>  
  
|<span data-ttu-id="e7cbb-145">メンバー</span><span class="sxs-lookup"><span data-stu-id="e7cbb-145">Member</span></span>|<span data-ttu-id="e7cbb-146">型</span><span class="sxs-lookup"><span data-stu-id="e7cbb-146">Type</span></span>|<span data-ttu-id="e7cbb-147">説明</span><span class="sxs-lookup"><span data-stu-id="e7cbb-147">Description</span></span>|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="e7cbb-148">フォルダー パスを入力として受け取りのコレクションを生成<xref:System.Drawing.Bitmap>オブジェクトとして出力します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-148">Takes a folder path as input and produces a collection of <xref:System.Drawing.Bitmap> objects as output.</span></span>|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|<span data-ttu-id="e7cbb-149">コレクションを受け取って<xref:System.Drawing.Bitmap>オブジェクトを入力としてし、出力として複合ビットマップを生成します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-149">Takes a collection of <xref:System.Drawing.Bitmap> objects as input and produces a composite bitmap as output.</span></span>|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="e7cbb-150">フォーム上に複合ビットマップを表示します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-150">Displays the composite bitmap on the form.</span></span>|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|<span data-ttu-id="e7cbb-151">操作が取り消されたことを示すためにイメージを表示し、ユーザーが別のフォルダーを選択できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-151">Displays an image to indicate that the operation is canceled and enables the user to select another folder.</span></span>|  
  
 <span data-ttu-id="e7cbb-152">この例では、ネットワークを形成するデータフロー ブロックを接続するには<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-152">To connect the dataflow blocks to form a network, this example uses the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method.</span></span> <span data-ttu-id="e7cbb-153"><xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>メソッドには受け取るオーバー ロードされたバージョンが含まれています、<xref:System.Predicate%601>ターゲット ブロックが受け入れるか、メッセージを拒否するかどうかを決定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-153">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method contains an overloaded version that takes a <xref:System.Predicate%601> object that determines whether the target block accepts or rejects a message.</span></span> <span data-ttu-id="e7cbb-154">このフィルターのしくみによって、メッセージ ブロックは特定の値のみを受信できます。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-154">This filtering mechanism enables message blocks to receive only certain values.</span></span> <span data-ttu-id="e7cbb-155">この例では、ネットワークが、2 つに分岐します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-155">In this example, the network can branch in one of two ways.</span></span> <span data-ttu-id="e7cbb-156">メイン分岐は、ディスクからイメージを読み込み、複合イメージを作成し、フォームにそのイメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-156">The main branch loads the images from disk, creates the composite image, and displays that image on the form.</span></span> <span data-ttu-id="e7cbb-157">もう 1 つの分岐では、現在の操作がキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-157">The alternate branch cancels the current operation.</span></span> <span data-ttu-id="e7cbb-158"><xref:System.Predicate%601>オブジェクトが特定のメッセージを拒否することによって、別の分岐を切り替えるには、メイン分岐に沿ったデータ フロー ブロックを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-158">The <xref:System.Predicate%601> objects enable the dataflow blocks along the main branch to switch to the alternative branch by rejecting certain messages.</span></span> <span data-ttu-id="e7cbb-159">たとえば、ユーザーが操作をキャンセルした場合、データフロー ブロック `createCompositeBitmap` で、`null`([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `Nothing`) が出力として生成されます。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-159">For example, if the user cancels the operation, the dataflow block `createCompositeBitmap` produces `null` (`Nothing` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) as its output.</span></span> <span data-ttu-id="e7cbb-160">データフロー ブロック `displayCompositeBitmap` では、`null` 入力値が拒否されるため、メッセージが `operationCancelled` に提供されます。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-160">The dataflow block `displayCompositeBitmap` rejects `null` input values, and therefore, the message is offered to `operationCancelled`.</span></span> <span data-ttu-id="e7cbb-161">データフロー ブロック `operationCancelled` はすべてのメッセージを受け入れるため、操作が取り消されたことを示すためにイメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-161">The dataflow block `operationCancelled` accepts all messages and therefore, displays an image to indicate that the operation is canceled.</span></span>  
  
 <span data-ttu-id="e7cbb-162">次の図は、イメージ処理ネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-162">The following illustration shows the image processing network.</span></span>  
  
 <span data-ttu-id="e7cbb-163">![イメージ処理ネットワーク](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")</span><span class="sxs-lookup"><span data-stu-id="e7cbb-163">![The image processing network](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")</span></span>  
  
 <span data-ttu-id="e7cbb-164">`displayCompositeBitmap` と `operationCancelled` のデータフロー ブロックはユーザー インターフェイスで機能するので、これらの操作をユーザー インターフェイス スレッドで実行することが重要です。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-164">Because the `displayCompositeBitmap` and `operationCancelled` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="e7cbb-165">これを実現する、構築時に、これらのオブジェクトは各の提供、<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>を持つオブジェクト、<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A>プロパティに設定<xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-165">To accomplish this, during construction, these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e7cbb-166"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> メソッドは、現行の同期コンテキストで作業を実行する <xref:System.Threading.Tasks.TaskScheduler> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-166">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="e7cbb-167">ユーザー インターフェイス スレッドで実行される`CreateImageProcessingNetwork` メソッドは、**[フォルダーの選択]** ボタンのハンドラーから呼び出されるため、`displayCompositeBitmap` と`operationCancelled` のデータフロー ブロックのアクションも、ユーザー インターフェイス スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-167">Because the `CreateImageProcessingNetwork` method is called from the handler of the **Choose Folder** button, which runs on the user-interface thread, the actions for the `displayCompositeBitmap` and `operationCancelled` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="e7cbb-168">この例の設定ではなく、共有のキャンセル トークンを使用して、<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>プロパティのため、<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>プロパティが完全にデータ フロー ブロックの実行をキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-168">This example uses a shared cancellation token instead of setting the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution.</span></span> <span data-ttu-id="e7cbb-169">キャンセル トークンによって、この例では、ユーザーが 1 つまたは複数の操作をキャンセルしたときにも、同じデータフロー ネットワークを複数回再利用できます。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-169">A cancellation token enables this example to reuse the same dataflow network multiple times, even when the user cancels one or more operations.</span></span> <span data-ttu-id="e7cbb-170">使用する例については<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>取り消すには完全にデータ フロー ブロックの実行、次を参照してください。[する方法: データフロー ブロックをキャンセル](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)です。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-170">For an example that uses <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> to permanently cancel the execution of a dataflow block, see [How to: Cancel a Dataflow Block](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).</span></span>  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a><span data-ttu-id="e7cbb-171">ユーザー インターフェイスへのデータフロー ネットワークの接続</span><span class="sxs-lookup"><span data-stu-id="e7cbb-171">Connecting the Dataflow Network to the User Interface</span></span>  
 <span data-ttu-id="e7cbb-172">このセクションでは、ユーザー インターフェイスにデータフロー ネットワークを接続する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-172">This section describes how to connect the dataflow network to the user interface.</span></span> <span data-ttu-id="e7cbb-173">複合イメージの作成と、操作のキャンセルは、**[フォルダーの選択]** と **[キャンセル]** の各ボタンから開始されます。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-173">The creation of the composite image and cancellation of the operation are initiated from the **Choose Folder** and **Cancel** buttons.</span></span> <span data-ttu-id="e7cbb-174">ユーザーがこのいずれかのボタンを選択すると、適切な操作が非同期的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-174">When the user chooses either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a><span data-ttu-id="e7cbb-175">ユーザー インターフェイスにデータフロー ネットワークを接続するには</span><span class="sxs-lookup"><span data-stu-id="e7cbb-175">To Connect the Dataflow Network to the User Interface</span></span>  
  
1.  <span data-ttu-id="e7cbb-176">メイン フォームのフォーム デザイナーでのイベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**フォルダーを選択**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-176">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Choose Folder** button.</span></span>  
  
2.  <span data-ttu-id="e7cbb-177">実装、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**フォルダーを選択**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-177">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Choose Folder** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  <span data-ttu-id="e7cbb-178">メイン フォームのフォーム デザイナーでのイベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**キャンセル**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-178">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="e7cbb-179">実装、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**キャンセル**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-179">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="e7cbb-180">完全な例</span><span class="sxs-lookup"><span data-stu-id="e7cbb-180">The Complete Example</span></span>  
 <span data-ttu-id="e7cbb-181">次の例は、このチュートリアルのコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-181">The following example shows the complete code for this walkthrough.</span></span>  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 <span data-ttu-id="e7cbb-182">次の図は、一般的な \Sample Pictures\ フォルダーの典型的な出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="e7cbb-182">The following illustration shows typical output for the common \Sample Pictures\ folder.</span></span>  
  
 <span data-ttu-id="e7cbb-183">![Windows フォーム アプリケーション](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")</span><span class="sxs-lookup"><span data-stu-id="e7cbb-183">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="e7cbb-184">次の手順</span><span class="sxs-lookup"><span data-stu-id="e7cbb-184">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7cbb-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7cbb-185">See Also</span></span>  
 [<span data-ttu-id="e7cbb-186">データフロー</span><span class="sxs-lookup"><span data-stu-id="e7cbb-186">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
