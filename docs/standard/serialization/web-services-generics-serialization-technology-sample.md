---
title: "Web サービス ジェネリック シリアル化の技術サンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0ec4f05fd68c523bcffcb9173de7e66d0dcc9a0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="9b619-102">Web サービス ジェネリック シリアル化の技術サンプル</span><span class="sxs-lookup"><span data-stu-id="9b619-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="9b619-103">サンプルのダウンロード</span><span class="sxs-lookup"><span data-stu-id="9b619-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="9b619-104">このサンプルでは、ASP.NET Web サービスで、ジェネリックのシリアル化を使用および制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b619-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="9b619-105">Visual Studio を使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="9b619-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="9b619-106">Visual Studio を起動し、**[ファイル]** メニューの **[新しい Web サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b619-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="9b619-107">**[新しい Web サイト]** ダイアログ ボックスの左ペインで、目的のプログラミング言語を選択し、右ペインの **[ASP.NET Web サービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b619-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="9b619-108">**[参照]** をクリックし、\CS\GenericsService サブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="9b619-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4.  <span data-ttu-id="9b619-109">Service.asmx を選択して、このファイルを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="9b619-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5.  <span data-ttu-id="9b619-110">**[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b619-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b619-111">この一覧の最初の 5 つの手順は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9b619-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="9b619-112">サービスが最初に要求されたときに、.NET Framework ランタイムによって Web サービスが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="9b619-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b619-113">サンプルをビルドするには、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="9b619-113">The following steps are required to build the sample.</span></span>  
  
1.  <span data-ttu-id="9b619-114">[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]を開き、\CS サブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="9b619-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2.  <span data-ttu-id="9b619-115">GenericsService サブディレクトリのアイコンを右クリックし、**[共有とセキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b619-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3.  <span data-ttu-id="9b619-116">**[Web 共有]** タブの **[このフォルダーを共有する]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="9b619-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b619-117">**[別名]** ウィンドウに表示される仮想ディレクトリ名をメモします。このディレクトリ名は、サンプルを実行するために必要になります。</span><span class="sxs-lookup"><span data-stu-id="9b619-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="9b619-118">インターネット インフォメーション サービス (IIS: Internet Information Services) を使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="9b619-118">To build the sample using Internet Information Services</span></span>  
  
1.  <span data-ttu-id="9b619-119">**[インターネット インフォメーション サービス]** 管理スナップインを開き、**[Web サイト]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b619-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2.  <span data-ttu-id="9b619-120">**[既定の Web サイト]** を左クリックして **[新規作成]**、**[仮想ディレクトリ]** の順にクリックし、**仮想ディレクトリの作成ウィザード**を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b619-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3.  <span data-ttu-id="9b619-121">**[次へ]** をクリックし、仮想ディレクトリのパブリック別名を入力し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b619-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="9b619-122">サンプルを保存したディレクトリへのパス (通常は \CS\GenericsService サブディレクトリ) を入力し、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b619-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="9b619-123">**[次へ]** をクリックして、ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="9b619-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b619-124">**[別名]** ペインに表示される仮想ディレクトリ名をメモします。このディレクトリ名は、サンプルを実行するために必要になります。</span><span class="sxs-lookup"><span data-stu-id="9b619-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="9b619-125">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="9b619-125">To run the sample</span></span>  
  
1.  <span data-ttu-id="9b619-126">Web ブラウザー ウィンドウを開き、アドレス バーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b619-126">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="9b619-127">**http://localhost/[virtual directory]/Service.asmx** と入力します。[virtual directory] は、サンプルのビルド時に作成した仮想ディレクトリを表します。</span><span class="sxs-lookup"><span data-stu-id="9b619-127">Type **http://localhost/[virtual directory]/Service.asmx**, where [virtual directory] represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b619-128">コメント</span><span class="sxs-lookup"><span data-stu-id="9b619-128">Remarks</span></span>  
 <span data-ttu-id="9b619-129">サンプルでは、Web サービスの定義へのリンクを含む既定の ASP.NET ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b619-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="9b619-130">Web サービスのソース コードの変更に加えて、表示のカスタマイズも可能です。</span><span class="sxs-lookup"><span data-stu-id="9b619-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="9b619-131">詳細については、「[XML Web サービス クライアントの作成](http://msdn.microsoft.com/en-us/c606f3cb-4111-45b4-ae42-9300420fa16c)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b619-131">For more information, see [Building XML Web Service Clients](http://msdn.microsoft.com/en-us/c606f3cb-4111-45b4-ae42-9300420fa16c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b619-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b619-132">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Web.Services>  
 <xref:System.Xml.Serialization>  
 [<span data-ttu-id="9b619-133">シリアル化</span><span class="sxs-lookup"><span data-stu-id="9b619-133">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="9b619-134">ASP.NET と XML Web サービス クライアントを使用して作成した XML Web サービス</span><span class="sxs-lookup"><span data-stu-id="9b619-134">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)
