---
title: "ICorDebugFrame::GetCode メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a99b652a439a284033f3e7a9ecc46b3599fae00b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="4d67f-102">ICorDebugFrame::GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="4d67f-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="4d67f-103">このスタック フレームに関連付けられているコードへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d67f-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d67f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4d67f-104">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d67f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4d67f-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="4d67f-106">[out]このフレームに関連付けられているコードを表す ICorDebugCode オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4d67f-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d67f-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="4d67f-107">Requirements</span></span>  
 <span data-ttu-id="4d67f-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4d67f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d67f-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d67f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d67f-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d67f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d67f-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d67f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
