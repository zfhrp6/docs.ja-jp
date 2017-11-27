---
title: "ICorDebugHandleValue::GetHandleType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue.GetHandleType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 05a146eb3885d84a144cbbfe23763f5ff3981898
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="c59de-102">ICorDebugHandleValue::GetHandleType メソッド</span><span class="sxs-lookup"><span data-stu-id="c59de-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="c59de-103">ICorDebugHandleValue オブジェクトによって参照されているハンドルの種類を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c59de-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c59de-104">構文</span><span class="sxs-lookup"><span data-stu-id="c59de-104">Syntax</span></span>  
  
```  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c59de-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c59de-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="c59de-106">[out]このハンドルの種類を示す CorDebugHandleType 列挙型の値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c59de-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c59de-107">要件</span><span class="sxs-lookup"><span data-stu-id="c59de-107">Requirements</span></span>  
 <span data-ttu-id="c59de-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c59de-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c59de-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c59de-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c59de-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c59de-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c59de-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c59de-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
