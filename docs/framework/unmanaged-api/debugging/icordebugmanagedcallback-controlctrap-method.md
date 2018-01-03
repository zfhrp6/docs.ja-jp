---
title: "ICorDebugManagedCallback::ControlCTrap メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ControlCTrap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5de52b810efeaf7b5c103dcd39a37a37ab3272
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="bde05-102">ICorDebugManagedCallback::ControlCTrap メソッド</span><span class="sxs-lookup"><span data-stu-id="bde05-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="bde05-103">CTRL + C が、デバッグ対象プロセスにトラップされることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="bde05-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bde05-104">構文</span><span class="sxs-lookup"><span data-stu-id="bde05-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bde05-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bde05-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="bde05-106">[in]CTRL + C をトラップするプロセスを表す ICorDebugProcess オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bde05-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bde05-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="bde05-107">Return Value</span></span>  
  
|<span data-ttu-id="bde05-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bde05-108">HRESULT</span></span>|<span data-ttu-id="bde05-109">説明</span><span class="sxs-lookup"><span data-stu-id="bde05-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bde05-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bde05-110">S_OK</span></span>|<span data-ttu-id="bde05-111">デバッガーでは、ctrl キーを押しながら C トラップを処理します。</span><span class="sxs-lookup"><span data-stu-id="bde05-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="bde05-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bde05-112">S_FALSE</span></span>|<span data-ttu-id="bde05-113">デバッガーでは、ctrl キーを押しながら C トラップは処理されません。</span><span class="sxs-lookup"><span data-stu-id="bde05-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bde05-114">コメント</span><span class="sxs-lookup"><span data-stu-id="bde05-114">Remarks</span></span>  
 <span data-ttu-id="bde05-115">プロセス内のすべてのアプリケーション ドメインがこのコールバックを停止します。</span><span class="sxs-lookup"><span data-stu-id="bde05-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bde05-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="bde05-116">Requirements</span></span>  
 <span data-ttu-id="bde05-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bde05-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bde05-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bde05-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bde05-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bde05-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bde05-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bde05-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bde05-121">参照</span><span class="sxs-lookup"><span data-stu-id="bde05-121">See Also</span></span>  
 [<span data-ttu-id="bde05-122">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bde05-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
