---
title: "アセンブリ バインディング リダイレクトのセキュリティ アクセス許可"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1bd25dd0444c428e000371abe494e62b258eaa63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="d7ba1-102">アセンブリ バインディング リダイレクトのセキュリティ アクセス許可</span><span class="sxs-lookup"><span data-stu-id="d7ba1-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="d7ba1-103">アプリケーション構成ファイルで明示的にアセンブリ バインディングをリダイレクトするには、セキュリティ アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="d7ba1-104">これは、.NET Framework アセンブリおよびサードパーティ製アセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="d7ba1-105">許可を設定して、<xref:System.Security.Permissions.SecurityPermissionFlag>フラグを<xref:System.Security.Permissions.SecurityPermission>です。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="d7ba1-106">マネージ アセンブリは、既定ではアクセス許可を持っていません。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="d7ba1-107">セキュリティ アクセス許可は、信頼済みゾーン (ローカル コンピューター) とイントラネット ゾーンで実行されているアプリケーションに与えられます。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="d7ba1-108">インターネット ゾーンで実行されているアプリケーションが禁止アセンブリ バインド リダイレクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="d7ba1-109">コンポーネントの発行者によって制御されるパブリッシャー ポリシー ファイル、または管理者によって制御されるコンピューターの構成ファイルでアセンブリのリダイレクトを実行する場合は、アクセス許可は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="d7ba1-110">ただし、アクセス許可は、アプリケーションを使用して発行者ポリシーを明示的に無視する必要が、 [ \<publisherPolicy 適用 ="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)アプリケーション構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="d7ba1-111">次の表は、既定のセキュリティ設定、**すること**フラグ。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="d7ba1-112">ゾーン</span><span class="sxs-lookup"><span data-stu-id="d7ba1-112">Zone</span></span>|<span data-ttu-id="d7ba1-113">設定することフラグ</span><span class="sxs-lookup"><span data-stu-id="d7ba1-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="d7ba1-114">信頼済みゾーン (ローカル コンピューター)</span><span class="sxs-lookup"><span data-stu-id="d7ba1-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="d7ba1-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="d7ba1-115">**ON**</span></span>|  
|<span data-ttu-id="d7ba1-116">イントラネット ゾーン</span><span class="sxs-lookup"><span data-stu-id="d7ba1-116">Intranet Zone</span></span>|<span data-ttu-id="d7ba1-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="d7ba1-117">**ON**</span></span>|  
|<span data-ttu-id="d7ba1-118">インターネット ゾーン</span><span class="sxs-lookup"><span data-stu-id="d7ba1-118">Internet Zone</span></span>|<span data-ttu-id="d7ba1-119">**オフ**</span><span class="sxs-lookup"><span data-stu-id="d7ba1-119">**OFF**</span></span>|  
|<span data-ttu-id="d7ba1-120">信頼されていないゾーン</span><span class="sxs-lookup"><span data-stu-id="d7ba1-120">Untrusted zones</span></span>|<span data-ttu-id="d7ba1-121">**オフ**</span><span class="sxs-lookup"><span data-stu-id="d7ba1-121">**OFF**</span></span>|  
  
 <span data-ttu-id="d7ba1-122">管理者は、これらのセキュリティ設定をサポートしたり、特定のコンピューターで特定のシナリオの制限を変更できます。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="d7ba1-123">変更するためのツールがない、**すること**フラグです。 既定値の設定、管理者はユーザーのコンピューターに Security.config ファイルを編集してする必要があります手動でします。</span><span class="sxs-lookup"><span data-stu-id="d7ba1-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ba1-124">参照</span><span class="sxs-lookup"><span data-stu-id="d7ba1-124">See Also</span></span>  
 [<span data-ttu-id="d7ba1-125">発行者ポリシー ファイルとサイド バイ サイド実行</span><span class="sxs-lookup"><span data-stu-id="d7ba1-125">Publisher Policy Files and Side-by-Side Execution</span></span>](http://msdn.microsoft.com/en-us/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="d7ba1-126">方法: 自動バインディング リダイレクトを有効/無効にする</span><span class="sxs-lookup"><span data-stu-id="d7ba1-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="d7ba1-127">side-by-side 実行</span><span class="sxs-lookup"><span data-stu-id="d7ba1-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
