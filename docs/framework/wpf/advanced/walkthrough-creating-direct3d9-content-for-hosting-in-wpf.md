---
title: 'チュートリアル : WPF でホストするための Direct3D9 コンテンツの作成'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: f279fb1749be9953e6d09d4b1bd4dd8578d42615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547369"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="b6df9-102">チュートリアル : WPF でホストするための Direct3D9 コンテンツの作成</span><span class="sxs-lookup"><span data-stu-id="b6df9-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="b6df9-103">このチュートリアルでは、Windows Presentation Foundation (WPF) アプリケーションでホストするために適切な Direct3D9 コンテンツを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="b6df9-104">WPF アプリケーションで Direct3D9 コンテンツをホストの詳細については、次を参照してください。 [WPF と Direct3D9 相互運用](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6df9-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).</span></span>  
  
 <span data-ttu-id="b6df9-105">このチュートリアルでは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="b6df9-106">Direct3D9 プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-106">Create a Direct3D9 project.</span></span>  
  
-   <span data-ttu-id="b6df9-107">Direct3D9 プロジェクトを WPF アプリケーションのホスト用に構成します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>  
  
 <span data-ttu-id="b6df9-108">完了したら、WPF アプリケーションで使用するための Direct3D9 コンテンツを含んでいる DLL があります。</span><span class="sxs-lookup"><span data-stu-id="b6df9-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b6df9-109">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b6df9-109">Prerequisites</span></span>  
 <span data-ttu-id="b6df9-110">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="b6df9-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="b6df9-111">。</span><span class="sxs-lookup"><span data-stu-id="b6df9-111">.</span></span>  
  
-   <span data-ttu-id="b6df9-112">DirectX SDK 9or 以降。</span><span class="sxs-lookup"><span data-stu-id="b6df9-112">DirectX SDK 9or later.</span></span>  
  
## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="b6df9-113">Direct3D9 プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-113">Creating the Direct3D9 Project</span></span>  
 <span data-ttu-id="b6df9-114">最初の手順を作成し、Direct3D9 プロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-114">The first step is to create and configure the Direct3D9 project.</span></span>  
  
#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="b6df9-115">Direct3D9 プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="b6df9-115">To create the Direct3D9 project</span></span>  
  
1.  <span data-ttu-id="b6df9-116">C という名前で新しい Win32 プロジェクトを作成`D3DContent`です。</span><span class="sxs-lookup"><span data-stu-id="b6df9-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>  
  
     <span data-ttu-id="b6df9-117">Win32 アプリケーション ウィザードが開き、ようこそ画面を表示します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>  
  
2.  <span data-ttu-id="b6df9-118">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6df9-118">Click **Next**.</span></span>  
  
     <span data-ttu-id="b6df9-119">アプリケーション設定 画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-119">The Application Settings screen appears.</span></span>  
  
3.  <span data-ttu-id="b6df9-120">**アプリケーションの種類:**  セクションで、select、 **DLL**オプション。</span><span class="sxs-lookup"><span data-stu-id="b6df9-120">In the **Application type:** section, select the **DLL** option.</span></span>  
  
