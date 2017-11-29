---
title: "方法 : MMC スナップインを使用して証明書を参照する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 43925a301d4f0d2ca1a852912255be49dd330ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="1df3a-102">方法 : MMC スナップインを使用して証明書を参照する</span><span class="sxs-lookup"><span data-stu-id="1df3a-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="1df3a-103">X.509 証明書は、広く使用されている資格情報です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="1df3a-104">セキュリティで保護されたサービスやクライアントを作成する場合、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> メソッドなどのメソッドを使用して、クライアントやサービスの資格情報として使用する証明書を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1df3a-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="1df3a-105">このメソッドでは、証明書を格納するストアや証明書を検索するときに使用する値など、さまざまなパラメーターが必要になります。</span><span class="sxs-lookup"><span data-stu-id="1df3a-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="1df3a-106">次の手順では、コンピューター上のストアを調べて適切な証明書を検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1df3a-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="1df3a-107">証明書の拇印を検索の例は、次を参照してください。[する方法: 証明書のサムプリントを取得](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="1df3a-108">MMC スナップインで証明書を参照するには</span><span class="sxs-lookup"><span data-stu-id="1df3a-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="1df3a-109">コマンド プロンプト ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="1df3a-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="1df3a-110">型`mmc`ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1df3a-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="1df3a-111">ローカル コンピューターのストアにある証明書を表示するには、管理者のロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="1df3a-112">**ファイル** メニューのをクリックして**スナップインの追加/削除**です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="1df3a-113">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1df3a-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="1df3a-114">**スタンドアロン スナップインの追加**ダイアログ ボックスで、**証明書**です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="1df3a-115">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1df3a-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="1df3a-116">**証明書スナップイン**ダイアログ ボックスで、**コンピューター アカウント** をクリック**次**です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="1df3a-117">必要に応じて、選択**ユーザー アカウント**または**サービス アカウント**です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="1df3a-118">そのコンピューターの管理者でない場合は、自分のユーザー アカウントの証明書のみを管理できます。</span><span class="sxs-lookup"><span data-stu-id="1df3a-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="1df3a-119">**コンピューターの選択**ダイアログ ボックスで、をクリックして**完了**です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="1df3a-120">**スタンドアロン スナップインの追加**ダイアログ ボックスで、をクリックして**閉じる**です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="1df3a-121">**スナップインの追加と削除**ダイアログ ボックスで、をクリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="1df3a-122">**コンソール ルート**ウィンドウで、をクリックして**証明書 (ローカル コンピューター)**コンピューターのストアに証明書を表示します。</span><span class="sxs-lookup"><span data-stu-id="1df3a-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="1df3a-123">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-123">Optional.</span></span> <span data-ttu-id="1df3a-124">自分のアカウントの証明書を表示するには、手順 3. ～ 6. を繰り返し、</span><span class="sxs-lookup"><span data-stu-id="1df3a-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="1df3a-125">手順 7. で選択する代わりに**コンピューター アカウント**をクリックして**ユーザー アカウント**手順 8. ~ 10. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1df3a-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="1df3a-126">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-126">Optional.</span></span> <span data-ttu-id="1df3a-127">**ファイル** メニューのをクリックして**保存**または**名前を付けて保存**です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="1df3a-128">再利用できるようにコンソール ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="1df3a-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="1df3a-129">Internet Explorer を使用した証明書の表示</span><span class="sxs-lookup"><span data-stu-id="1df3a-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="1df3a-130">Internet Explorer を使用して、証明書を表示、エクスポート、インポート、または削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="1df3a-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="1df3a-131">Internet Explorer で証明書を表示するには</span><span class="sxs-lookup"><span data-stu-id="1df3a-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="1df3a-132">Internet Explorer で、をクリックして**ツール**をクリックし、**インターネット オプション**を表示する、**インターネット オプション** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="1df3a-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="1df3a-133">クリックして、**コンテンツ**タブです。</span><span class="sxs-lookup"><span data-stu-id="1df3a-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="1df3a-134">**証明書**をクリックして**証明書**です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="1df3a-135">任意の証明書の詳細を表示し、証明書を選択し、クリックして**ビュー**です。</span><span class="sxs-lookup"><span data-stu-id="1df3a-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df3a-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="1df3a-136">See Also</span></span>  
 [<span data-ttu-id="1df3a-137">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="1df3a-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="1df3a-138">方法: 開発中に使用するための一時的な証明書を作成</span><span class="sxs-lookup"><span data-stu-id="1df3a-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [<span data-ttu-id="1df3a-139">方法: 証明書のサムプリントの取得</span><span class="sxs-lookup"><span data-stu-id="1df3a-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
