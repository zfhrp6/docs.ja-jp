---
title: "WAITORTIMERCALLBACK 関数ポインター"
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
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f39c023c6911ca0bcc6b62a562785c069d846d15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="4bf40-102">WAITORTIMERCALLBACK 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="4bf40-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="4bf40-103">待機を処理するホストに通知する関数を指します (<xref:System.Threading.WaitHandle>) がされたシグナル状態またはタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4bf40-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="4bf40-104">この関数ポインターが削除されて、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="4bf40-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bf40-105">構文</span><span class="sxs-lookup"><span data-stu-id="4bf40-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bf40-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4bf40-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="4bf40-107">[in]ホストによって定義された情報を格納しているオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4bf40-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="4bf40-108">[in]`true`待機ハンドルがタイムアウトした場合または`false`がタイムアウトした場合。</span><span class="sxs-lookup"><span data-stu-id="4bf40-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bf40-109">コメント</span><span class="sxs-lookup"><span data-stu-id="4bf40-109">Remarks</span></span>  
 <span data-ttu-id="4bf40-110">関数`WAITORTIMERCALLBACK`ポイントはコールバック関数であり、ホスト アプリケーションの作成者によって実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bf40-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bf40-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="4bf40-111">Requirements</span></span>  
 <span data-ttu-id="4bf40-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4bf40-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bf40-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4bf40-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bf40-114">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="4bf40-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="4bf40-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bf40-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf40-116">参照</span><span class="sxs-lookup"><span data-stu-id="4bf40-116">See Also</span></span>  
 [<span data-ttu-id="4bf40-117">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="4bf40-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
