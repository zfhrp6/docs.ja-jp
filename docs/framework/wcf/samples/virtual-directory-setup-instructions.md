---
title: 仮想ディレクトリのセットアップ手順
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 3ff578b69590071ef2135e777b3105e7c226563e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="2894f-102">仮想ディレクトリのセットアップ手順</span><span class="sxs-lookup"><span data-stu-id="2894f-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="2894f-103">Windows Communication Foundation (WCF) サンプルは %SystemDrive%\inetpub\wwwroot\servicemodelsamples フォルダーにマップされている servicemodelsamples という仮想ディレクトリを共有します。</span><span class="sxs-lookup"><span data-stu-id="2894f-103">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2894f-104">%SystemDrive% は、インターネット インフォメーション サービス (IIS) がインストールされているドライブの場所に応じて、通常は C: または D: になります。</span><span class="sxs-lookup"><span data-stu-id="2894f-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="2894f-105">ファイルを Setupvroot.bat と Cleanupvroot.bat を実行することができます、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)仮想ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="2894f-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="2894f-106">この仮想ディレクトリを手動で作成する場合は、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2894f-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="2894f-107">手順</span><span class="sxs-lookup"><span data-stu-id="2894f-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="2894f-108">IIS 7.0 または 7.5 で仮想ディレクトリを作成するには</span><span class="sxs-lookup"><span data-stu-id="2894f-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="2894f-109">**開始** メニューのをクリックして**実行**、入力**inetmgr**を開くには、インターネット インフォメーション サービス (IIS) MMC スナップイン。</span><span class="sxs-lookup"><span data-stu-id="2894f-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="2894f-110">左側のウィンドウで、コンピューターの名前を持つノードを展開し、展開、**サイト**ノード。</span><span class="sxs-lookup"><span data-stu-id="2894f-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3.  <span data-ttu-id="2894f-111">右クリック**既定の Web サイト**、し、**アプリケーションの追加**を開くには、**追加のアプリケーション ウィンドウ**します。</span><span class="sxs-lookup"><span data-stu-id="2894f-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4.  <span data-ttu-id="2894f-112">ウィンドウで、次のように入力します。`servicemodelsamples`として作成している仮想ディレクトリのエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="2894f-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="2894f-113">次のディレクトリを作成します。%SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="2894f-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6.  <span data-ttu-id="2894f-114">物理パスを %SystemDrive%\inetpub\wwwroot\servicemodelsamples に設定します。</span><span class="sxs-lookup"><span data-stu-id="2894f-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="2894f-115">WCF サンプルの多くは、ビルド時にサービス実行可能ファイルをこの場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="2894f-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7.  <span data-ttu-id="2894f-116">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2894f-116">Click **OK**.</span></span> <span data-ttu-id="2894f-117">Web アプリケーションが、WCF サンプル用に作成されました。</span><span class="sxs-lookup"><span data-stu-id="2894f-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2894f-118">このタスクは、同じ servicemodelsamples Web アプリケーションを使用するすべての WCF サンプルために、1 回だけ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2894f-118">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2894f-119">このドキュメントでは、`virtual directory`という用語は `Web application`と同じ意味で使用しています。</span><span class="sxs-lookup"><span data-stu-id="2894f-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="2894f-120">仮想ディレクトリを作成するだけでなく、実行する WCF サービスを有効にするには、そのプロパティを設定することも必要があります。</span><span class="sxs-lookup"><span data-stu-id="2894f-120">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="2894f-121">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2894f-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="2894f-122">仮想ディレクトリを IIS 5.1 または 6.0 で作成するには</span><span class="sxs-lookup"><span data-stu-id="2894f-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="2894f-123">コマンド プロンプト ウィンドウを開き`start inetmgr`を開くには、インターネット インフォメーション サービス (IIS) MMC スナップイン。</span><span class="sxs-lookup"><span data-stu-id="2894f-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="2894f-124">左側のウィンドウで、コンピューターの名前を持つノードを展開し、展開、 **Websites**ノード。</span><span class="sxs-lookup"><span data-stu-id="2894f-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3.  <span data-ttu-id="2894f-125">右クリック**既定の Web サイト**選択 **、新しい仮想ディレクトリ**仮想ディレクトリの作成ウィザードを開きます。</span><span class="sxs-lookup"><span data-stu-id="2894f-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4.  <span data-ttu-id="2894f-126">ウィザードで、次のように入力します。`servicemodelsamples`として作成している仮想ディレクトリのエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="2894f-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="2894f-127">パスを %SystemDrive%\inetpub\wwwroot\servicemodelsamples に設定します。</span><span class="sxs-lookup"><span data-stu-id="2894f-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="2894f-128">WCF サンプルの多くは、ビルド時にサービス実行可能ファイルをこの場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="2894f-128">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6.  <span data-ttu-id="2894f-129">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2894f-129">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="2894f-130">既定では、次のチェック ボックスがオンになっています。</span><span class="sxs-lookup"><span data-stu-id="2894f-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="2894f-131">**読み取り**</span><span class="sxs-lookup"><span data-stu-id="2894f-131">**Read**</span></span>  
  
    -   <span data-ttu-id="2894f-132">**(ASP) などのスクリプトを実行します。**</span><span class="sxs-lookup"><span data-stu-id="2894f-132">**Run scripts (such as ASP)**</span></span>  
  
