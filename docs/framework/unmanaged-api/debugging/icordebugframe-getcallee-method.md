---
title: ICorDebugFrame::GetCallee メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d62f4f8a34123bcd3f0cbe56f1c1b958bcaa6ef2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413373"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="ab3db-102">ICorDebugFrame::GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="ab3db-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="ab3db-103">このフレームと呼ばれる現在のチェーンで ICorDebugFrame オブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="ab3db-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab3db-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab3db-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab3db-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ab3db-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="ab3db-106">[out]アドレスへのポインター、`ICorDebugFrame`呼び出されたフレームを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ab3db-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="ab3db-107">この値は、呼び出し元のフレームが現在のチェーン内の最も内側のフレームが場合は null です。</span><span class="sxs-lookup"><span data-stu-id="ab3db-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab3db-108">要件</span><span class="sxs-lookup"><span data-stu-id="ab3db-108">Requirements</span></span>  
 <span data-ttu-id="ab3db-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ab3db-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab3db-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab3db-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab3db-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab3db-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab3db-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab3db-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
