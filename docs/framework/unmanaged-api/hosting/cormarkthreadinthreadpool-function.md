---
title: CorMarkThreadInThreadPool 関数
ms.date: 03/30/2017
api_name:
- CorMarkThreadInThreadPool
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorMarkThreadInThreadPool
helpviewer_keywords:
- CorMarkThreadInThreadPool function [.NET Framework hosting]
ms.assetid: 3f958d41-e82e-4ec3-ae6f-16c7b3b31e3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b395bc4d199738b309be74868243b61f924878c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431234"
---
# <a name="cormarkthreadinthreadpool-function"></a><span data-ttu-id="6915a-102">CorMarkThreadInThreadPool 関数</span><span class="sxs-lookup"><span data-stu-id="6915a-102">CorMarkThreadInThreadPool Function</span></span>
<span data-ttu-id="6915a-103">現在実行されているスレッド プールのスレッドに、マネージ コードの実行のマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="6915a-103">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="6915a-104">.NET Framework Version 2.0 以降では、この関数に効力はありません。</span><span class="sxs-lookup"><span data-stu-id="6915a-104">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="6915a-105">必要でないと、コードから削除することができます。この関数は非推奨、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6915a-105">It is not required, and can be removed from your code.This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6915a-106">構文</span><span class="sxs-lookup"><span data-stu-id="6915a-106">Syntax</span></span>  
  
```  
void CorMarkThreadInThreadPool ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="6915a-107">要件</span><span class="sxs-lookup"><span data-stu-id="6915a-107">Requirements</span></span>  
 <span data-ttu-id="6915a-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6915a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6915a-109">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6915a-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6915a-110">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6915a-110">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6915a-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6915a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6915a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="6915a-112">See Also</span></span>  
 <span data-ttu-id="6915a-113">
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span><span class="sxs-lookup"><span data-stu-id="6915a-113">[Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span></span>
