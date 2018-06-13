---
title: '方法 : MMC スナップインを使用して証明書を参照する'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: d924121b9d9fa267fa7d1ada13c9dc5f5bf1523d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493351"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a><span data-ttu-id="b42ad-102">方法 : MMC スナップインを使用して証明書を参照する</span><span class="sxs-lookup"><span data-stu-id="b42ad-102">How to: View Certificates with the MMC Snap-in</span></span>
<span data-ttu-id="b42ad-103">X.509 証明書は、広く使用されている資格情報です。</span><span class="sxs-lookup"><span data-stu-id="b42ad-103">A common type of credential is the X.509 certificate.</span></span> <span data-ttu-id="b42ad-104">セキュリティで保護されたサービスやクライアントを作成する場合、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> メソッドなどのメソッドを使用して、クライアントやサービスの資格情報として使用する証明書を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b42ad-104">When creating secure services or clients, you can specify a certificate be used as the client or service credential by using methods such as the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method.</span></span> <span data-ttu-id="b42ad-105">このメソッドでは、証明書を格納するストアや証明書を検索するときに使用する値など、さまざまなパラメーターが必要になります。</span><span class="sxs-lookup"><span data-stu-id="b42ad-105">The method requires various parameters, such as the store where the certificate is stored and a value to use when searching for the certificate.</span></span> <span data-ttu-id="b42ad-106">次の手順では、コンピューター上のストアを調べて適切な証明書を検索する方法を示します。 </span><span class="sxs-lookup"><span data-stu-id="b42ad-106">The following procedure demonstrates how to examine the stores on a computer to find an appropriate certificate.</span></span> <span data-ttu-id="b42ad-107">証明書の拇印を検索する方法の例は[方法: 証明書のサムプリントを取得 ](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b42ad-107">For an example of finding the certificate thumbprint, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a><span data-ttu-id="b42ad-108">MMC スナップインで証明書を参照するには</span><span class="sxs-lookup"><span data-stu-id="b42ad-108">To view certificates in the MMC snap-in</span></span>  
  
1.  <span data-ttu-id="b42ad-109">コマンド プロンプト ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="b42ad-109">Open a Command Prompt window.</span></span>  
  
2.  <span data-ttu-id="b42ad-110">`mmc` と入力して、ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b42ad-110">Type `mmc` and press the ENTER key.</span></span> <span data-ttu-id="b42ad-111">ローカル コンピューターのストアにある証明書を表示するには、管理者のロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="b42ad-111">Note that to view certificates in the local machine store, you must be in the Administrator role.</span></span>  
  
3.  <span data-ttu-id="b42ad-112">**ファイル** メニューから **スナップインの追加/削除** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b42ad-112">On the **File** menu, click **Add/Remove Snap In**.</span></span>  
  
4.  <span data-ttu-id="b42ad-113">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b42ad-113">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="b42ad-114">**スタンドアロン スナップインの追加**ダイアログ ボックスで **証明書**を選択します。</span><span class="sxs-lookup"><span data-stu-id="b42ad-114">In the **Add Standalone Snap-in** dialog box, select **Certificates**.</span></span>  
  
6.  <span data-ttu-id="b42ad-115">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b42ad-115">Click **Add**.</span></span>  
  
7.  <span data-ttu-id="b42ad-116">**証明書スナップイン**ダイアログ ボックスで **コンピューター アカウント** を選択し **次** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b42ad-116">In the **Certificates snap-in** dialog box, select **Computer account** and click **Next**.</span></span> <span data-ttu-id="b42ad-117">必要に応じて、**ユーザー アカウント** または　**サービス アカウント** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="b42ad-117">Optionally, you can select **My User account** or **Service account**.</span></span> <span data-ttu-id="b42ad-118">そのコンピューターの管理者でない場合は、自分のユーザー アカウントの証明書のみを管理できます。</span><span class="sxs-lookup"><span data-stu-id="b42ad-118">If you are not an administrator of the computer, you can manage certificates only for your user account.</span></span>  
  
8.  <span data-ttu-id="b42ad-119">**コンピューターの選択** ダイアログ ボックスで **完了** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b42ad-119">In the **Select Computer** dialog box, click **Finish**.</span></span>  
  
