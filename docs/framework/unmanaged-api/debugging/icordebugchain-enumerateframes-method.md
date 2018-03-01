---
title: "ICorDebugChain::EnumerateFrames メソッド"
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
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9df99c239568948c04f61ca4ec5e2b9207930f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="3d2d3-102">ICorDebugChain::EnumerateFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="3d2d3-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="3d2d3-103">最新のフレームを使用して開始する、チェーン内のすべてのマネージ スタック フレームを含む列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="3d2d3-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d2d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d2d3-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d2d3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d2d3-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="3d2d3-106">[out]スタック フレームの列挙子である ICorDebugFrameEnum オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3d2d3-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d2d3-107">コメント</span><span class="sxs-lookup"><span data-stu-id="3d2d3-107">Remarks</span></span>  
 <span data-ttu-id="3d2d3-108">チェーンは、スレッドの物理呼び出し履歴を表します。</span><span class="sxs-lookup"><span data-stu-id="3d2d3-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="3d2d3-109">`EnumerateFrames`メソッドは、管理対象のチェーンでのみ呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d2d3-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="3d2d3-110">デバッグ API では、アンマネージのチェーンに含まれているフレームを取得するメソッドが提供されません。</span><span class="sxs-lookup"><span data-stu-id="3d2d3-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="3d2d3-111">デバッガーは、その他の方法を使用して、この情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d2d3-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d2d3-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="3d2d3-112">Requirements</span></span>  
 <span data-ttu-id="3d2d3-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d2d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d2d3-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d2d3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d2d3-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d2d3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d2d3-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d2d3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
