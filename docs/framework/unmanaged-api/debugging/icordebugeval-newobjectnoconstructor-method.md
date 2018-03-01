---
title: "ICorDebugEval::NewObjectNoConstructor メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ceb35781d4685e3576470da3b99a6666ba233e19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="c766d-102">ICorDebugEval::NewObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="c766d-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="c766d-103">コンス トラクター メソッドを呼び出さずに、指定した型の新しいオブジェクト インスタンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c766d-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="c766d-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="c766d-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c766d-105">使用して[icordebugeval 2::newparameterizedobjectnoconstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)代わりにします。</span><span class="sxs-lookup"><span data-stu-id="c766d-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c766d-106">構文</span><span class="sxs-lookup"><span data-stu-id="c766d-106">Syntax</span></span>  
  
```  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c766d-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c766d-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="c766d-108">[in]インスタンス化されるオブジェクトの型を表す ICorDebugClass オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c766d-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c766d-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="c766d-109">Requirements</span></span>  
 <span data-ttu-id="c766d-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c766d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c766d-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c766d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c766d-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c766d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c766d-113">**.NET framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="c766d-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c766d-114">参照</span><span class="sxs-lookup"><span data-stu-id="c766d-114">See Also</span></span>  
 [<span data-ttu-id="c766d-115">NewParameterizedObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="c766d-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
