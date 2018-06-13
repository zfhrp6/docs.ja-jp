---
title: ICorDebugEval::NewObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ff378602fc7338263ef49aee6802d2138bab9d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413173"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="6ec4f-102">ICorDebugEval::NewObject メソッド</span><span class="sxs-lookup"><span data-stu-id="6ec4f-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="6ec4f-103">オブジェクトの新しいインスタンスを割り当てるし、指定したコンス トラクター メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6ec4f-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="6ec4f-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="6ec4f-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6ec4f-105">使用して[icordebugeval 2::newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)代わりにします。</span><span class="sxs-lookup"><span data-stu-id="6ec4f-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec4f-106">構文</span><span class="sxs-lookup"><span data-stu-id="6ec4f-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ec4f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6ec4f-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="6ec4f-108">[in]呼び出されるコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="6ec4f-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="6ec4f-109">[in] `ppArgs` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6ec4f-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="6ec4f-110">[in]ICorDebugValue オブジェクトのコンス トラクターに渡される引数を表す配列。</span><span class="sxs-lookup"><span data-stu-id="6ec4f-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ec4f-111">要件</span><span class="sxs-lookup"><span data-stu-id="6ec4f-111">Requirements</span></span>  
 <span data-ttu-id="6ec4f-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ec4f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ec4f-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ec4f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ec4f-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ec4f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ec4f-115">**.NET framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="6ec4f-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec4f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ec4f-116">See Also</span></span>  
 [<span data-ttu-id="6ec4f-117">NewParameterizedObject メソッド</span><span class="sxs-lookup"><span data-stu-id="6ec4f-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
