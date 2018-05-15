---
title: WCF 開発ツールの使用
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 41d2ee2881b79ffb086a931ec6d271d409ac66db
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="aaa77-102">WCF 開発ツールの使用</span><span class="sxs-lookup"><span data-stu-id="aaa77-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="aaa77-103">このセクションでは、WCFservice の開発に役立つ Visual Studio 開発ツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="aaa77-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="aaa77-104">基盤として Visual Studio テンプレートを使用して、独自のサービスをすばやく作成し、デバッグし、サービスをテストする WCF サービスの自動ホストと WCF テスト クライアントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="aaa77-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="aaa77-105">これらのツールによって、高速でシームレスなデバッグとテストのサイクルが実現し、初期の段階においてホスト モデルのコミットが必要なくなります。</span><span class="sxs-lookup"><span data-stu-id="aaa77-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="aaa77-106">WCF の開発者用ツール</span><span class="sxs-lookup"><span data-stu-id="aaa77-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="aaa77-107">WCF Visual Studio テンプレート</span><span class="sxs-lookup"><span data-stu-id="aaa77-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="aaa77-108">Visual Studio で、定義済みの Visual Studio プロジェクトと項目テンプレートを使用すると、WCF サービスや周辺アプリケーションを迅速に構築します。</span><span class="sxs-lookup"><span data-stu-id="aaa77-108">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="aaa77-109">WCF サービス ホスト (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="aaa77-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="aaa77-110">WCF サービスの自動ホスト (WcfSvcHost.exe) では、Visual Studio デバッガーを自動的にホストし、実装しているサービスをテストする (F5) を起動することができます。</span><span class="sxs-lookup"><span data-stu-id="aaa77-110">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="aaa77-111">検出して潜在的なエラーを修正する WCF テスト クライアント (wcfTestClient.exe) または独自のクライアントを使用して、サービスをテストできます。</span><span class="sxs-lookup"><span data-stu-id="aaa77-111">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="aaa77-112">WCF のテスト用クライアント (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="aaa77-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="aaa77-113">WCF テスト クライアント (WcfTestClient.exe) は、任意の型のパラメーターを入力し、そのサービス、およびサービスの応答を返信ビューに入力することができますを GUI ツールです。</span><span class="sxs-lookup"><span data-stu-id="aaa77-113">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="aaa77-114">テストできるように WCF サービスの自動ホストと組み合わせると、シームレスにサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="aaa77-114">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="aaa77-115">XML からのデータ型クラスの生成</span><span class="sxs-lookup"><span data-stu-id="aaa77-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="aaa77-116">クリップボードに格納されている XML データは、コード ページに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="aaa77-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="aaa77-117">データで定義されているクラスは、コード型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="aaa77-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="aaa77-118">管理特権を必要としないツールの使用</span><span class="sxs-lookup"><span data-stu-id="aaa77-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="aaa77-119">名前空間の ACL (アクセス制御リスト) を作成する WCF サービスの開発を管理者特権のないユーザーを有効にするには、"http://+:8731/Design_Time_Addresses"Visual Studio のインストール中にします。</span><span class="sxs-lookup"><span data-stu-id="aaa77-119">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="aaa77-120">この ACL は (UI) に設定され、コンピューターにログオンしているすべての対話ユーザーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="aaa77-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="aaa77-121">管理者は、この ACL にユーザーを追加または削除したり、追加のポートを開いたりできます。この ACL によって、既定の構成で、WCF テンプレートまたは WF テンプレートでデータを送受信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="aaa77-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="aaa77-122">ユーザーが管理者特権を与えずに WCF サービスの自動ホスト (wcfSvcHost.exe) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="aaa77-122">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="aaa77-123">システム特権のある管理者アカウントで [!INCLUDE[wv](../../../includes/wv-md.md)] の Netsh.exe ツールを使用すると、アクセスを変更できます。</span><span class="sxs-lookup"><span data-stu-id="aaa77-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="aaa77-124">Netsh.exe の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="aaa77-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="aaa77-125">Netsh.exe の詳細については、次を参照してください。 [Netsh.exe ツールとコマンド ライン スイッチを使用する方法](http://go.microsoft.com/fwlink/?LinkId=97877)です。</span><span class="sxs-lookup"><span data-stu-id="aaa77-125">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa77-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="aaa77-126">See Also</span></span>  
 [<span data-ttu-id="aaa77-127">WCF Visual Studio テンプレート</span><span class="sxs-lookup"><span data-stu-id="aaa77-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="aaa77-128">WCF サービス ホスト (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="aaa77-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="aaa77-129">WCF のテスト用クライアント (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="aaa77-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
