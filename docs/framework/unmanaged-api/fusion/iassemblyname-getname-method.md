---
title: "IAssemblyName::GetName メソッド"
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
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 681df0b4d6b3d7206954264355afb3ef2628243d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="d7f17-102">IAssemblyName::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="d7f17-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="d7f17-103">これによって参照されるアセンブリの単純な暗号化されていない名前を取得[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d7f17-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7f17-104">構文</span><span class="sxs-lookup"><span data-stu-id="d7f17-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7f17-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d7f17-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="d7f17-106">[入力、出力].サイズ`pwzName`ワイド文字、終端の null 文字を含むです。</span><span class="sxs-lookup"><span data-stu-id="d7f17-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="d7f17-107">[out]参照先アセンブリの名前を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="d7f17-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7f17-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="d7f17-108">Requirements</span></span>  
 <span data-ttu-id="d7f17-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d7f17-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7f17-110">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d7f17-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d7f17-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7f17-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f17-112">参照</span><span class="sxs-lookup"><span data-stu-id="d7f17-112">See Also</span></span>  
 [<span data-ttu-id="d7f17-113">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7f17-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
