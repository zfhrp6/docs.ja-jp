---
title: "ICorDebugArrayValue::HasBaseIndicies メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.HasBaseIndicies
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1aa7e263c4e6b1460e327869c0c6945cba65328
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="b1916-102">ICorDebugArrayValue::HasBaseIndicies メソッド</span><span class="sxs-lookup"><span data-stu-id="b1916-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="b1916-103">この配列のディメンションに 0 以外の基本のインデックスが設定されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b1916-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1916-104">構文</span><span class="sxs-lookup"><span data-stu-id="b1916-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1916-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b1916-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="b1916-106">[out]ブール値へのポインター`true`場合この 1 つまたは複数のディメンション`ICorDebugArrayValue`オブジェクト ベースのインデックス 0 ではないのです。 それ以外の場合、ブール値は`false`します。</span><span class="sxs-lookup"><span data-stu-id="b1916-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1916-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="b1916-107">Requirements</span></span>  
 <span data-ttu-id="b1916-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b1916-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1916-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1916-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1916-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1916-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1916-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1916-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
