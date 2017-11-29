---
title: "ICorDebugStringValue::GetLength メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStringValue.GetLength
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c072e7420e400e6402c8697eefc62c658c590261
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="5a5d3-102">ICorDebugStringValue::GetLength メソッド</span><span class="sxs-lookup"><span data-stu-id="5a5d3-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="5a5d3-103">この ICorDebugStringValue によって参照される文字列の文字数を取得します。</span><span class="sxs-lookup"><span data-stu-id="5a5d3-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a5d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="5a5d3-104">Syntax</span></span>  
  
```  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a5d3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5a5d3-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="5a5d3-106">[out]これによって参照される文字列の長さを指定する値へのポインター`ICorDebugStringValue`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5a5d3-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a5d3-107">要件</span><span class="sxs-lookup"><span data-stu-id="5a5d3-107">Requirements</span></span>  
 <span data-ttu-id="5a5d3-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a5d3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a5d3-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a5d3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a5d3-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a5d3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a5d3-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a5d3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