8.  <span data-ttu-id="2894f-133">をクリックして **[次へ]**、順にクリック**完了**ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="2894f-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2894f-134">このタスクは、すべての WCF サンプルには、同じ servicemodelsamples 仮想ディレクトリが使用するため、1 回だけ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2894f-134">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="2894f-135">IIS 7.0 での他の仮想ディレクトリのプロパティまたは 7.5 を設定するには</span><span class="sxs-lookup"><span data-stu-id="2894f-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="2894f-136">servicemodelsamples ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2894f-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="2894f-137">ウィンドウの下端に沿って 2 つのビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2894f-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="2894f-138">選択**機能ビュー**が選択されていない場合。</span><span class="sxs-lookup"><span data-stu-id="2894f-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2.  <span data-ttu-id="2894f-139">エントリをダブルクリックして**ディレクトリの参照**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3.  <span data-ttu-id="2894f-140">[操作] ウィンドウで、選択、**を有効にする**オプション。</span><span class="sxs-lookup"><span data-stu-id="2894f-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="2894f-141">これにより、Internet Explorer でディレクトリにアクセスできるようになり、サービスのデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2894f-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="2894f-142">最後に、servicemodelsamples フォルダーのセキュリティ プロパティを、他のユーザーがアクセスできるように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2894f-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="2894f-143">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2894f-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="2894f-144">仮想ディレクトリの追加プロパティを IIS 5.1 または 6.0 で設定するには</span><span class="sxs-lookup"><span data-stu-id="2894f-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="2894f-145">Servicemodelsamples ノードを右クリックし、をクリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="2894f-146">既定では、次のチェック ボックスがオンになっています。</span><span class="sxs-lookup"><span data-stu-id="2894f-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="2894f-147">**読み取り**</span><span class="sxs-lookup"><span data-stu-id="2894f-147">**Read**</span></span>  
  
    -   <span data-ttu-id="2894f-148">**[ログ アクセス]**</span><span class="sxs-lookup"><span data-stu-id="2894f-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="2894f-149">**このリソースします。**</span><span class="sxs-lookup"><span data-stu-id="2894f-149">**Index this resource**</span></span>  
  
3.  <span data-ttu-id="2894f-150">選択、**ディレクトリの参照**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="2894f-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="2894f-151">これにより、Internet Explorer でディレクトリにアクセスできるようになり、サービスのデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2894f-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="2894f-152">IIS 7.0 または 7.5 でフォルダーのセキュリティ プロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="2894f-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="2894f-153">%SystemDrive%\inetpub\wwwroot\servicemodelsamples に移動します。</span><span class="sxs-lookup"><span data-stu-id="2894f-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="2894f-154">Servicemodelsamples フォルダーを右クリックし、をクリックして**共有**または**共有で**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3.  <span data-ttu-id="2894f-155">左側にある下向きの矢印をクリックして、**追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2894f-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4.  <span data-ttu-id="2894f-156">選択、**検索**エントリです。</span><span class="sxs-lookup"><span data-stu-id="2894f-156">Select the **Find** entry.</span></span> <span data-ttu-id="2894f-157">**ユーザーまたはグループ**ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="2894f-157">The **Select Users or Groups** window opens.</span></span>  
  
