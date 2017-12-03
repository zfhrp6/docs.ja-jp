---
title: "WCF 開発ツールの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9532363adafd492ca35e10e6d20c788ddf5b1d17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="837b7-102">WCF 開発ツールの使用</span><span class="sxs-lookup"><span data-stu-id="837b7-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="837b7-103">ここでは、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] サービスの開発に役立つ [!INCLUDE[indigo1](../../../includes/indigo1-md.md)][!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 開発ツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="837b7-103">This section describes the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)][!INCLUDE[indigo1](../../../includes/indigo1-md.md)] development tools that can assist you in developing your [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]service.</span></span>  
  
 <span data-ttu-id="837b7-104">基盤となる [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] テンプレートを使用して独自のサービスをすばやく構築し、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホストと [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアントを使用してサービスをデバッグおよびテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="837b7-104">You can use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] templates as a foundation to quickly build your own service, then use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host and [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client to debug and test your service.</span></span> <span data-ttu-id="837b7-105">これらのツールによって、高速でシームレスなデバッグとテストのサイクルが実現し、初期の段階でホスト モデルにコミットする必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="837b7-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="837b7-106">WCF の開発者用ツール</span><span class="sxs-lookup"><span data-stu-id="837b7-106">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="837b7-107">WCF Visual Studio テンプレート</span><span class="sxs-lookup"><span data-stu-id="837b7-107">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
  
 <span data-ttu-id="837b7-108">定義済みの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] プロジェクト テンプレートと項目テンプレートを [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で使用すると、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスや周辺アプリケーションをすばやく構築できます。</span><span class="sxs-lookup"><span data-stu-id="837b7-108">You can use the predefined [!INCLUDE[indigo2](../../../includes/indigo2-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] project and item templates in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] to quickly build [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="837b7-109">WCF サービス ホスト (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="837b7-109">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="837b7-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホスト (WcfSvcHost.exe) を使用すると、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] デバッガーを起動して (F5 キーを押します)、実装しているサービスを自動的にホストおよびテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="837b7-110">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (WcfSvcHost.exe) allows you to launch the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="837b7-111">その後、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のテスト用クライアント (wcfTestClient.exe) または独自のクライアントを使用してサービスをテストし、潜在的なエラーを見つけて修正できます。</span><span class="sxs-lookup"><span data-stu-id="837b7-111">You can then test the service using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="837b7-112">WCF のテスト用クライアント (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="837b7-112">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="837b7-113"> のテスト用クライアント (WcfTestClient.exe) は GUI ツールです。このツールを使用すると、任意の型のパラメーターを入力し、その入力をサービスに送信して、サービスから返される応答を表示できます。</span><span class="sxs-lookup"><span data-stu-id="837b7-113"> Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="837b7-114">このツールを [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホストと組み合わせて使用すると、シームレスにサービスをテストできるようになります。</span><span class="sxs-lookup"><span data-stu-id="837b7-114">It provides a seamless service testing experience when combined with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host.</span></span>  
  
 [<span data-ttu-id="837b7-115">XML からのデータ型クラスの生成</span><span class="sxs-lookup"><span data-stu-id="837b7-115">Generating Data Type Classes from XML</span></span>](../../../docs/framework/wcf/generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="837b7-116">クリップボードに格納されている XML データは、コード ページに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="837b7-116">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="837b7-117">データで定義されているクラスは、コード型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="837b7-117">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="837b7-118">管理特権を必要としないツールの使用</span><span class="sxs-lookup"><span data-stu-id="837b7-118">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="837b7-119">管理特権のないユーザーが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを開発できるようにするために、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のインストール時には、名前空間 "http://+:8731/Design_Time_Addresses" に対してアクセス制御リスト (ACL: Access Control List) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="837b7-119">To enable users without administrator privilege to develop [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="837b7-120">この ACL は (UI) に設定され、コンピューターにログオンしているすべての対話ユーザーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="837b7-120">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="837b7-121">管理者は、この ACL にユーザーを追加または削除したり、追加のポートを開いたりできます。この ACL によって、既定の構成で、WCF テンプレートまたは WF テンプレートでデータを送受信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="837b7-121">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="837b7-122">また、ユーザーは、管理特権が付与されていなくても、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの自動ホスト (wcfSvcHost.exe) を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="837b7-122">It also enables users to use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="837b7-123">システム特権のある管理者アカウントで [!INCLUDE[wv](../../../includes/wv-md.md)] の Netsh.exe ツールを使用すると、アクセスを変更できます。</span><span class="sxs-lookup"><span data-stu-id="837b7-123">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="837b7-124">Netsh.exe の使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="837b7-124">The following is an example of using Netsh.exe.</span></span>  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="837b7-125">Netsh.exe を参照してください[Netsh.exe ツールとコマンド ライン スイッチを使用する方法](http://go.microsoft.com/fwlink/?LinkId=97877)です。</span><span class="sxs-lookup"><span data-stu-id="837b7-125"> Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](http://go.microsoft.com/fwlink/?LinkId=97877).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="837b7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="837b7-126">See Also</span></span>  
 [<span data-ttu-id="837b7-127">WCF Visual Studio テンプレート</span><span class="sxs-lookup"><span data-stu-id="837b7-127">WCF Visual Studio Templates</span></span>](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [<span data-ttu-id="837b7-128">WCF サービス ホスト (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="837b7-128">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [<span data-ttu-id="837b7-129">WCF のテスト用クライアント (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="837b7-129">WCF Test Client (WcfTestClient.exe)</span></span>](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
