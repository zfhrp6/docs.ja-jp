---
title: "ICorDebugProcess6::GetCode メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f532c52ac487915b76d624e62886a93db6d1eae4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="b35de-102">ICorDebugProcess6::GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="b35de-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="b35de-103">特定のコード アドレスで、マネージ コードに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="b35de-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b35de-104">構文</span><span class="sxs-lookup"><span data-stu-id="b35de-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b35de-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b35de-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="b35de-106">[in]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)マネージ コードのセグメントの開始アドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="b35de-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="b35de-107">[out]マネージ コードのセグメントを表す"ICorDebugCode"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b35de-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b35de-108">コメント</span><span class="sxs-lookup"><span data-stu-id="b35de-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b35de-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b35de-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b35de-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="b35de-110">Requirements</span></span>  
 <span data-ttu-id="b35de-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b35de-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b35de-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b35de-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b35de-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b35de-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b35de-114">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b35de-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b35de-115">参照</span><span class="sxs-lookup"><span data-stu-id="b35de-115">See Also</span></span>  
 [<span data-ttu-id="b35de-116">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b35de-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="b35de-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b35de-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
