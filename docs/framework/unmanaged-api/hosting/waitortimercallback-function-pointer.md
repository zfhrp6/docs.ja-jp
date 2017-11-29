---
title: "WAITORTIMERCALLBACK 関数ポインター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: WAITORTIMERCALLBACK
api_location: mscoree.dll
api_type: COM
f1_keywords: WAITORTIMERCALLBACK
helpviewer_keywords: WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 873d2ff489085ec2a0c37be2feeb3e15f61c9227
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="39bd1-102">WAITORTIMERCALLBACK 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="39bd1-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="39bd1-103">待機を処理するホストに通知する関数を指します (<xref:System.Threading.WaitHandle>) がされたシグナル状態またはタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="39bd1-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="39bd1-104">この関数ポインターが削除されて、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="39bd1-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39bd1-105">構文</span><span class="sxs-lookup"><span data-stu-id="39bd1-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39bd1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="39bd1-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="39bd1-107">[in]ホストによって定義された情報を格納しているオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39bd1-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="39bd1-108">[in]`true`待機ハンドルがタイムアウトした場合または`false`がタイムアウトした場合。</span><span class="sxs-lookup"><span data-stu-id="39bd1-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39bd1-109">コメント</span><span class="sxs-lookup"><span data-stu-id="39bd1-109">Remarks</span></span>  
 <span data-ttu-id="39bd1-110">関数`WAITORTIMERCALLBACK`ポイントはコールバック関数であり、ホスト アプリケーションの作成者によって実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39bd1-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39bd1-111">要件</span><span class="sxs-lookup"><span data-stu-id="39bd1-111">Requirements</span></span>  
 <span data-ttu-id="39bd1-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="39bd1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39bd1-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="39bd1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39bd1-114">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="39bd1-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="39bd1-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39bd1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39bd1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="39bd1-116">See Also</span></span>  
 [<span data-ttu-id="39bd1-117">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="39bd1-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
