---
title: 'チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: 7a4f84281da78068b5c6f7a505c8cb9225b31a39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548900"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a><span data-ttu-id="9cc0f-102">チュートリアル: WPF アプリケーション内のアプリケーション データのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="9cc0f-102">Walkthrough: Caching Application Data in a WPF Application</span></span>
<span data-ttu-id="9cc0f-103">キャッシュを使用すると、メモリにデータを格納して高速にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-103">Caching enables you to store data in memory for rapid access.</span></span> <span data-ttu-id="9cc0f-104">データを再度アクセスすると、アプリケーションは、代わりに、元のソースから取得するキャッシュからデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-104">When the data is accessed again, applications can get the data from the cache instead retrieving it from the original source.</span></span> <span data-ttu-id="9cc0f-105">そのため、パフォーマンスとスケーラビリティが向上します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-105">This can improve performance and scalability.</span></span> <span data-ttu-id="9cc0f-106">また、データ ソースが一時的に使用できない場合でも、キャッシュのデータを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-106">In addition, caching makes data available when the data source is temporarily unavailable.</span></span>  
  
 <span data-ttu-id="9cc0f-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]でのキャッシュを使用するためのクラスを提供[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides classes that enable you to use caching in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="9cc0f-108">これらのクラスにある、<xref:System.Runtime.Caching>名前空間。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-108">These classes are located in the <xref:System.Runtime.Caching> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cc0f-109"><xref:System.Runtime.Caching>名前空間はの新機能、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-109">The <xref:System.Runtime.Caching> namespace is new in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="9cc0f-110">この名前空間は、キャッシュは、すべて使用できる[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-110">This namespace makes caching is available to all [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] applications.</span></span> <span data-ttu-id="9cc0f-111">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の以前のバージョンでは、キャッシュは <xref:System.Web> 名前空間でのみ使用可能だったため、ASP.NET クラスへの依存が必要でした。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-111">In previous versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], caching was available only in the <xref:System.Web> namespace and therefore required a dependency on ASP.NET classes.</span></span>  
  
 <span data-ttu-id="9cc0f-112">このチュートリアルで使用可能なキャッシュの機能を使用する方法、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]の一部として、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-112">This walkthrough shows you how to use the caching functionality that is available in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] as part of a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="9cc0f-113">このチュートリアルでは、テキスト ファイルの内容をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-113">In the walkthrough, you cache the contents of a text file.</span></span>  
  
 <span data-ttu-id="9cc0f-114">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-114">Tasks illustrated in this walkthrough include the following:</span></span>  
  
-   <span data-ttu-id="9cc0f-115">WPF アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-115">Creating a WPF application project.</span></span>  
  
-   <span data-ttu-id="9cc0f-116">参照を追加する、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-116">Adding a reference to the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
-   <span data-ttu-id="9cc0f-117">キャッシュを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-117">Initializing a cache.</span></span>  
  
-   <span data-ttu-id="9cc0f-118">テキスト ファイルの内容を格納するキャッシュ エントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-118">Adding a cache entry that contains the contents of a text file.</span></span>  
  
-   <span data-ttu-id="9cc0f-119">キャッシュ エントリの削除ポリシーを提供します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-119">Providing an eviction policy for the cache entry.</span></span>  
  
-   <span data-ttu-id="9cc0f-120">キャッシュされたファイルのパスの監視と通知する、キャッシュ インスタンスは、監視対象のアイテムを変更します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-120">Monitoring the path of the cached file and notifying the cache instance about changes to the monitored item.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9cc0f-121">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9cc0f-121">Prerequisites</span></span>  
 <span data-ttu-id="9cc0f-122">このチュートリアルを完了するための要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-122">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="9cc0f-123">Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-123">Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].</span></span>  
  