5.  <span data-ttu-id="2894f-158">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2894f-158">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="2894f-159">をクリックして**場所**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-159">Click **Locations**.</span></span> <span data-ttu-id="2894f-160">**場所**ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="2894f-160">The **Locations** window is now open.</span></span>  
  
7.  <span data-ttu-id="2894f-161">使用するコンピューターのエントリを選択します。</span><span class="sxs-lookup"><span data-stu-id="2894f-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="2894f-162">一覧表示されているドメインやネットワークのエントリではなく、ローカル コンピューターを選択してください。</span><span class="sxs-lookup"><span data-stu-id="2894f-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="2894f-163">コンピューターを選択した後にをクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-163">After you have selected the computer, click **OK**.</span></span>  
  
8.  <span data-ttu-id="2894f-164">をクリックして**今すぐ検索**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-164">Click **Find Now**.</span></span> <span data-ttu-id="2894f-165">これで、ローカル コンピューターに関連付けられたオブジェクトが検索結果に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2894f-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="2894f-166">検索、 **IIS_IUSRS**内のエントリ、**名 (相対識別名)** 列です。</span><span class="sxs-lookup"><span data-stu-id="2894f-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="2894f-167">そのエントリを選択し、をクリックして**OK**結果ウィンドウの検索を閉じます。</span><span class="sxs-lookup"><span data-stu-id="2894f-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="2894f-168">をクリックして**OK**を閉じる、 **ユーザーまたはグループ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2894f-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="2894f-169">をクリックして**共有**変更を保持します。</span><span class="sxs-lookup"><span data-stu-id="2894f-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="2894f-170">共有を有効にする変更が完了した後にをクリックして**完了**を閉じる、**ファイルの共有**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="2894f-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="2894f-171">フォルダーのセキュリティ プロパティを IIS 5.1 または 6.0 で設定するには</span><span class="sxs-lookup"><span data-stu-id="2894f-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="2894f-172">%SystemDrive%\inetpub\wwwroot\servicemodelsamples に移動します。</span><span class="sxs-lookup"><span data-stu-id="2894f-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="2894f-173">右クリックし、 **servicemodelsamples**フォルダーをクリックして**共有とセキュリティ。**</span><span class="sxs-lookup"><span data-stu-id="2894f-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3.  <span data-ttu-id="2894f-174">**[セキュリティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2894f-174">Click the **Security** tab.</span></span>  
  
4.  <span data-ttu-id="2894f-175">IIS 6.0 を使用している場合、**グループまたはユーザー名**ボックスで、チェックするかどうか**インターネット ゲスト アカウント**が表示されています。</span><span class="sxs-lookup"><span data-stu-id="2894f-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="2894f-176">表示されていない場合:</span><span class="sxs-lookup"><span data-stu-id="2894f-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="2894f-177">をクリックして**開始**] をクリックし、**コントロール パネルの [** です。</span><span class="sxs-lookup"><span data-stu-id="2894f-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="2894f-178">表示されない場合、**ユーザー アカウント** アイコンをクリックして**カテゴリのビューに切り替えます**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="2894f-179">クリックして、**ユーザー アカウント**アイコン。</span><span class="sxs-lookup"><span data-stu-id="2894f-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="2894f-180">「またはコントロール パネルを選んで」クリックして**ユーザー アカウント**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="2894f-181">**ユーザー アカウント**ダイアログ ボックスで、をクリックして、**詳細** タブ。</span><span class="sxs-lookup"><span data-stu-id="2894f-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="2894f-182">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2894f-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="2894f-183">**ローカル ユーザーとグループ**ダイアログ ボックスで、クリックして展開し、**ユーザー**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="2894f-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="2894f-184">右側のウィンドウでダブルクリック**インターネット ゲスト アカウント**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="2894f-185">**プロパティ**名前は、インターネット ゲスト アカウントとして使用 ダイアログ ボックスで、コピーします。</span><span class="sxs-lookup"><span data-stu-id="2894f-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="2894f-186">既定では、その名前は "USR_" で始まり、その次にコンピューターの名前が続きます。</span><span class="sxs-lookup"><span data-stu-id="2894f-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="2894f-187">**[プロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2894f-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="2894f-188">閉じる、**ローカル ユーザーとグループ** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="2894f-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="2894f-189">閉じる、**ユーザー アカウント** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="2894f-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="2894f-190">もう一方を閉じる**ユーザー アカウント** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="2894f-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="2894f-191">**Servicemodelsamples プロパティ** ダイアログ ボックスで、**セキュリティ** タブで、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="2894f-192">円記号の後にコンピューターの名前を入力し、たとえば、myMachineName でインターネット ユーザー アカウントの名前を貼り付けます\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="2894f-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="2894f-193">をクリックして**名前の確認**追加を確認します。</span><span class="sxs-lookup"><span data-stu-id="2894f-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="2894f-194">名前が有効な場合は、すべての文字が下線付きの大文字になります。</span><span class="sxs-lookup"><span data-stu-id="2894f-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5.  <span data-ttu-id="2894f-195">IIS 6.0 でもチェックのネットワーク サービスが表示されていること、**グループまたはユーザー名**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2894f-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="2894f-196">NETWORK SERVICE が表示されていない場合:</span><span class="sxs-lookup"><span data-stu-id="2894f-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="2894f-197">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2894f-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="2894f-198">**ユーザーまたはグループ**に円記号が、コンピューターの名の後にダイアログ ボックスで入力します。</span><span class="sxs-lookup"><span data-stu-id="2894f-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="2894f-199">型**サービス**円記号 (空白なし) 後にします。</span><span class="sxs-lookup"><span data-stu-id="2894f-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="2894f-200">をクリックして**名前の確認**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="2894f-201">複数の名前が見つかった場合は、選択**NETWORK SERVICE**  をクリック**OK**です。</span><span class="sxs-lookup"><span data-stu-id="2894f-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="2894f-202">をクリックして**OK**を閉じる、 **[ユーザーまたはグループ**] ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="2894f-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6.  <span data-ttu-id="2894f-203">Windows XP SP2 で IIS 5.1 を使用している場合は、インターネット ゲスト アカウントと"aspnet"の両方が表示されていることを確認、**グループまたはユーザー名**ボックス。</span><span class="sxs-lookup"><span data-stu-id="2894f-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="2894f-204">ASPNET ユーザーは、組み込みのメンバーである可能性があります**ユーザー**セキュリティ グループです。</span><span class="sxs-lookup"><span data-stu-id="2894f-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="2894f-205">場合は、場合、**ユーザー**  ダイアログ ボックスでグループが一覧表示されて、別のアイテムとして許可されているユーザーの一覧に追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2894f-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="2894f-206">ASPNET の一部であるかどうかを確認する、**ユーザー**セキュリティ グループ。</span><span class="sxs-lookup"><span data-stu-id="2894f-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="2894f-207">**開始**] メニューのをクリックして**コントロール パネルの [** です。</span><span class="sxs-lookup"><span data-stu-id="2894f-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="2894f-208">クリックして、**ユーザー アカウント**アイコン。</span><span class="sxs-lookup"><span data-stu-id="2894f-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="2894f-209">**グループ**列、ことを確認の値は、 **ASPNET** "Users"は、</span><span class="sxs-lookup"><span data-stu-id="2894f-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2894f-210">関連項目</span><span class="sxs-lookup"><span data-stu-id="2894f-210">See Also</span></span>  
 [<span data-ttu-id="2894f-211">インターネット インフォメーション サービスのホスティング手順</span><span class="sxs-lookup"><span data-stu-id="2894f-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
