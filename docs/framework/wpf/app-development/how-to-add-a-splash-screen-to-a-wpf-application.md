---
title: "方法 : スプラッシュ スクリーンを WPF アプリケーションに追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ed9669479a3854c843716a1aeb37f7701ea7d7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="d9c45-102">方法 : スプラッシュ スクリーンを WPF アプリケーションに追加する</span><span class="sxs-lookup"><span data-stu-id="d9c45-102">How to: Add a Splash Screen to a WPF Application</span></span>
<span data-ttu-id="d9c45-103">このトピックは、[スタートアップ] ウィンドウを追加する方法を示しますまたは*スプラッシュ スクリーン*、Windows Presentation Foundation (WPF) アプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="d9c45-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="d9c45-104">スプラッシュ スクリーンとして既存のイメージを追加するには</span><span class="sxs-lookup"><span data-stu-id="d9c45-104">To add an existing image as a splash screen</span></span>  
  
1.  <span data-ttu-id="d9c45-105">スプラッシュ スクリーンを使用するイメージを作成または選択します。</span><span class="sxs-lookup"><span data-stu-id="d9c45-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="d9c45-106">Windows イメージング コンポーネント (WIC) ではサポートされているすべてのイメージ形式を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d9c45-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="d9c45-107">たとえば、BMP、GIF、JPEG、PNG、または TIFF の形式を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d9c45-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>  
  
2.  <span data-ttu-id="d9c45-108">WPF アプリケーション プロジェクトにイメージ ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="d9c45-108">Add the image file to the WPF Application project.</span></span> <span data-ttu-id="d9c45-109">詳細については、次を参照してください。 [NIB: 方法: 既存の項目をプロジェクトに追加](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)です。</span><span class="sxs-lookup"><span data-stu-id="d9c45-109">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
3.  <span data-ttu-id="d9c45-110">ソリューション エクスプ ローラーで、イメージを選択します。</span><span class="sxs-lookup"><span data-stu-id="d9c45-110">In Solution Explorer, select the image.</span></span>  
  
4.  <span data-ttu-id="d9c45-111">[プロパティ] ウィンドウでのドロップダウン矢印をクリックして、**ビルド アクション**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d9c45-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>  
  
5.  <span data-ttu-id="d9c45-112">選択**SplashScreen**ドロップダウン リストからです。</span><span class="sxs-lookup"><span data-stu-id="d9c45-112">Select **SplashScreen** from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9c45-113">表示されない場合、 **SplashScreen**オプションを使用していることを確認してください[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]SP1 またはそれ以降。</span><span class="sxs-lookup"><span data-stu-id="d9c45-113">If you do not see the **SplashScreen** option, be sure to check that you are using [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 or later.</span></span>  
  
6.  <span data-ttu-id="d9c45-114">F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="d9c45-114">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="d9c45-115">スプラッシュ スクリーンのイメージは、画面の中央に表示され、アプリケーションのメイン ウィンドウが表示されたら、フェードし。</span><span class="sxs-lookup"><span data-stu-id="d9c45-115">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="d9c45-116">スプラッシュ スクリーンをアプリケーションから削除するには</span><span class="sxs-lookup"><span data-stu-id="d9c45-116">To remove the splash screen from an application</span></span>  
  
1.  <span data-ttu-id="d9c45-117">ソリューション エクスプ ローラーでは、スプラッシュ スクリーンのイメージを選択します。</span><span class="sxs-lookup"><span data-stu-id="d9c45-117">In Solution Explorer, select the splash screen image.</span></span>  
  
2.  <span data-ttu-id="d9c45-118">[プロパティ] ウィンドウで、設定、**ビルド アクション**に**なし**です。</span><span class="sxs-lookup"><span data-stu-id="d9c45-118">In the Properties window, set the **Build Action** to **None**.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="d9c45-119">スプラッシュ スクリーンをアプリケーションから削除するには</span><span class="sxs-lookup"><span data-stu-id="d9c45-119">To remove the splash screen from an application</span></span>  
  
-   <span data-ttu-id="d9c45-120">ソリューション エクスプ ローラーでは、スプラッシュ スクリーンのイメージを削除します。</span><span class="sxs-lookup"><span data-stu-id="d9c45-120">In Solution Explorer, delete the splash screen image.</span></span>  
  
-   <span data-ttu-id="d9c45-121">スプラッシュ スクリーンのイメージをプロジェクトから除外します。</span><span class="sxs-lookup"><span data-stu-id="d9c45-121">Exclude the splash screen image from the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c45-122">参照</span><span class="sxs-lookup"><span data-stu-id="d9c45-122">See Also</span></span>  
 <xref:System.Windows.SplashScreen>  
 [<span data-ttu-id="d9c45-123">NIB: 方法: 既存の項目をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="d9c45-123">NIB:How to: Add Existing Items to a Project</span></span>](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
