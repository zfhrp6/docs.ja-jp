---
title: "仮想ディレクトリのセットアップ手順"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: "36"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b727f391abfeb1112de1b6cde3ceb564d3860974
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="030d3-102">仮想ディレクトリのセットアップ手順</span><span class="sxs-lookup"><span data-stu-id="030d3-102">Virtual Directory Setup Instructions</span></span>
<span data-ttu-id="030d3-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルは、servicemodelsamples という共通の仮想ディレクトリの共有を想定しています。この仮想ディレクトリは %SystemDrive%\inetpub\wwwroot\servicemodelsamples フォルダーにマップされています。</span><span class="sxs-lookup"><span data-stu-id="030d3-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="030d3-104">%SystemDrive% は、インターネット インフォメーション サービス (IIS) がインストールされているドライブの場所に応じて、通常は C: または D: になります。</span><span class="sxs-lookup"><span data-stu-id="030d3-104">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="030d3-105">ファイルを Setupvroot.bat と Cleanupvroot.bat を実行することができます、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)仮想ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="030d3-105">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="030d3-106">この仮想ディレクトリを手動で作成する場合は、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="030d3-106">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="030d3-107">手順</span><span class="sxs-lookup"><span data-stu-id="030d3-107">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="030d3-108">IIS 7.0 または 7.5 で仮想ディレクトリを作成するには</span><span class="sxs-lookup"><span data-stu-id="030d3-108">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="030d3-109">**開始** メニューのをクリックして**実行**、入力**inetmgr**を開くには、インターネット インフォメーション サービス (IIS) MMC スナップイン。</span><span class="sxs-lookup"><span data-stu-id="030d3-109">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="030d3-110">左側のウィンドウで、コンピューターの名前を持つノードを展開し、展開、**サイト**ノード。</span><span class="sxs-lookup"><span data-stu-id="030d3-110">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3.  <span data-ttu-id="030d3-111">右クリック**既定の Web サイト**、し、**アプリケーションの追加**を開くには、**追加のアプリケーション ウィンドウ**します。</span><span class="sxs-lookup"><span data-stu-id="030d3-111">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4.  <span data-ttu-id="030d3-112">ウィンドウで、次のように入力します。`servicemodelsamples`として作成している仮想ディレクトリのエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="030d3-112">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="030d3-113">次のディレクトリを作成します。%SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="030d3-113">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6.  <span data-ttu-id="030d3-114">物理パスを %SystemDrive%\inetpub\wwwroot\servicemodelsamples に設定します。</span><span class="sxs-lookup"><span data-stu-id="030d3-114">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="030d3-115">WCF サンプルの多くは、ビルド時にサービス実行可能ファイルをこの場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="030d3-115">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7.  <span data-ttu-id="030d3-116">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="030d3-116">Click **OK**.</span></span> <span data-ttu-id="030d3-117">Web アプリケーションが、WCF サンプル用に作成されました。</span><span class="sxs-lookup"><span data-stu-id="030d3-117">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="030d3-118">すべての [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サンプルで同じ servicemodelsamples Web アプリケーションを使用するため、この作業は 1 回だけ実行してください。</span><span class="sxs-lookup"><span data-stu-id="030d3-118">This task must be performed only once, because all of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="030d3-119">このドキュメントでは、`virtual directory`という用語は `Web application`と同じ意味で使用しています。</span><span class="sxs-lookup"><span data-stu-id="030d3-119">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="030d3-120">仮想ディレクトリの作成に加えて、さらに仮想ディレクトリのプロパティを設定し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの実行を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="030d3-120">In addition to creating the virtual directory, you must also set its properties to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to run.</span></span> <span data-ttu-id="030d3-121">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="030d3-121">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="030d3-122">仮想ディレクトリを IIS 5.1 または 6.0 で作成するには</span><span class="sxs-lookup"><span data-stu-id="030d3-122">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="030d3-123">コマンド プロンプト ウィンドウを開き`start inetmgr`を開くには、インターネット インフォメーション サービス (IIS) MMC スナップイン。</span><span class="sxs-lookup"><span data-stu-id="030d3-123">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="030d3-124">左側のウィンドウで、コンピューターの名前を持つノードを展開し、展開、 **Websites**ノード。</span><span class="sxs-lookup"><span data-stu-id="030d3-124">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3.  <span data-ttu-id="030d3-125">右クリック**既定の Web サイト**選択**、新しい仮想ディレクトリ**仮想ディレクトリの作成ウィザードを開きます。</span><span class="sxs-lookup"><span data-stu-id="030d3-125">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4.  <span data-ttu-id="030d3-126">ウィザードで、次のように入力します。`servicemodelsamples`として作成している仮想ディレクトリのエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="030d3-126">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5.  <span data-ttu-id="030d3-127">パスを %SystemDrive%\inetpub\wwwroot\servicemodelsamples に設定します。</span><span class="sxs-lookup"><span data-stu-id="030d3-127">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="030d3-128">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サンプルの多くは、ビルド時にサービス実行可能ファイルをこの場所にコピーします。</span><span class="sxs-lookup"><span data-stu-id="030d3-128">Most of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples copy service executable files to this location when built.</span></span>  
  
6.  <span data-ttu-id="030d3-129">**[次へ]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="030d3-129">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="030d3-130">既定では、次のチェック ボックスがオンになっています。</span><span class="sxs-lookup"><span data-stu-id="030d3-130">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="030d3-131">**読み取り**</span><span class="sxs-lookup"><span data-stu-id="030d3-131">**Read**</span></span>  
  
    -   <span data-ttu-id="030d3-132">**(ASP) などのスクリプトを実行します。**</span><span class="sxs-lookup"><span data-stu-id="030d3-132">**Run scripts (such as ASP)**</span></span>  
  
8.  <span data-ttu-id="030d3-133">をクリックして**[次へ]**、順にクリック**完了**ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="030d3-133">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="030d3-134">すべての [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サンプルで同じ servicemodelsamples 仮想ディレクトリを使用するため、この作業は 1 回だけ実行してください。</span><span class="sxs-lookup"><span data-stu-id="030d3-134">This task must be performed only once because all of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="030d3-135">IIS 7.0 での他の仮想ディレクトリのプロパティまたは 7.5 を設定するには</span><span class="sxs-lookup"><span data-stu-id="030d3-135">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="030d3-136">servicemodelsamples ノードをクリックします。</span><span class="sxs-lookup"><span data-stu-id="030d3-136">Click the servicemodelsamples node.</span></span> <span data-ttu-id="030d3-137">ウィンドウの下端に沿って 2 つのビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="030d3-137">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="030d3-138">選択**機能ビュー**が選択されていない場合。</span><span class="sxs-lookup"><span data-stu-id="030d3-138">Select **Features View** if it isn’t already selected.</span></span>  
  
2.  <span data-ttu-id="030d3-139">エントリをダブルクリックして**ディレクトリの参照**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-139">Double-click the entry for **Directory Browsing**.</span></span>  
  
3.  <span data-ttu-id="030d3-140">[操作] ウィンドウで、選択、**を有効にする**オプション。</span><span class="sxs-lookup"><span data-stu-id="030d3-140">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="030d3-141">これにより、Internet Explorer でディレクトリにアクセスできるようになり、サービスのデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="030d3-141">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="030d3-142">最後に、servicemodelsamples フォルダーのセキュリティ プロパティを、他のユーザーがアクセスできるように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="030d3-142">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="030d3-143">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="030d3-143">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="030d3-144">仮想ディレクトリの追加プロパティを IIS 5.1 または 6.0 で設定するには</span><span class="sxs-lookup"><span data-stu-id="030d3-144">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="030d3-145">Servicemodelsamples ノードを右クリックし、をクリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-145">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="030d3-146">既定では、次のチェック ボックスがオンになっています。</span><span class="sxs-lookup"><span data-stu-id="030d3-146">By default, the following check boxes are selected:</span></span>  
  
    -   <span data-ttu-id="030d3-147">**読み取り**</span><span class="sxs-lookup"><span data-stu-id="030d3-147">**Read**</span></span>  
  
    -   <span data-ttu-id="030d3-148">**[ログ アクセス]**</span><span class="sxs-lookup"><span data-stu-id="030d3-148">**Log visits**</span></span>  
  
    -   <span data-ttu-id="030d3-149">**このリソースします。**</span><span class="sxs-lookup"><span data-stu-id="030d3-149">**Index this resource**</span></span>  
  
3.  <span data-ttu-id="030d3-150">選択、**ディレクトリの参照**チェック ボックスをオンします。</span><span class="sxs-lookup"><span data-stu-id="030d3-150">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="030d3-151">これにより、Internet Explorer でディレクトリにアクセスできるようになり、サービスのデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="030d3-151">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="030d3-152">IIS 7.0 または 7.5 でフォルダーのセキュリティ プロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="030d3-152">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1.  <span data-ttu-id="030d3-153">%SystemDrive%\inetpub\wwwroot\servicemodelsamples に移動します。</span><span class="sxs-lookup"><span data-stu-id="030d3-153">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="030d3-154">Servicemodelsamples フォルダーを右クリックし、をクリックして**共有**または**共有で**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-154">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3.  <span data-ttu-id="030d3-155">左側にある下向きの矢印をクリックして、**追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="030d3-155">Click the down arrow to the left of the **Add** button.</span></span>  
  
4.  <span data-ttu-id="030d3-156">選択、**検索**エントリです。</span><span class="sxs-lookup"><span data-stu-id="030d3-156">Select the **Find** entry.</span></span> <span data-ttu-id="030d3-157">**ユーザーまたはグループ**ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="030d3-157">The **Select Users or Groups** window opens.</span></span>  
  
5.  <span data-ttu-id="030d3-158">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="030d3-158">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="030d3-159">をクリックして**場所**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-159">Click **Locations**.</span></span> <span data-ttu-id="030d3-160">**場所**ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="030d3-160">The **Locations** window is now open.</span></span>  
  
7.  <span data-ttu-id="030d3-161">使用するコンピューターのエントリを選択します。</span><span class="sxs-lookup"><span data-stu-id="030d3-161">Select the entry for the computer being used.</span></span> <span data-ttu-id="030d3-162">一覧表示されているドメインやネットワークのエントリではなく、ローカル コンピューターを選択してください。</span><span class="sxs-lookup"><span data-stu-id="030d3-162">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="030d3-163">コンピューターを選択した後にをクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-163">After you have selected the computer, click **OK**.</span></span>  
  
8.  <span data-ttu-id="030d3-164">をクリックして**今すぐ検索**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-164">Click **Find Now**.</span></span> <span data-ttu-id="030d3-165">これで、ローカル コンピューターに関連付けられたオブジェクトが検索結果に表示されます。</span><span class="sxs-lookup"><span data-stu-id="030d3-165">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="030d3-166">検索、 **IIS_IUSRS**内のエントリ、**名 (相対識別名)**列です。</span><span class="sxs-lookup"><span data-stu-id="030d3-166">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="030d3-167">そのエントリを選択し、をクリックして**OK**結果ウィンドウの検索を閉じます。</span><span class="sxs-lookup"><span data-stu-id="030d3-167">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="030d3-168">をクリックして**OK**を閉じる、 **ユーザーまたはグループ**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="030d3-168">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="030d3-169">をクリックして**共有**変更を保持します。</span><span class="sxs-lookup"><span data-stu-id="030d3-169">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="030d3-170">共有を有効にする変更が完了した後にをクリックして**完了**を閉じる、**ファイルの共有**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="030d3-170">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="030d3-171">フォルダーのセキュリティ プロパティを IIS 5.1 または 6.0 で設定するには</span><span class="sxs-lookup"><span data-stu-id="030d3-171">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1.  <span data-ttu-id="030d3-172">%SystemDrive%\inetpub\wwwroot\servicemodelsamples に移動します。</span><span class="sxs-lookup"><span data-stu-id="030d3-172">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2.  <span data-ttu-id="030d3-173">右クリックし、 **servicemodelsamples**フォルダーをクリックして**共有とセキュリティ。**</span><span class="sxs-lookup"><span data-stu-id="030d3-173">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3.  <span data-ttu-id="030d3-174">**[セキュリティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="030d3-174">Click the **Security** tab.</span></span>  
  
4.  <span data-ttu-id="030d3-175">IIS 6.0 を使用している場合、**グループまたはユーザー名**ボックスで、チェックするかどうか**インターネット ゲスト アカウント**が表示されています。</span><span class="sxs-lookup"><span data-stu-id="030d3-175">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="030d3-176">表示されていない場合:</span><span class="sxs-lookup"><span data-stu-id="030d3-176">If it is not listed:</span></span>  
  
    1.  <span data-ttu-id="030d3-177">をクリックして**開始**] をクリックし、**コントロール パネルの [**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-177">Click **Start** and then click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="030d3-178">表示されない場合、**ユーザー アカウント** アイコンをクリックして**カテゴリのビューに切り替えます**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-178">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3.  <span data-ttu-id="030d3-179">クリックして、**ユーザー アカウント**アイコン。</span><span class="sxs-lookup"><span data-stu-id="030d3-179">Click the **User Accounts** icon.</span></span>  
  
    4.  <span data-ttu-id="030d3-180">「またはコントロール パネルを選んで」クリックして**ユーザー アカウント**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-180">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5.  <span data-ttu-id="030d3-181">**ユーザー アカウント**ダイアログ ボックスで、をクリックして、**詳細** タブ。</span><span class="sxs-lookup"><span data-stu-id="030d3-181">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6.  <span data-ttu-id="030d3-182">**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="030d3-182">Click **Advanced**.</span></span>  
  
    7.  <span data-ttu-id="030d3-183">**ローカル ユーザーとグループ**ダイアログ ボックスで、クリックして展開し、**ユーザー**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="030d3-183">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8.  <span data-ttu-id="030d3-184">右側のウィンドウでダブルクリック**インターネット ゲスト アカウント**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-184">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="030d3-185">**プロパティ**名前は、インターネット ゲスト アカウントとして使用 ダイアログ ボックスで、コピーします。</span><span class="sxs-lookup"><span data-stu-id="030d3-185">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="030d3-186">既定では、その名前は "USR_" で始まり、その次にコンピューターの名前が続きます。</span><span class="sxs-lookup"><span data-stu-id="030d3-186">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="030d3-187">**[プロパティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="030d3-187">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="030d3-188">閉じる、**ローカル ユーザーとグループ** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="030d3-188">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="030d3-189">閉じる、**ユーザー アカウント** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="030d3-189">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="030d3-190">もう一方を閉じる**ユーザー アカウント** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="030d3-190">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="030d3-191">**Servicemodelsamples プロパティ** ダイアログ ボックスで、**セキュリティ** タブで、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-191">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="030d3-192">円記号の後にコンピューターの名前を入力し、たとえば、myMachineName でインターネット ユーザー アカウントの名前を貼り付けます\\InternetGuestAccountName %</span><span class="sxs-lookup"><span data-stu-id="030d3-192">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="030d3-193">をクリックして**名前の確認**追加を確認します。</span><span class="sxs-lookup"><span data-stu-id="030d3-193">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="030d3-194">名前が有効な場合は、すべての文字が下線付きの大文字になります。</span><span class="sxs-lookup"><span data-stu-id="030d3-194">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5.  <span data-ttu-id="030d3-195">IIS 6.0 でもチェックのネットワーク サービスが表示されていること、**グループまたはユーザー名**ボックス。</span><span class="sxs-lookup"><span data-stu-id="030d3-195">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="030d3-196">NETWORK SERVICE が表示されていない場合:</span><span class="sxs-lookup"><span data-stu-id="030d3-196">If NETWORK SERVICE is not listed:</span></span>  
  
    1.  <span data-ttu-id="030d3-197">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="030d3-197">Click **Add**.</span></span>  
  
    2.  <span data-ttu-id="030d3-198">**ユーザーまたはグループ**に円記号が、コンピューターの名の後にダイアログ ボックスで入力します。</span><span class="sxs-lookup"><span data-stu-id="030d3-198">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3.  <span data-ttu-id="030d3-199">型**サービス**円記号 (空白なし) 後にします。</span><span class="sxs-lookup"><span data-stu-id="030d3-199">Type **service** after the backslash (no space).</span></span>  
  
    4.  <span data-ttu-id="030d3-200">をクリックして**名前の確認**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-200">Click **Check names**.</span></span>  
  
    5.  <span data-ttu-id="030d3-201">複数の名前が見つかった場合は、選択**NETWORK SERVICE**  をクリック**OK**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-201">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6.  <span data-ttu-id="030d3-202">をクリックして**OK**を閉じる、 **[ユーザーまたはグループ**] ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="030d3-202">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6.  <span data-ttu-id="030d3-203">Windows XP SP2 で IIS 5.1 を使用している場合は、インターネット ゲスト アカウントと"aspnet"の両方が表示されていることを確認、**グループまたはユーザー名**ボックス。</span><span class="sxs-lookup"><span data-stu-id="030d3-203">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="030d3-204">ASPNET ユーザーは、組み込みのメンバーである可能性があります**ユーザー**セキュリティ グループです。</span><span class="sxs-lookup"><span data-stu-id="030d3-204">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="030d3-205">場合は、場合、**ユーザー**  ダイアログ ボックスでグループが一覧表示されて、別のアイテムとして許可されているユーザーの一覧に追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="030d3-205">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="030d3-206">ASPNET の一部であるかどうかを確認する、**ユーザー**セキュリティ グループ。</span><span class="sxs-lookup"><span data-stu-id="030d3-206">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1.  <span data-ttu-id="030d3-207">**開始**] メニューのをクリックして**コントロール パネルの [**です。</span><span class="sxs-lookup"><span data-stu-id="030d3-207">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="030d3-208">クリックして、**ユーザー アカウント**アイコン。</span><span class="sxs-lookup"><span data-stu-id="030d3-208">Click the **User Accounts** icon.</span></span>  
  
    3.  <span data-ttu-id="030d3-209">**グループ**列、ことを確認の値は、 **ASPNET** "Users"は、</span><span class="sxs-lookup"><span data-stu-id="030d3-209">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="030d3-210">関連項目</span><span class="sxs-lookup"><span data-stu-id="030d3-210">See Also</span></span>  
 [<span data-ttu-id="030d3-211">インターネット情報サービスのホスティング手順</span><span class="sxs-lookup"><span data-stu-id="030d3-211">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
