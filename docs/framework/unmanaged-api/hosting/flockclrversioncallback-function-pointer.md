---
title: "FLockClrVersionCallback 関数ポインター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FLockClrVersionCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: FLockClrVersionCallback
helpviewer_keywords: FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca1b97c509ea8ed2c43c30cab278048aeb4170a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="d6f9f-102">FLockClrVersionCallback 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="d6f9f-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="d6f9f-103">初期化を示すために、共通言語ランタイム (CLR) 呼び出しの開始または完了がいる関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d6f9f-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="d6f9f-104">この関数ポインターが削除されて、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d6f9f-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6f9f-105">構文</span><span class="sxs-lookup"><span data-stu-id="d6f9f-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="d6f9f-106">コメント</span><span class="sxs-lookup"><span data-stu-id="d6f9f-106">Remarks</span></span>  
 <span data-ttu-id="d6f9f-107">この関数は、ホストによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="d6f9f-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6f9f-108">要件</span><span class="sxs-lookup"><span data-stu-id="d6f9f-108">Requirements</span></span>  
 <span data-ttu-id="d6f9f-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6f9f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6f9f-110">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6f9f-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6f9f-111">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="d6f9f-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="d6f9f-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6f9f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6f9f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6f9f-113">See Also</span></span>  
 [<span data-ttu-id="d6f9f-114">LockClrVersion 関数</span><span class="sxs-lookup"><span data-stu-id="d6f9f-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 [<span data-ttu-id="d6f9f-115">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="d6f9f-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
