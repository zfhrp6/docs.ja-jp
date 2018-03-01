---
title: "HOST_TYPE 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8c910dd06109a8a69f29517812737d4b4dcef21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="38ec9-102">HOST_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="38ec9-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="38ec9-103">アプリケーションを起動するホストの種類を指定する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="38ec9-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38ec9-104">構文</span><span class="sxs-lookup"><span data-stu-id="38ec9-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="38ec9-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="38ec9-105">Members</span></span>  
  
|<span data-ttu-id="38ec9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="38ec9-106">Member</span></span>|<span data-ttu-id="38ec9-107">説明</span><span class="sxs-lookup"><span data-stu-id="38ec9-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="38ec9-108">AppLaunch.exe からアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="38ec9-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="38ec9-109">部分的に信頼されたアプリケーションには、この値を使用します。</span><span class="sxs-lookup"><span data-stu-id="38ec9-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="38ec9-110">アプリケーションを直接起動します。</span><span class="sxs-lookup"><span data-stu-id="38ec9-110">Launch the application directly.</span></span> <span data-ttu-id="38ec9-111">独自の .exe ファイルからアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="38ec9-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="38ec9-112">完全に信頼されたアプリケーションには、この値を使用します。</span><span class="sxs-lookup"><span data-stu-id="38ec9-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="38ec9-113">HOST_TYPE_APPLAUNCH と同じです。</span><span class="sxs-lookup"><span data-stu-id="38ec9-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38ec9-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="38ec9-114">Requirements</span></span>  
 <span data-ttu-id="38ec9-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="38ec9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38ec9-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38ec9-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38ec9-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38ec9-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38ec9-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38ec9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ec9-119">参照</span><span class="sxs-lookup"><span data-stu-id="38ec9-119">See Also</span></span>  
 [<span data-ttu-id="38ec9-120">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="38ec9-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
