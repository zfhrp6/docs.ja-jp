---
title: "HOST_TYPE 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: HOST_TYPE
api_location: mscoree.dll
api_type: COM
f1_keywords: HOST_TYPE
helpviewer_keywords: HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e191293ff7bde6b1be2210af4e7830fec0d7290d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="hosttype-enumeration"></a><span data-ttu-id="4130f-102">HOST_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="4130f-102">HOST_TYPE Enumeration</span></span>
<span data-ttu-id="4130f-103">アプリケーションを起動するホストの種類を指定する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4130f-103">Contains values that specify the type of host that is launching an application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4130f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4130f-104">Syntax</span></span>  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="4130f-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="4130f-105">Members</span></span>  
  
|<span data-ttu-id="4130f-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4130f-106">Member</span></span>|<span data-ttu-id="4130f-107">説明</span><span class="sxs-lookup"><span data-stu-id="4130f-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|<span data-ttu-id="4130f-108">AppLaunch.exe からアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="4130f-108">Launch the application from AppLaunch.exe.</span></span><br /><br /> <span data-ttu-id="4130f-109">部分的に信頼されたアプリケーションには、この値を使用します。</span><span class="sxs-lookup"><span data-stu-id="4130f-109">Use this value for partially-trusted applications.</span></span>|  
|`HOST_TYPE_CORFLAG`|<span data-ttu-id="4130f-110">アプリケーションを直接起動します。</span><span class="sxs-lookup"><span data-stu-id="4130f-110">Launch the application directly.</span></span> <span data-ttu-id="4130f-111">独自の .exe ファイルからアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="4130f-111">That is, launch the application from its own .exe file.</span></span><br /><br /> <span data-ttu-id="4130f-112">完全に信頼されたアプリケーションには、この値を使用します。</span><span class="sxs-lookup"><span data-stu-id="4130f-112">Use this value for fully-trusted applications.</span></span>|  
|`HOST_TYPE_DEFAULT`|<span data-ttu-id="4130f-113">HOST_TYPE_APPLAUNCH と同じです。</span><span class="sxs-lookup"><span data-stu-id="4130f-113">Same as HOST_TYPE_APPLAUNCH.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4130f-114">要件</span><span class="sxs-lookup"><span data-stu-id="4130f-114">Requirements</span></span>  
 <span data-ttu-id="4130f-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4130f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4130f-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4130f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4130f-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4130f-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4130f-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4130f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4130f-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4130f-119">See Also</span></span>  
 [<span data-ttu-id="4130f-120">ホスティングの列挙体</span><span class="sxs-lookup"><span data-stu-id="4130f-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
