---
title: EInitializeNewDomainFlags 列挙体
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0175ab1d06a8166a5bbfd0c42018085a801740f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431450"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="63800-102">EInitializeNewDomainFlags 列挙体</span><span class="sxs-lookup"><span data-stu-id="63800-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="63800-103">ホストがランタイムにアプリケーション ドメインの初期化に関する情報を提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="63800-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63800-104">構文</span><span class="sxs-lookup"><span data-stu-id="63800-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="63800-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="63800-105">Members</span></span>  
  
|<span data-ttu-id="63800-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="63800-106">Member</span></span>|<span data-ttu-id="63800-107">説明</span><span class="sxs-lookup"><span data-stu-id="63800-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="63800-108">フラグがありません。</span><span class="sxs-lookup"><span data-stu-id="63800-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="63800-109">共通言語ランタイム (CLR) の通知、こと、ホスト変更できなくなりますで、アプリケーション ドメインのセキュリティの状態を<xref:System.AppDomainManager.InitializeNewDomain%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="63800-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63800-110">コメント</span><span class="sxs-lookup"><span data-stu-id="63800-110">Remarks</span></span>  
 <span data-ttu-id="63800-111">[Iclrdomainmanager::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)メソッドが型のパラメーターを受け取る`EInitializeNewDomainFlags`です。</span><span class="sxs-lookup"><span data-stu-id="63800-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63800-112">要件</span><span class="sxs-lookup"><span data-stu-id="63800-112">Requirements</span></span>  
 <span data-ttu-id="63800-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="63800-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63800-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63800-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63800-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63800-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63800-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63800-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63800-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="63800-117">See Also</span></span>  
 [<span data-ttu-id="63800-118">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="63800-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="63800-119">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="63800-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
