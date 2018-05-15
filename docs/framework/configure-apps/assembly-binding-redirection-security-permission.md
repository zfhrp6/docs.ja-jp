---
title: アセンブリ バインディング リダイレクトのセキュリティ アクセス許可
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ef9295028aeb7bfcc6df88e9c8bb7f80e2a31368
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="f9381-102">アセンブリ バインディング リダイレクトのセキュリティ アクセス許可</span><span class="sxs-lookup"><span data-stu-id="f9381-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="f9381-103">アプリケーション構成ファイルで明示的にアセンブリ バインディングをリダイレクトするには、セキュリティ アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="f9381-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="f9381-104">これは、.NET Framework アセンブリおよびサードパーティ製アセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f9381-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="f9381-105">許可を設定して、<xref:System.Security.Permissions.SecurityPermissionFlag>フラグを<xref:System.Security.Permissions.SecurityPermission>です。</span><span class="sxs-lookup"><span data-stu-id="f9381-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="f9381-106">マネージ アセンブリは、既定ではアクセス許可を持っていません。</span><span class="sxs-lookup"><span data-stu-id="f9381-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="f9381-107">セキュリティ アクセス許可は、信頼済みゾーン (ローカル コンピューター) とイントラネット ゾーンで実行されているアプリケーションに与えられます。</span><span class="sxs-lookup"><span data-stu-id="f9381-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="f9381-108">インターネット ゾーンで実行されているアプリケーションが禁止アセンブリ バインド リダイレクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="f9381-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="f9381-109">コンポーネントの発行者によって制御されるパブリッシャー ポリシー ファイル、または管理者によって制御されるコンピューターの構成ファイルでアセンブリのリダイレクトを実行する場合は、アクセス許可は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f9381-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="f9381-110">ただし、アクセス許可は、アプリケーションを使用して発行者ポリシーを明示的に無視する必要が、 [ \<publisherPolicy 適用 ="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)アプリケーション構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="f9381-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="f9381-111">次の表は、既定のセキュリティ設定、**すること**フラグ。</span><span class="sxs-lookup"><span data-stu-id="f9381-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="f9381-112">ゾーン</span><span class="sxs-lookup"><span data-stu-id="f9381-112">Zone</span></span>|<span data-ttu-id="f9381-113">設定することフラグ</span><span class="sxs-lookup"><span data-stu-id="f9381-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="f9381-114">信頼済みゾーン (ローカル コンピューター)</span><span class="sxs-lookup"><span data-stu-id="f9381-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="f9381-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="f9381-115">**ON**</span></span>|  
|<span data-ttu-id="f9381-116">イントラネット ゾーン</span><span class="sxs-lookup"><span data-stu-id="f9381-116">Intranet Zone</span></span>|<span data-ttu-id="f9381-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="f9381-117">**ON**</span></span>|  
|<span data-ttu-id="f9381-118">インターネット ゾーン</span><span class="sxs-lookup"><span data-stu-id="f9381-118">Internet Zone</span></span>|<span data-ttu-id="f9381-119">**OFF**</span><span class="sxs-lookup"><span data-stu-id="f9381-119">**OFF**</span></span>|  
|<span data-ttu-id="f9381-120">信頼されていないゾーン</span><span class="sxs-lookup"><span data-stu-id="f9381-120">Untrusted zones</span></span>|<span data-ttu-id="f9381-121">**OFF**</span><span class="sxs-lookup"><span data-stu-id="f9381-121">**OFF**</span></span>|  
  
 <span data-ttu-id="f9381-122">管理者は、これらのセキュリティ設定をサポートしたり、特定のコンピューターで特定のシナリオの制限を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f9381-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="f9381-123">変更するためのツールがない、**すること**フラグです。 既定値の設定、管理者はユーザーのコンピューターに Security.config ファイルを編集してする必要があります手動でします。</span><span class="sxs-lookup"><span data-stu-id="f9381-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9381-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9381-124">See Also</span></span>  
 [<span data-ttu-id="f9381-125">発行者ポリシー ファイルとサイド バイ サイド実行</span><span class="sxs-lookup"><span data-stu-id="f9381-125">Publisher Policy Files and Side-by-Side Execution</span></span>](http://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="f9381-126">方法: 自動バインディング リダイレクトを有効/無効にする</span><span class="sxs-lookup"><span data-stu-id="f9381-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="f9381-127">side-by-side 実行</span><span class="sxs-lookup"><span data-stu-id="f9381-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