-   <span data-ttu-id="9cc0f-124">少量のテキストを含むテキスト ファイル。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-124">A text file that contains a small amount of text.</span></span> <span data-ttu-id="9cc0f-125">(テキスト ファイルの内容は、メッセージ ボックスに表示されます)。このチュートリアルで示すコードでは、次のファイルを使用することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-125">(You will display the contents of the text file in a message box.) The code illustrated in the walkthrough assumes that you are working with the following file:</span></span>  
  
     `c:\cache\cacheText.txt`  
  
     <span data-ttu-id="9cc0f-126">ただし、テキスト ファイルを使用し、このチュートリアルのコードに小さな変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-126">However, you can use any text file and make small changes to the code in this walkthrough.</span></span>  
  
## <a name="creating-a-wpf-application-project"></a><span data-ttu-id="9cc0f-127">WPF アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-127">Creating a WPF Application Project</span></span>  
 <span data-ttu-id="9cc0f-128">WPF アプリケーション プロジェクトを作成することで始めます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-128">You will start by creating a WPF application project.</span></span>  
  
#### <a name="to-create-a-wpf-application"></a><span data-ttu-id="9cc0f-129">WPF アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="9cc0f-129">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="9cc0f-130">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-130">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="9cc0f-131">**ファイル** メニューのをクリックして**新規**、クリックして**新しいプロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-131">In the **File** menu, click **New**, and then click **New Project**.</span></span>  
  
     <span data-ttu-id="9cc0f-132">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-132">The **New Project** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="9cc0f-133">**インストールされたテンプレート**、使用するプログラミング言語を選択 (**Visual Basic**または**Visual c#**)。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-133">Under **Installed Templates**, select the programming language you want to use (**Visual Basic** or **Visual C#**).</span></span>  
  
4.  <span data-ttu-id="9cc0f-134">**新しいプロジェクト**ダイアログ ボックスで、 **WPF アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-134">In the **New Project** dialog box, select **WPF Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9cc0f-135">表示されない場合、 **WPF アプリケーション**テンプレートのバージョンを対象にすることを確認してください、 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] WPF をサポートします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-135">If you do not see the **WPF Application** template, make sure that you are targeting a version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] that supports WPF.</span></span> <span data-ttu-id="9cc0f-136">**新しいプロジェクト**ダイアログ ボックスで、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]一覧からです。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-136">In the **New Project** dialog box, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] from the list.</span></span>  
  
5.  <span data-ttu-id="9cc0f-137">**名前**テキスト ボックスに、プロジェクトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-137">In the **Name** text box, enter a name for your project.</span></span> <span data-ttu-id="9cc0f-138">たとえば、入力**WPFCaching**です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-138">For example, you can enter **WPFCaching**.</span></span>  
  
6.  <span data-ttu-id="9cc0f-139">選択、**ソリューションのディレクトリを作成**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-139">Select the **Create directory for solution** check box.</span></span>  
  
