---
title: "チュートリアル : WPF での Direct3D9 コンテンツのホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10558348a963f0b243dcfbe23171f6e24da6da0d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="7b1c6-102">チュートリアル : WPF での Direct3D9 コンテンツのホスト</span><span class="sxs-lookup"><span data-stu-id="7b1c6-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="7b1c6-103">このチュートリアルでは、Windows Presentation Foundation (WPF) アプリケーションで Direct3D9 コンテンツをホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="7b1c6-104">このチュートリアルでは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="7b1c6-105">Direct3D9 コンテンツをホストする WPF プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="7b1c6-106">Direct3D9 コンテンツをインポートします。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="7b1c6-107">使用して Direct3D9 コンテンツを表示、<xref:System.Windows.Interop.D3DImage>クラスです。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="7b1c6-108">完了したら、WPF アプリケーションで Direct3D9 コンテンツをホストする方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7b1c6-109">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7b1c6-109">Prerequisites</span></span>  
 <span data-ttu-id="7b1c6-110">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="7b1c6-111">。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-111">.</span></span>  
  
-   <span data-ttu-id="7b1c6-112">DirectX SDK 9 以降。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="7b1c6-113">WPF と互換性のある形式で Direct3D9 コンテンツを含む DLL です。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="7b1c6-114">詳細については、次を参照してください。 [WPF と Direct3D9 相互運用](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)と[チュートリアル: WPF でのホストの Direct3D9 のコンテンツを作成する](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)です。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-114">For more information, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="7b1c6-115">WPF プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="7b1c6-116">最初の手順では、WPF アプリケーションのプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="7b1c6-117">WPF プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="7b1c6-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="7b1c6-118">新しい WPF アプリケーション プロジェクトを作成するには名前付き Visual c# で`D3DHost`です。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="7b1c6-119">詳細については、次を参照してください。[する方法: 新しい WPF アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)です。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-119">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
     <span data-ttu-id="7b1c6-120">MainWindow.xaml を開きます、[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="7b1c6-121">Direct3D9 コンテンツをインポートします。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="7b1c6-122">使用してアンマネージ DLL から Direct3D9 コンテンツをインポートする、`DllImport`属性。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="7b1c6-123">Direct3D9 コンテンツをインポートするには</span><span class="sxs-lookup"><span data-stu-id="7b1c6-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="7b1c6-124">MainWindow.xaml.cs をコード エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="7b1c6-125">自動的に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="7b1c6-126">Direct3D9 コンテンツをホストしています。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="7b1c6-127">最後に、使用して、 <xref:System.Windows.Interop.D3DImage> Direct3D9 コンテンツをホストするクラス。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="7b1c6-128">Direct3D9 コンテンツをホストするには</span><span class="sxs-lookup"><span data-stu-id="7b1c6-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="7b1c6-129">MainWindow.xaml で自動的に生成された XAML を次の XAML に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="7b1c6-130">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="7b1c6-131">Bin/debug フォルダーに Direct3D9 コンテンツを含んでいる DLL をコピーします。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="7b1c6-132">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="7b1c6-133">WPF アプリケーション内で Direct3D9 コンテンツが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b1c6-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b1c6-134">参照</span><span class="sxs-lookup"><span data-stu-id="7b1c6-134">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="7b1c6-135">Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="7b1c6-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
