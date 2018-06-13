---
title: ICorDebugFrame::GetCaller メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2452f4be0acde300676bf56011416e0a9ef16464
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411717"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="cb63e-102">ICorDebugFrame::GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="cb63e-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="cb63e-103">現在のこのフレームを呼び出したチェーン内 ICorDebugFrame オブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="cb63e-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb63e-104">構文</span><span class="sxs-lookup"><span data-stu-id="cb63e-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb63e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cb63e-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="cb63e-106">[out]アドレスへのポインター、`ICorDebugFrame`を呼び出し元のフレームを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="cb63e-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="cb63e-107">この値は、呼び出されたフレームが現在のチェーン内の最も外側のフレームが場合は null です。</span><span class="sxs-lookup"><span data-stu-id="cb63e-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb63e-108">要件</span><span class="sxs-lookup"><span data-stu-id="cb63e-108">Requirements</span></span>  
 <span data-ttu-id="cb63e-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb63e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb63e-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb63e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb63e-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb63e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb63e-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb63e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
