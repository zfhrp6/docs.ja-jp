---
title: Identity and Access Tool for Visual Studio 2012
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a009f37e1f16646df10e693a10827990b073c65c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a><span data-ttu-id="3c2b1-102">Identity and Access Tool for Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="3c2b1-102">Identity and Access Tool for Visual Studio 2012</span></span>
<span data-ttu-id="3c2b1-103">このトピックでは、新しい Identity and Access Tool for Visual Studio 11 について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-103">This topic describes the new Identity and Access Tool for Visual Studio 11.</span></span> <span data-ttu-id="3c2b1-104">このツールは [http://go.microsoft.com/fwlink/?LinkID=245849](http://go.microsoft.com/fwlink/?LinkID=245849) からダウンロードできます。また、拡張機能マネージャーで直接 "ID" を検索して、Visual Studio 11 から直接ダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-104">You can download this tool from the following URL: [http://go.microsoft.com/fwlink/?LinkID=245849](http://go.microsoft.com/fwlink/?LinkID=245849) or directly from within Visual Studio 11 by searching for "identity" directly in the Extensions Manager.</span></span>  
  
 <span data-ttu-id="3c2b1-105">Identity and Access Tool for Visual Studio 11 の特長を次に示します。これにより、開発時の操作性が大幅に簡素化されます。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-105">The Identity and Access Tool for Visual Studio 11 delivers a dramatically simplified development-time experience with the following highlights:</span></span>  
  
-   <span data-ttu-id="3c2b1-106">新しいツールを使用すると、Web アプリケーション プロジェクトの種類およびターゲット IIS Express を使用して開発できます。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-106">Using the new tool, you can develop using web applications project types and target IIS express.</span></span>  
  
-   <span data-ttu-id="3c2b1-107">ブランケット保護のみの認証とは異なり、新しいツールによって、ローカルのホーム レルム探索ページ/コントローラー (または、アプリケーション内で認証によって実行されるその他のエンドポイント処理) を指定できます。WIF は要求の構成を変更して、認証されていないすべての要求が、STS ではなくその場所にリダイレクトされるようにします。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-107">Unlike with the blanket protection-only authentication, with the new tool, you can specify your local home realm discovery page/controller (or any other endpoint handling the authentication experience within your application) and WIF will configure all unauthenticated requests to go there, instead of redirecting them to the STS.</span></span>  
  
-   <span data-ttu-id="3c2b1-108">ツールには、テスト セキュリティ トークン サービス (STS) が含まれています。この STS は、デバッグ セッションの起動時にローカル コンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-108">The tool includes a test Security Token Service (STS) which runs on your local machine when you launch a debug session.</span></span> <span data-ttu-id="3c2b1-109">したがって、アプリケーションのテストに必要なクレームを取得する目的で、カスタム STS プロジェクトを作成して調整する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-109">Therefore, you no longer need to create custom STS projects and tweak them in order to get the claims you need to test your applications.</span></span> <span data-ttu-id="3c2b1-110">クレームの種類と値は完全にカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-110">The claim types and values are fully customizable.</span></span>  
  
-   <span data-ttu-id="3c2b1-111">ツールの UI を使用して共通の設定を直接変更できます。web.config を編集する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-111">You can modify common settings directly via the tool’s UI, without the need to edit web.config.</span></span>  
  
-   <span data-ttu-id="3c2b1-112">Active Directory フェデレーション サービス (AD FS) 2.0 (または、他の WS-Federation プロバイダー) を使用して、1 つの画面でフェデレーションを確立できます。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-112">You can establish federation with Active Directory Federation Services (AD FS) 2.0 (or other WS-Federation providers) in a single screen.</span></span>  
  
-   <span data-ttu-id="3c2b1-113">ツールでは Microsoft Azure のアクセス制御サービス (ACS) の機能を使用できます。この機能には、使用するすべての ID プロバイダー (Facebook、Google、Live ID、Yahoo! などの OpenID プロバイダー、および WS-Federation プロバイダー) のチェック ボックスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-113">The tool leverages Windows Azure Access Control Service (ACS) capabilities with a simple list of checkboxes for all the identity providers that you want to use: Facebook, Google, Live ID, Yahoo!, any OpenID provider, and any WS-Federation provider.</span></span> <span data-ttu-id="3c2b1-114">ID プロバイダーのチェック ボックスをオンにして、[OK] をクリックし、F5 キーを押すと、アプリケーションと ACS の両方が自動的に構成され、テスト アプリケーションが ACS 対応になります。</span><span class="sxs-lookup"><span data-stu-id="3c2b1-114">Select your identity providers, click OK, then F5, and both your application and ACS will be automatically configured and your test application will be ACS-aware.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c2b1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c2b1-115">See Also</span></span>  
 [<span data-ttu-id="3c2b1-116">WIF の機能</span><span class="sxs-lookup"><span data-stu-id="3c2b1-116">WIF Features</span></span>](../../../docs/framework/security/wif-features.md)
