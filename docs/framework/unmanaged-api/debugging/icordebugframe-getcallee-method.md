---
title: "ICorDebugFrame::GetCallee メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCallee
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54a26ad7d4818aae81b765ab4e6c0e5be821680e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="90acf-102">ICorDebugFrame::GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="90acf-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="90acf-103">このフレームと呼ばれる現在のチェーンで ICorDebugFrame オブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="90acf-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90acf-104">構文</span><span class="sxs-lookup"><span data-stu-id="90acf-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90acf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="90acf-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="90acf-106">[out]アドレスへのポインター、`ICorDebugFrame`呼び出されたフレームを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="90acf-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="90acf-107">この値は、呼び出し元のフレームが現在のチェーン内の最も内側のフレームが場合は null です。</span><span class="sxs-lookup"><span data-stu-id="90acf-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90acf-108">要件</span><span class="sxs-lookup"><span data-stu-id="90acf-108">Requirements</span></span>  
 <span data-ttu-id="90acf-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="90acf-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90acf-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90acf-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90acf-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90acf-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90acf-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90acf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
