---
title: "ICorDebugEval::IsActive メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a695bfc4b7575a1a56dfba3dca515321a07239cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="d7dce-102">ICorDebugEval::IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="d7dce-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="d7dce-103">この ICorDebugEval オブジェクトが現在実行されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d7dce-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7dce-104">構文</span><span class="sxs-lookup"><span data-stu-id="d7dce-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7dce-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d7dce-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="d7dce-106">[out]この評価がアクティブかどうかを示す値を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="d7dce-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7dce-107">要件</span><span class="sxs-lookup"><span data-stu-id="d7dce-107">Requirements</span></span>  
 <span data-ttu-id="d7dce-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d7dce-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7dce-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7dce-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7dce-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7dce-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7dce-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7dce-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
