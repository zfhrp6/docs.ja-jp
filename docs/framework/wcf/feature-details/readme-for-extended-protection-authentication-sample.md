---
title: "拡張保護認証のサンプルの ReadMe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 78e787c129c0161e8730472124ee4162e2d1ba9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="b04d8-102">拡張保護認証のサンプルの ReadMe</span><span class="sxs-lookup"><span data-stu-id="b04d8-102">ReadMe for Extended Protection Authentication Sample</span></span>
<span data-ttu-id="b04d8-103">拡張保護を攻撃者 (、「- 内の中間」) がクライアントの資格情報をインターセプトし、クライアントの目的のサーバーのセキュリティで保護されたリソースにアクセスするために使用、中間の (MITM) 攻撃を防ぐためにセキュリティ イニシアチブです。</span><span class="sxs-lookup"><span data-stu-id="b04d8-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>  
  
 <span data-ttu-id="b04d8-104">詳細については、次を参照してください。[認証の概要の拡張保護](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="b04d8-104">For more information, see [Extended Protection for Authentication Overview](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b04d8-105">このサンプルは、IIS でホストされた場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="b04d8-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="b04d8-106">このサンプルは HTTPS をサポートしないので、Visual Studio Development Server 上では機能しません。</span><span class="sxs-lookup"><span data-stu-id="b04d8-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b04d8-107">サンプルをセットアップしてビルドし、実行するには</span><span class="sxs-lookup"><span data-stu-id="b04d8-107">To Set Up, Build, and Run the Sample</span></span>  
  
1.  <span data-ttu-id="b04d8-108">[プログラムの追加と削除] の [Windows の機能] から IIS をインストールします。</span><span class="sxs-lookup"><span data-stu-id="b04d8-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>  
  
2.  <span data-ttu-id="b04d8-109">Windows 機能の Windows 認証を有効にします ([インターネット インフォメーション サービス] -> [World Wide Web サービス] -> [セキュリティ] -> [Windows 認証])。</span><span class="sxs-lookup"><span data-stu-id="b04d8-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>  
  
3.  <span data-ttu-id="b04d8-110">Windows 機能の HTTP アクティブ化を有効にします ([Microsoft .NET Framework 3.5.1] -> [Windows Communication Foundation HTTP Activation])。</span><span class="sxs-lookup"><span data-stu-id="b04d8-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>  
  
4.  <span data-ttu-id="b04d8-111">このサンプルを実行するには、サーバーとの安全なチャネルを確立する必要のあるクライアントが必要なので、インターネット インフォメーション サービス (IIS) マネージャーからインストールすることのできるサーバー証明書が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b04d8-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="b04d8-112">IIS マネージャーを開いて、[機能表示] タブから [サーバー証明書] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b04d8-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>  
  
    2.  <span data-ttu-id="b04d8-113">このサンプルをテストする目的で、自己署名証明書を作成できます </span><span class="sxs-lookup"><span data-stu-id="b04d8-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="b04d8-114">(インターネット エクスプローラーで証明書の安全性に関するプロンプトが表示されないようにする場合は、信頼されたルート証明機関ストアに証明書をインストールできます)。</span><span class="sxs-lookup"><span data-stu-id="b04d8-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>  
  
5.  <span data-ttu-id="b04d8-115">既定の Web サイトの操作ウィンドウに移動します。</span><span class="sxs-lookup"><span data-stu-id="b04d8-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="b04d8-116">[サイトの編集] の [バインド] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b04d8-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="b04d8-117">存在しない場合は、種類として HTTPS を追加します。ポート番号に 443 を指定し、前の手順で作成した SSL 証明書を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b04d8-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>  
  
6.  <span data-ttu-id="b04d8-118">サービスをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b04d8-118">Build the service.</span></span> <span data-ttu-id="b04d8-119">(プロジェクト プロパティで指定されたビルド後のアクションから) IIS に仮想ディレクトリが作成され、サービスを Web ホスト サービスにするために必要な dll、.svc、および構成ファイルがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="b04d8-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>  
  
7.  <span data-ttu-id="b04d8-120">IIS マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="b04d8-120">Open the IIS Manager.</span></span> <span data-ttu-id="b04d8-121">前の手順で作成した仮想ディレクトリ (ExtendedProtection) を右クリックして、[アプリケーションへの変換] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b04d8-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>  
  
8.  <span data-ttu-id="b04d8-122">この仮想ディレクトリの認証モジュールを IIS マネージャーで開き、Windows 認証を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b04d8-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>  
  
9. <span data-ttu-id="b04d8-123">このサンプルでは対応する ExtendedProtection 設定が [常に] に設定されているので、この仮想ディレクトリの Windows 認証の [詳細設定] を開き、[必須] に設定します。</span><span class="sxs-lookup"><span data-stu-id="b04d8-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>  
  
10. <span data-ttu-id="b04d8-124">ブラウザー ウィンドウから URL にアクセスして、サービスをテストできます。</span><span class="sxs-lookup"><span data-stu-id="b04d8-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="b04d8-125">コンピューター間でこの URL にアクセスする場合は、すべての受信 HTTP および HTTPS 通信に対してファイアウォールが開かれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b04d8-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>  
  
11. <span data-ttu-id="b04d8-126">クライアント構成ファイルを開きのフル コンピューター名を指定、\<クライアント >-\<エンドポイント >-アドレスの属性、<< full_machine_name >> を置換します。</span><span class="sxs-lookup"><span data-stu-id="b04d8-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing <<full_machine_name>>.</span></span>  
  
12. <span data-ttu-id="b04d8-127">クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="b04d8-127">Run the client.</span></span> <span data-ttu-id="b04d8-128">クライアントがセキュリティで保護されたチャネルを確立し、エンドポイント保護を使用してサービスと通信します。</span><span class="sxs-lookup"><span data-stu-id="b04d8-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