7.  <span data-ttu-id="9cc0f-140">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-140">Click **OK**.</span></span>  
  
     <span data-ttu-id="9cc0f-141">WPF デザイナーで開きます**デザイン**を表示し、MainWindow.xaml ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-141">The WPF Designer opens in **Design** view and displays the MainWindow.xaml file.</span></span> <span data-ttu-id="9cc0f-142">Visual Studio によって作成、 **My Project**フォルダー、Application.xaml ファイル、および、MainWindow.xaml ファイル。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-142">Visual Studio creates the **My Project** folder, the Application.xaml file, and the MainWindow.xaml file.</span></span>  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a><span data-ttu-id="9cc0f-143">.NET Framework を対象として、キャッシュのアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-143">Targeting the .NET Framework and Adding a Reference to the Caching Assemblies</span></span>  
 <span data-ttu-id="9cc0f-144">既定では、WPF アプリケーションのターゲット、[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-144">By default, WPF applications target the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].</span></span> <span data-ttu-id="9cc0f-145">使用する、 <xref:System.Runtime.Caching> WPF アプリケーションの名前空間は、アプリケーションを対象にする、 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (されません、 [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) 名前空間への参照を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-145">To use the <xref:System.Runtime.Caching> namespace in a WPF application, the application must target the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (not the [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) and must include a reference to the namespace.</span></span>  
  
 <span data-ttu-id="9cc0f-146">したがって、次の手順は、.NET Framework のターゲットを変更しへの参照を追加、<xref:System.Runtime.Caching>名前空間。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-146">Therefore, the next step is to change the .NET Framework target and add a reference to the <xref:System.Runtime.Caching> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cc0f-147">.NET Framework のターゲットを変更する手順は Visual c# プロジェクトおよび Visual Basic プロジェクトでは異なります。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-147">The procedure for changing the .NET Framework target is different in a Visual Basic project and in a Visual C# project.</span></span>  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a><span data-ttu-id="9cc0f-148">Visual Basic での .NET Framework のターゲットを変更するには</span><span class="sxs-lookup"><span data-stu-id="9cc0f-148">To change the target .NET Framework in Visual Basic</span></span>  
  
1.  <span data-ttu-id="9cc0f-149">**ソリューション エクスプ ローラー**プロジェクト名を右クリックし、クリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-149">In **Solutions Explorer**, right-click the project name, and then click **Properties**.</span></span>  
  
     <span data-ttu-id="9cc0f-150">アプリケーションのプロパティ ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-150">The properties window for the application is displayed.</span></span>  
  
2.  <span data-ttu-id="9cc0f-151">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-151">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="9cc0f-152">ウィンドウの下部には、をクリックして**詳細コンパイル オプション**.</span><span class="sxs-lookup"><span data-stu-id="9cc0f-152">At the bottom of the window, click **Advanced Compile Options…**.</span></span>  
  
     <span data-ttu-id="9cc0f-153">**コンパイラ設定の高度な** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-153">The **Advanced Compiler Settings** dialog box is displayed.</span></span>  
  
4.  <span data-ttu-id="9cc0f-154">**ターゲット フレームワーク (すべての構成)** 一覧で、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-154">In the **Target framework (all configurations)** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="9cc0f-155">(選択しないでください[!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-155">(Do not select [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)</span></span>  
  
5.  <span data-ttu-id="9cc0f-156">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-156">Click **OK**.</span></span>  
  
     <span data-ttu-id="9cc0f-157">**ターゲット フレームワークの変更** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-157">The **Target Framework Change** dialog box is displayed.</span></span>  
  
6.  <span data-ttu-id="9cc0f-158">**ターゲット フレームワークの変更**ダイアログ ボックスで、をクリックして**はい**です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-158">In the **Target Framework Change** dialog box, click **Yes**.</span></span>  
  
     <span data-ttu-id="9cc0f-159">プロジェクトが閉じられ、再び開いたです。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-159">The project is closed and is then reopened.</span></span>  
  
7.  <span data-ttu-id="9cc0f-160">次の手順でキャッシュのアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-160">Add a reference to the caching assembly by following these steps:</span></span>  
  
    1.  <span data-ttu-id="9cc0f-161">**ソリューション エクスプ ローラー**プロジェクトの名前を右クリックし、クリックして**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-161">In **Solution Explorer**, right-click the name of the project and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="9cc0f-162">選択、 **.NET** ] タブで [ `System.Runtime.Caching`、クリックして **[ok]** です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-162">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a><span data-ttu-id="9cc0f-163">Visual c# プロジェクトのターゲットの .NET Framework を変更するには</span><span class="sxs-lookup"><span data-stu-id="9cc0f-163">To change the target .NET Framework in a Visual C# project</span></span>  
  
1.  <span data-ttu-id="9cc0f-164">**ソリューション エクスプ ローラー**プロジェクト名を右クリックし、クリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-164">In **Solution Explorer**, right-click the project name and then click **Properties**.</span></span>  
  
     <span data-ttu-id="9cc0f-165">アプリケーションのプロパティ ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-165">The properties window for the application is displayed.</span></span>  
  
2.  <span data-ttu-id="9cc0f-166">**[アプリケーション]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-166">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="9cc0f-167">**ターゲット フレームワーク**一覧で、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-167">In the **Target framework** list, select [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="9cc0f-168">(選択しないでください **.NET Framework 4 Client Profile**)。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-168">(Do not select **.NET Framework 4 Client Profile**.)</span></span>  
  
4.  <span data-ttu-id="9cc0f-169">次の手順でキャッシュのアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-169">Add a reference to the caching assembly by following these steps:</span></span>  
  
    1.  <span data-ttu-id="9cc0f-170">右クリックし、**参照**フォルダーをクリックして**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-170">Right-click the **References** folder and then click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="9cc0f-171">選択、 **.NET** ] タブで [ `System.Runtime.Caching`、クリックして **[ok]** です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-171">Select the **.NET** tab, select `System.Runtime.Caching`, and then click **OK**.</span></span>  
  
## <a name="adding-a-button-to-the-wpf-window"></a><span data-ttu-id="9cc0f-172">WPF ウィンドウへボタンの追加</span><span class="sxs-lookup"><span data-stu-id="9cc0f-172">Adding a Button to the WPF Window</span></span>  
 <span data-ttu-id="9cc0f-173">次に、ボタン コントロールを追加し、ボタンのイベント ハンドラーを作成`Click`イベント。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-173">Next, you will add a button control and create an event handler for the button's `Click` event.</span></span> <span data-ttu-id="9cc0f-174">後で、テキスト ファイルの内容がキャッシュされ、表示されるボタンをクリックすると、コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-174">Later you will add code to so when you click the button, the contents of the text file are cached and displayed.</span></span>  
  
#### <a name="to-add-a-button-control"></a><span data-ttu-id="9cc0f-175">ボタン コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="9cc0f-175">To add a button control</span></span>  
  
1.  <span data-ttu-id="9cc0f-176">**ソリューション エクスプ ローラー**、MainWindow.xaml ファイルを開くをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-176">In **Solution Explorer**, double-click the MainWindow.xaml file to open it.</span></span>  
  
2.  <span data-ttu-id="9cc0f-177">**ツールボックス****共通の WPF コントロール**、ドラッグ、`Button`コントロールを`MainWindow`ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-177">From the **Toolbox**, under **Common WPF Controls**, drag a `Button` control to the `MainWindow` window.</span></span>  
  
3.  <span data-ttu-id="9cc0f-178">**プロパティ**ウィンドウで、設定、`Content`のプロパティ、`Button`に制御を**取得キャッシュ**です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-178">In the **Properties** window, set the `Content` property of the `Button` control to **Get Cache**.</span></span>  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a><span data-ttu-id="9cc0f-179">キャッシュの初期化とエントリをキャッシュ</span><span class="sxs-lookup"><span data-stu-id="9cc0f-179">Initializing the Cache and Caching an Entry</span></span>  
 <span data-ttu-id="9cc0f-180">次に、次のタスクを実行するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-180">Next, you will add the code to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="9cc0f-181">キャッシュ クラスのインスタンスを作成する: つまりはインスタンス化する新しい<xref:System.Runtime.Caching.MemoryCache>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-181">Create an instance of the cache class—that is, you will instantiate a new <xref:System.Runtime.Caching.MemoryCache> object.</span></span>  
  
-   <span data-ttu-id="9cc0f-182">キャッシュが使用するように指定、<xref:System.Runtime.Caching.HostFileChangeMonitor>のテキスト ファイルの変更を監視するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-182">Specify that the cache uses a <xref:System.Runtime.Caching.HostFileChangeMonitor> object to monitor changes in the text file.</span></span>  
  
-   <span data-ttu-id="9cc0f-183">テキスト ファイルの読み取りおよびキャッシュ エントリとしてその内容をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-183">Read the text file and cache its contents as a cache entry.</span></span>  
  
-   <span data-ttu-id="9cc0f-184">キャッシュされたテキスト ファイルの内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-184">Display the contents of the cached text file.</span></span>  
  
#### <a name="to-create-the-cache-object"></a><span data-ttu-id="9cc0f-185">キャッシュ オブジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="9cc0f-185">To create the cache object</span></span>  
  
1.  <span data-ttu-id="9cc0f-186">MainWindow.xaml.cs または MainWindow.Xaml.vb ファイルで、イベント ハンドラーを作成するために追加したボタンをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-186">Double-click the button you just added in order to create an event handler in the MainWindow.xaml.cs or MainWindow.Xaml.vb file.</span></span>  
  
2.  <span data-ttu-id="9cc0f-187">(宣言の前に、クラス) ファイルの上部には、次のコードを追加`Imports`(Visual Basic) または`using`(c#) ステートメント。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-187">At the top of the file (before the class declaration), add the following `Imports` (Visual Basic) or `using` (C#) statements:</span></span>  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  <span data-ttu-id="9cc0f-188">イベント ハンドラーでは、キャッシュ オブジェクトをインスタンス化する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-188">In the event handler, add the following code to instantiate the cache object:</span></span>  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <span data-ttu-id="9cc0f-189"><xref:System.Runtime.Caching.ObjectCache>クラスは、メモリ内のオブジェクトのキャッシュを提供する組み込みクラスです。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-189">The <xref:System.Runtime.Caching.ObjectCache> class is a built-in class that provides an in-memory object cache.</span></span>  
  
4.  <span data-ttu-id="9cc0f-190">という名前のキャッシュ エントリの内容を読み取るには、次のコードを追加`filecontents`:</span><span class="sxs-lookup"><span data-stu-id="9cc0f-190">Add the following code to read the contents of a cache entry named `filecontents`:</span></span>  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  <span data-ttu-id="9cc0f-191">キャッシュ エントリが名前付きかどうかを確認するには、次のコードを追加`filecontents`が存在します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-191">Add the following code to check whether the cache entry named `filecontents` exists:</span></span>  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     <span data-ttu-id="9cc0f-192">指定されたキャッシュ エントリが存在しない場合は、テキスト ファイルの読み取りし、キャッシュ エントリとしてキャッシュに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-192">If the specified cache entry does not exist, you must read the text file and add it as a cache entry to the cache.</span></span>  
  
6.  <span data-ttu-id="9cc0f-193">`if/then`ブロックして、新たに作成するのには、次のコードを追加するには、<xref:System.Runtime.Caching.CacheItemPolicy>に 10 秒後に、キャッシュ エントリが期限切れを指定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-193">In the `if/then` block, add the following code to create a new <xref:System.Runtime.Caching.CacheItemPolicy> object that specifies that the cache entry expires after 10 seconds.</span></span>  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     <span data-ttu-id="9cc0f-194">削除または有効期限の情報が指定されていない場合、既定値は<xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>、キャッシュ エントリは決して期限切れに基づいて絶対時間にのみです。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-194">If no eviction or expiration information is provided, the default is <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, which means the cache entries never expire based only on an absolute time.</span></span> <span data-ttu-id="9cc0f-195">代わりに、キャッシュ エントリには、メモリ負荷がかかっている場合にのみが期限切れです。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-195">Instead, cache entries expire only when there is memory pressure.</span></span> <span data-ttu-id="9cc0f-196">ベスト プラクティスとしては、常に明示的に、絶対または側線有効期限を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-196">As a best practice, you should always explicitly provide either an absolute or a siding expiration.</span></span>  
  
7.  <span data-ttu-id="9cc0f-197">内部、`if/then`をブロックし、前の手順で追加したコードの後に、監視、し、テキスト ファイルのパスをコレクションに追加するファイルのパスのコレクションを作成する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-197">Inside the `if/then` block and following the code you added in the previous step, add the following code to create a collection for the file paths that you want to monitor, and to add the path of the text file to the collection:</span></span>  
  
    ```vb  
    Dim filePaths As New List(Of String)()  
    filePaths.Add("c:\cache\cacheText.txt")  
    ```  
  
    ```csharp  
    List<string> filePaths = new List<string>();  
    filePaths.Add("c:\\cache\\cacheText.txt");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9cc0f-198">かどうかに使用するテキスト ファイルは`c:\cache\cacheText.txt`、テキスト ファイルが使用するパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-198">If the text file you want to use is not `c:\cache\cacheText.txt`, specify the path where the text file is that you want to use.</span></span>  
  
8.  <span data-ttu-id="9cc0f-199">新しいを追加する次のコードを追加する前の手順で追加したコードを次<xref:System.Runtime.Caching.HostFileChangeMonitor>キャッシュ エントリの変更のコレクションにオブジェクトを監視します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-199">Following the code that you added in the previous step, add the following code to add a new <xref:System.Runtime.Caching.HostFileChangeMonitor> object to the collection of change monitors for the cache entry:</span></span>  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <span data-ttu-id="9cc0f-200"><xref:System.Runtime.Caching.HostFileChangeMonitor>オブジェクトは、テキスト ファイルのパスを監視し、変更が発生する場合は、キャッシュに通知します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-200">The <xref:System.Runtime.Caching.HostFileChangeMonitor> object monitors the text file's path and notifies the cache if changes occur.</span></span> <span data-ttu-id="9cc0f-201">この例では、キャッシュ エントリの有効期限、ファイルの内容が変更された場合。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-201">In this example, the cache entry will expire if the content of the file changes.</span></span>  
  
9. <span data-ttu-id="9cc0f-202">前の手順で追加したコードの後に、テキスト ファイルの内容を読み取るには、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-202">Following the code that you added in the previous step, add the following code to read the contents of the text file:</span></span>  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     <span data-ttu-id="9cc0f-203">キャッシュ エントリの有効期限が切れるときに表示できるように、日付と時刻のタイムスタンプが追加されます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-203">The date and time timestamp is added so that you will be able to see when the cache entry expires.</span></span>  
  
10. <span data-ttu-id="9cc0f-204">としてキャッシュ オブジェクトに、ファイルの内容を挿入する次のコードを追加する前の手順で追加したコードの後、<xref:System.Runtime.Caching.CacheItem>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-204">Following the code that you added in the previous step, add the following code to insert the contents of the file into the cache object as a <xref:System.Runtime.Caching.CacheItem> instance:</span></span>  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     <span data-ttu-id="9cc0f-205">渡すことによって、キャッシュ エントリを削除する方法に関する情報を指定する、<xref:System.Runtime.Caching.CacheItemPolicy>をパラメーターとして、先ほど作成したオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-205">You specify information about how the cache entry should be evicted by passing the <xref:System.Runtime.Caching.CacheItemPolicy> object that you created earlier as a parameter.</span></span>  
  
11. <span data-ttu-id="9cc0f-206">後に、`if/then`ブロックは、メッセージ ボックスに、キャッシュされたファイルの内容を表示する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-206">After the `if/then` block, add the following code to display the cached file content in a message box:</span></span>  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. <span data-ttu-id="9cc0f-207">**ビルド** メニューのをクリックして**ビルド WPFCaching**プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-207">In the **Build** menu, click **Build WPFCaching** to build your project.</span></span>  
  
## <a name="testing-caching-in-the-wpf-application"></a><span data-ttu-id="9cc0f-208">WPF アプリケーションでキャッシュのテスト</span><span class="sxs-lookup"><span data-stu-id="9cc0f-208">Testing Caching in the WPF Application</span></span>  
 <span data-ttu-id="9cc0f-209">アプリケーションをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-209">You can now test the application.</span></span>  
  
#### <a name="to-test-caching-in-the-wpf-application"></a><span data-ttu-id="9cc0f-210">WPF アプリケーションでキャッシュをテストするには</span><span class="sxs-lookup"><span data-stu-id="9cc0f-210">To test caching in the WPF application</span></span>  
  
1.  <span data-ttu-id="9cc0f-211">Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-211">Press CTRL+F5 to run the application.</span></span>  
  
     <span data-ttu-id="9cc0f-212">`MainWindow`ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-212">The `MainWindow` window is displayed.</span></span>  
  
2.  <span data-ttu-id="9cc0f-213">をクリックして**キャッシュを取得する**です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-213">Click **Get Cache**.</span></span>  
  
     <span data-ttu-id="9cc0f-214">テキスト ファイルからキャッシュされたコンテンツは、メッセージ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-214">The cached content from the text file is displayed in a message box.</span></span> <span data-ttu-id="9cc0f-215">ファイルのタイムスタンプに注目してください。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-215">Notice the timestamp on the file.</span></span>  
  
3.  <span data-ttu-id="9cc0f-216">メッセージ ボックスを閉じ、をクリックして**取得キャッシュ**再度**です。**</span><span class="sxs-lookup"><span data-stu-id="9cc0f-216">Close the message box and then click **Get Cache** again **.**</span></span>  
  
     <span data-ttu-id="9cc0f-217">タイムスタンプは変更されません。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-217">The timestamp is unchanged.</span></span> <span data-ttu-id="9cc0f-218">これは、キャッシュされたコンテンツの表示を示します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-218">This indicates the cached content is displayed.</span></span>  
  
4.  <span data-ttu-id="9cc0f-219">クリックして、10 秒以上待機**取得キャッシュ**もう一度です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-219">Wait 10 seconds or more and then click **Get Cache** again.</span></span>  
  
     <span data-ttu-id="9cc0f-220">この時刻に新しいタイムスタンプが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-220">This time a new timestamp is displayed.</span></span> <span data-ttu-id="9cc0f-221">これは、ポリシーが期限切れのキャッシュ エントリを任せることと、新しいキャッシュされたコンテンツが表示されることを示します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-221">This indicates that the policy let the cache entry expire and that new cached content is displayed.</span></span>  
  
5.  <span data-ttu-id="9cc0f-222">テキスト エディターで作成したテキスト ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-222">In a text editor, open the text file that you created.</span></span> <span data-ttu-id="9cc0f-223">すべての変更をまだくださいしないでください。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-223">Do not make any changes yet.</span></span>  
  
6.  <span data-ttu-id="9cc0f-224">メッセージ ボックスを閉じ、をクリックして**取得キャッシュ**再度**です。**</span><span class="sxs-lookup"><span data-stu-id="9cc0f-224">Close the message box and then click **Get Cache** again **.**</span></span>  
  
     <span data-ttu-id="9cc0f-225">タイムスタンプをもう一度確認します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-225">Notice the timestamp again.</span></span>  
  
7.  <span data-ttu-id="9cc0f-226">テキスト ファイルに変更を加えるし、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-226">Make a change to the text file and then save the file.</span></span>  
  
8.  <span data-ttu-id="9cc0f-227">メッセージ ボックスを閉じ、をクリックして**取得キャッシュ**もう一度です。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-227">Close the message box and then click **Get Cache** again.</span></span>  
  
     <span data-ttu-id="9cc0f-228">このメッセージ ボックスには、新しいタイムスタンプやテキスト ファイルから更新されたコンテンツが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-228">This message box contains the updated content from the text file and a new timestamp.</span></span> <span data-ttu-id="9cc0f-229">ホスト ファイルの変更モニター削除すること、キャッシュ エントリ、ファイルを変更したときにすぐに、絶対のタイムアウト期間の有効期限が切れていない場合でもこれを示します。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-229">This indicates that the host-file change monitor evicted the cache entry immediately when you changed the file, even though the absolute timeout period had not expired.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9cc0f-230">ファイルを変更するための時間を 20 秒以上削除時間を増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-230">You can increase the eviction time to 20 seconds or more to allow more time for you to make a change in the file.</span></span>  
  
## <a name="code-example"></a><span data-ttu-id="9cc0f-231">コード例</span><span class="sxs-lookup"><span data-stu-id="9cc0f-231">Code Example</span></span>  
 <span data-ttu-id="9cc0f-232">このチュートリアルを完了した後に作成したプロジェクトのコードが次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="9cc0f-232">After you have completed this walkthrough, the code for the project you created will resemble the following example.</span></span>  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9cc0f-233">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cc0f-233">See Also</span></span>  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [<span data-ttu-id="9cc0f-234">.NET Framework アプリケーションでのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="9cc0f-234">Caching in .NET Framework Applications</span></span>](../../../../docs/framework/performance/caching-in-net-framework-applications.md)
