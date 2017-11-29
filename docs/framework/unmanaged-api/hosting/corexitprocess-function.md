---
title: "CorExitProcess 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorExitProcess
helpviewer_keywords: CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75b35631bad5de46d48ed818c6f929f25a5f7e66
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corexitprocess-function"></a><span data-ttu-id="d6ac2-102">CorExitProcess 関数</span><span class="sxs-lookup"><span data-stu-id="d6ac2-102">CorExitProcess Function</span></span>
<span data-ttu-id="d6ac2-103">現在のアンマネージ プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="d6ac2-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="d6ac2-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="d6ac2-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="d6ac2-105">使用して、 [iclrmetahost::exitprocess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="d6ac2-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ac2-106">構文</span><span class="sxs-lookup"><span data-stu-id="d6ac2-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6ac2-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6ac2-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="d6ac2-108">プロセス終了コードを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="d6ac2-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6ac2-109">コメント</span><span class="sxs-lookup"><span data-stu-id="d6ac2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6ac2-110">以降で、 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]、`CorExitProcess`すべて開始のランタイム プロセスでは、従来の Api がバインドされただけでなく、ランタイムが終了します。</span><span class="sxs-lookup"><span data-stu-id="d6ac2-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6ac2-111">要件</span><span class="sxs-lookup"><span data-stu-id="d6ac2-111">Requirements</span></span>  
 <span data-ttu-id="d6ac2-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6ac2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ac2-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6ac2-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6ac2-114">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6ac2-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6ac2-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6ac2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ac2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6ac2-116">See Also</span></span>  
 [<span data-ttu-id="d6ac2-117">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="d6ac2-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