4.  <span data-ttu-id="b6df9-121">**[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b6df9-121">Click **Finish**.</span></span>  
  
     <span data-ttu-id="b6df9-122">D3DContent プロジェクトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-122">The D3DContent project is generated.</span></span>  
  
5.  <span data-ttu-id="b6df9-123">ソリューション エクスプ ローラーで、D3DContent プロジェクトを右クリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="b6df9-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>  
  
     <span data-ttu-id="b6df9-124">**D3DContent プロパティ ページ** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-124">The **D3DContent Property Pages** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="b6df9-125">選択、 **C/C++** ノード。</span><span class="sxs-lookup"><span data-stu-id="b6df9-125">Select the **C/C++** node.</span></span>  
  
7.  <span data-ttu-id="b6df9-126">**追加のインクルード ディレクトリ**フィールドで、DirectX の場所を含めるフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="b6df9-127">このフォルダーの既定の場所は %ProgramFiles%\Microsoft DirectX SDK (*バージョン*) \Include です。</span><span class="sxs-lookup"><span data-stu-id="b6df9-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>  
  
8.  <span data-ttu-id="b6df9-128">ダブルクリックして、**リンカー**ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-128">Double-click the **Linker** node to expand it.</span></span>  
  
9. <span data-ttu-id="b6df9-129">**追加のライブラリ ディレクトリ**フィールドで、DirectX のライブラリ フォルダーの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="b6df9-130">このフォルダーの既定の場所は %ProgramFiles%\Microsoft DirectX SDK (*バージョン*) \Lib\x86 です。</span><span class="sxs-lookup"><span data-stu-id="b6df9-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>  
  
10. <span data-ttu-id="b6df9-131">選択、**入力**ノード。</span><span class="sxs-lookup"><span data-stu-id="b6df9-131">Select the **Input** node.</span></span>  
  
11. <span data-ttu-id="b6df9-132">**追加の依存関係**フィールドに、追加、`d3d9.lib`と`d3dx9.lib`ファイル。</span><span class="sxs-lookup"><span data-stu-id="b6df9-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>  
  
12. <span data-ttu-id="b6df9-133">ソリューション エクスプ ローラーで、新しいモジュール定義 (.def) という名前のファイルを追加`D3DContent.def`をプロジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="b6df9-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>  
  
## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="b6df9-134">Direct3D9 コンテンツを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-134">Creating the Direct3D9 Content</span></span>  
 <span data-ttu-id="b6df9-135">最適なパフォーマンスを得るに Direct3D9 コンテンツは、特定の設定を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6df9-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="b6df9-136">次のコードでは、最適なパフォーマンス特性を備えた Direct3D9 画面を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="b6df9-137">詳細については、次を参照してください。 [Direct3D9 と WPF の相互運用性のパフォーマンスに関する考慮事項](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6df9-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>  
  
#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="b6df9-138">コンテンツを作成、Direct3D9</span><span class="sxs-lookup"><span data-stu-id="b6df9-138">To create the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="b6df9-139">ソリューション エクスプ ローラーを使用して、次の名前のプロジェクトに 3 つの C++ クラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6df9-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>  
  
     <span data-ttu-id="b6df9-140">`CRenderer` (で仮想デストラクター)</span><span class="sxs-lookup"><span data-stu-id="b6df9-140">`CRenderer` (with virtual destructor)</span></span>  
  
     `CRendererManager`  
  
     `CTriangleRenderer`  
  
2.  <span data-ttu-id="b6df9-141">Renderer.h コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]  
  
3.  <span data-ttu-id="b6df9-142">Renderer.cpp コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]  
  
4.  <span data-ttu-id="b6df9-143">RendererManager.h コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]  
  
5.  <span data-ttu-id="b6df9-144">RendererManager.cpp コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]  
  
6.  <span data-ttu-id="b6df9-145">TriangleRenderer.h コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]  
  
7.  <span data-ttu-id="b6df9-146">TriangleRenderer.cpp コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]  
  
8.  <span data-ttu-id="b6df9-147">Stdafx.h コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]  
  
9. <span data-ttu-id="b6df9-148">Dllmain.cpp コード エディターで開き、自動的に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>  
  
     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]  
  
10. <span data-ttu-id="b6df9-149">コード エディターで D3DContent.def を開きます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-149">Open D3DContent.def in the code editor.</span></span>  
  
11. <span data-ttu-id="b6df9-150">自動的に生成されたコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="b6df9-150">Replace the automatically generated code with the following code.</span></span>  
  
    ```  
    LIBRARY "D3DContent"  
  
    EXPORTS  
  
    SetSize  
    SetAlpha  
    SetNumDesiredSamples  
    SetAdapter  
  
    GetBackBufferNoRef  
    Render  
    Destroy  
    ```  
  
12. <span data-ttu-id="b6df9-151">プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b6df9-151">Build the project.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b6df9-152">次の手順</span><span class="sxs-lookup"><span data-stu-id="b6df9-152">Next Steps</span></span>  
  
-   <span data-ttu-id="b6df9-153">WPF アプリケーションで Direct3D9 コンテンツをホストします。</span><span class="sxs-lookup"><span data-stu-id="b6df9-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="b6df9-154">詳細については、次を参照してください。[チュートリアル: wpf Direct3D9 のコンテンツをホストしている](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6df9-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6df9-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6df9-155">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="b6df9-156">Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="b6df9-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [<span data-ttu-id="b6df9-157">チュートリアル: WPF での Direct3D9 コンテンツのホスト</span><span class="sxs-lookup"><span data-stu-id="b6df9-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
