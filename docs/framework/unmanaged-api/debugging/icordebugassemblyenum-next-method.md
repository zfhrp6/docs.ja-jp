---
title: ICorDebugAssemblyEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b94ae83f2fb5f71abb8cb3a5c96aac9e268fc5db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405289"
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="afb1c-102">ICorDebugAssemblyEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="afb1c-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="afb1c-103">コレクションの現在のカーソル位置からのアセンブリの指定した数を取得します。</span><span class="sxs-lookup"><span data-stu-id="afb1c-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb1c-104">構文</span><span class="sxs-lookup"><span data-stu-id="afb1c-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="afb1c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="afb1c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="afb1c-106">[in]取得するアセンブリの数。</span><span class="sxs-lookup"><span data-stu-id="afb1c-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="afb1c-107">[out]アセンブリを表す ICorDebugAssembly オブジェクトを指し示すそれぞれが、ポインターの配列。</span><span class="sxs-lookup"><span data-stu-id="afb1c-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="afb1c-108">[out]実際に返されるアセンブリの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="afb1c-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="afb1c-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="afb1c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb1c-110">要件</span><span class="sxs-lookup"><span data-stu-id="afb1c-110">Requirements</span></span>  
 <span data-ttu-id="afb1c-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="afb1c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb1c-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afb1c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afb1c-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afb1c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afb1c-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb1c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
