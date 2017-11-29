---
title: "ICorDebugModule::IsInMemory メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.IsInMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58f7964faee19f85c83d1b9b1c3e176354ae9588
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="c13b1-102">ICorDebugModule::IsInMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="c13b1-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="c13b1-103">このモジュールは、メモリ内にのみ存在するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c13b1-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c13b1-104">構文</span><span class="sxs-lookup"><span data-stu-id="c13b1-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c13b1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c13b1-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="c13b1-106">[out]`true`メモリ内でのみこのモジュールが存在する場合は、それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="c13b1-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c13b1-107">コメント</span><span class="sxs-lookup"><span data-stu-id="c13b1-107">Remarks</span></span>  
 <span data-ttu-id="c13b1-108">共通言語ランタイム (CLR) は、生のバイト ストリームからのモジュールの読み込みをサポートします。</span><span class="sxs-lookup"><span data-stu-id="c13b1-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="c13b1-109">このようなモジュールが呼び出されます*インメモリ モジュール*ディスク上に存在しないとします。</span><span class="sxs-lookup"><span data-stu-id="c13b1-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c13b1-110">要件</span><span class="sxs-lookup"><span data-stu-id="c13b1-110">Requirements</span></span>  
 <span data-ttu-id="c13b1-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c13b1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c13b1-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c13b1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c13b1-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c13b1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c13b1-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c13b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c13b1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c13b1-115">See Also</span></span>  
    
 