9. <span data-ttu-id="b42ad-120">**スタンドアロン スナップインの追加** ダイアログ ボックスで **閉じる** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b42ad-120">In the **Add Standalone Snap-in** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="b42ad-121">**スナップインの追加と削除** ダイアログ ボックスで **OK** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b42ad-121">On the **Add/Remove Snap-in** dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="b42ad-122">**コンソール ルート** ウィンドウで **証明書 (ローカル コンピューター)** をクリックして、コンピューターの証明書ストアを表示します。</span><span class="sxs-lookup"><span data-stu-id="b42ad-122">In the **Console Root** window, click **Certificates (Local Computer)** to view the certificate stores for the computer.</span></span>  
  
12. <span data-ttu-id="b42ad-123">任意。</span><span class="sxs-lookup"><span data-stu-id="b42ad-123">Optional.</span></span> <span data-ttu-id="b42ad-124">必要に応じて、自分のアカウントの証明書を表示する場合は、手順 3. ～ 6. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="b42ad-124">To view certificates for your account, repeat steps 3 to 6.</span></span> <span data-ttu-id="b42ad-125">手順 7. では **コンピューター アカウント** を選択する代わりに **ユーザー アカウント** をクリックして、手順 8. ~ 10. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="b42ad-125">In step 7, instead of selecting **Computer account**, click **My User account** and repeat steps 8 to 10.</span></span>  
  
13. <span data-ttu-id="b42ad-126">任意。</span><span class="sxs-lookup"><span data-stu-id="b42ad-126">Optional.</span></span> <span data-ttu-id="b42ad-127">**ファイル** メニューのをクリックして**保存**または**名前を付けて保存**です。</span><span class="sxs-lookup"><span data-stu-id="b42ad-127">On the **File** menu, click **Save** or **Save As**.</span></span> <span data-ttu-id="b42ad-128">再利用できるようにコンソール ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="b42ad-128">Save the console file for later reuse.</span></span>  
  
## <a name="viewing-certificates-with-internet-explorer"></a><span data-ttu-id="b42ad-129">Internet Explorer を使用した証明書の表示</span><span class="sxs-lookup"><span data-stu-id="b42ad-129">Viewing Certificates with Internet Explorer</span></span>  
 <span data-ttu-id="b42ad-130">Internet Explorer を使用して、証明書を表示、エクスポート、インポート、または削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="b42ad-130">You can also view, export, import, and delete certificates by using Internet Explorer.</span></span>  
  
#### <a name="to-view-certificates-with-internet-explorer"></a><span data-ttu-id="b42ad-131">Internet Explorer で証明書を表示するには</span><span class="sxs-lookup"><span data-stu-id="b42ad-131">To view certificates with Internet Explorer</span></span>  
  
1.  <span data-ttu-id="b42ad-132">Internet Explorer で、をクリックして**ツール**をクリックし、**インターネット オプション**を表示する、**インターネット オプション** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="b42ad-132">In Internet Explorer, click **Tools**, then click **Internet Options** to display the **Internet Options** dialog box.</span></span>  
  
2.  <span data-ttu-id="b42ad-133">クリックして、**コンテンツ**タブです。</span><span class="sxs-lookup"><span data-stu-id="b42ad-133">Click the **Content** tab.</span></span>  
  
3.  <span data-ttu-id="b42ad-134">**証明書**をクリックして**証明書**です。</span><span class="sxs-lookup"><span data-stu-id="b42ad-134">Under **Certificates**, click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="b42ad-135">任意の証明書の詳細を表示し、証明書を選択し、クリックして**ビュー**です。</span><span class="sxs-lookup"><span data-stu-id="b42ad-135">To view details of any certificate, select the certificate and click **View**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42ad-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b42ad-136">See Also</span></span>  
 [<span data-ttu-id="b42ad-137">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="b42ad-137">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="b42ad-138">方法 : 開発中に使用する一時的な証明書を作成する</span><span class="sxs-lookup"><span data-stu-id="b42ad-138">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [<span data-ttu-id="b42ad-139">方法 : 証明書のサムプリントを取得する</span><span class="sxs-lookup"><span data-stu-id="b42ad-139">How to: Retrieve the Thumbprint of a Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
