---
title: CorExitProcess 関数
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3e7f3208d7ac84645fa4c7ad7e0b71f6a0d3d3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429330"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="6ac61-102">CorExitProcess 関数</span><span class="sxs-lookup"><span data-stu-id="6ac61-102">CorExitProcess Function</span></span>
<span data-ttu-id="6ac61-103">現在のアンマネージ プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="6ac61-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="6ac61-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="6ac61-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="6ac61-105">使用して、 [iclrmetahost::exitprocess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="6ac61-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ac61-106">構文</span><span class="sxs-lookup"><span data-stu-id="6ac61-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ac61-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6ac61-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="6ac61-108">プロセス終了コードを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="6ac61-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ac61-109">コメント</span><span class="sxs-lookup"><span data-stu-id="6ac61-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ac61-110">以降で、 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]、`CorExitProcess`すべて開始のランタイム プロセスでは、従来の Api がバインドされただけでなく、ランタイムが終了します。</span><span class="sxs-lookup"><span data-stu-id="6ac61-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ac61-111">要件</span><span class="sxs-lookup"><span data-stu-id="6ac61-111">Requirements</span></span>  
 <span data-ttu-id="6ac61-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ac61-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ac61-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ac61-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ac61-114">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ac61-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ac61-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ac61-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac61-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ac61-116">See Also</span></span>  
 <span data-ttu-id="6ac61-117">
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span><span class="sxs-lookup"><span data-stu-id="6ac61-117">[Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span></span>
