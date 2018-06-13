---
title: IAssemblyName::GetName メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c918de10f86442b10b0d85e6554bb1af0a8928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429612"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="41a8b-102">IAssemblyName::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="41a8b-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="41a8b-103">これによって参照されるアセンブリの単純な暗号化されていない名前を取得[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="41a8b-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41a8b-104">構文</span><span class="sxs-lookup"><span data-stu-id="41a8b-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41a8b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41a8b-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="41a8b-106">[入力、出力].サイズ`pwzName`ワイド文字、終端の null 文字を含むです。</span><span class="sxs-lookup"><span data-stu-id="41a8b-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="41a8b-107">[out]参照先アセンブリの名前を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="41a8b-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41a8b-108">要件</span><span class="sxs-lookup"><span data-stu-id="41a8b-108">Requirements</span></span>  
 <span data-ttu-id="41a8b-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="41a8b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41a8b-110">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="41a8b-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="41a8b-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41a8b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a8b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="41a8b-112">See Also</span></span>  
 [<span data-ttu-id="41a8b-113">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41a8b-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
