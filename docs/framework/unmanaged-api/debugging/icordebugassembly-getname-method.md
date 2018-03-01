---
title: "ICorDebugAssembly::GetName メソッド"
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
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf2b84a6ab7cc1745fbf7330e66f94ea04635892
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="47b76-102">ICorDebugAssembly::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="47b76-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="47b76-103">アセンブリの名前を取得この`ICorDebugAssembly`インスタンスが表すです。</span><span class="sxs-lookup"><span data-stu-id="47b76-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47b76-104">構文</span><span class="sxs-lookup"><span data-stu-id="47b76-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47b76-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47b76-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="47b76-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="47b76-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="47b76-107">[out]名前の実際の長さを指定する整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="47b76-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="47b76-108">[out]名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="47b76-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47b76-109">コメント</span><span class="sxs-lookup"><span data-stu-id="47b76-109">Remarks</span></span>  
 <span data-ttu-id="47b76-110">`GetName`メソッド、アセンブリの完全パスとファイル名を返します。</span><span class="sxs-lookup"><span data-stu-id="47b76-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47b76-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="47b76-111">Requirements</span></span>  
 <span data-ttu-id="47b76-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="47b76-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47b76-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47b76-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47b76-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47b76-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47b76-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47b76-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
