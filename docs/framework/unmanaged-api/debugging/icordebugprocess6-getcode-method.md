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
ms.openlocfilehash: c69ce290a486960978ddaf87203328df4f392b48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="9a214-102">ICorDebugProcess6::GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="9a214-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="9a214-103">特定のコード アドレスで、マネージ コードに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="9a214-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a214-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a214-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a214-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a214-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="9a214-106">[in]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)マネージ コードのセグメントの開始アドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="9a214-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="9a214-107">[out]マネージ コードのセグメントを表す"ICorDebugCode"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9a214-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a214-108">コメント</span><span class="sxs-lookup"><span data-stu-id="9a214-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a214-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a214-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a214-110">要件</span><span class="sxs-lookup"><span data-stu-id="9a214-110">Requirements</span></span>  
 <span data-ttu-id="9a214-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9a214-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a214-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a214-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a214-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a214-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a214-114">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a214-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a214-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a214-115">See Also</span></span>  
 [<span data-ttu-id="9a214-116">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a214-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="9a214-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a214-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
