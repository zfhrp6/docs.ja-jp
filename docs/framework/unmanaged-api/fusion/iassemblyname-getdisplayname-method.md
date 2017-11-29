---
title: "IAssemblyName::GetDisplayName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.GetDisplayName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 810192848e15a200a4b2eb33eaf60ddbd7c7c607
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="ee2d7-102">IAssemblyName::GetDisplayName メソッド</span><span class="sxs-lookup"><span data-stu-id="ee2d7-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="ee2d7-103">これによって参照されるアセンブリの人間が判読できる名前を取得[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ee2d7-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee2d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="ee2d7-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee2d7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ee2d7-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="ee2d7-106">[out]参照先アセンブリの名前を格納している文字列バッファー。</span><span class="sxs-lookup"><span data-stu-id="ee2d7-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="ee2d7-107">[入力、出力].サイズ`szDisplayName`ワイド文字、終端の null 文字を含むです。</span><span class="sxs-lookup"><span data-stu-id="ee2d7-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="ee2d7-108">[in]ビットごとの組み合わせ[ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md)の機能に影響を与える値`szDisplayName`です。</span><span class="sxs-lookup"><span data-stu-id="ee2d7-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee2d7-109">要件</span><span class="sxs-lookup"><span data-stu-id="ee2d7-109">Requirements</span></span>  
 <span data-ttu-id="ee2d7-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ee2d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee2d7-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ee2d7-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ee2d7-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee2d7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2d7-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee2d7-113">See Also</span></span>  
 [<span data-ttu-id="ee2d7-114">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee2d7-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="ee2d7-115">Fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="ee2d7-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
