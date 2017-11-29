---
title: "LPTHREAD_START_ROUTINE 関数ポインター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LPTHREAD_START_ROUTINE
api_location: mscoree.dll
api_type: COM
f1_keywords: LPTHREAD_START_ROUTINE
helpviewer_keywords: LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f29e4e52f9629073d676903e3f828a84023065bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="fd0de-102">LPTHREAD_START_ROUTINE 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="fd0de-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="fd0de-103">スレッドの実行を開始したことをホストに通知する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="fd0de-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="fd0de-104">この関数ポインターが削除されて、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="fd0de-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd0de-105">構文</span><span class="sxs-lookup"><span data-stu-id="fd0de-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd0de-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd0de-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="fd0de-107">[in]実行が開始された、コードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fd0de-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd0de-108">コメント</span><span class="sxs-lookup"><span data-stu-id="fd0de-108">Remarks</span></span>  
 <span data-ttu-id="fd0de-109">関数`LPTHREAD_START_ROUTINE`ポイントはコールバック関数であり、ホスト アプリケーションの作成者によって実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd0de-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd0de-110">要件</span><span class="sxs-lookup"><span data-stu-id="fd0de-110">Requirements</span></span>  
 <span data-ttu-id="fd0de-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fd0de-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd0de-112">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd0de-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd0de-113">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="fd0de-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="fd0de-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd0de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd0de-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd0de-115">See Also</span></span>  
 [<span data-ttu-id="fd0de-116">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="fd0de-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
