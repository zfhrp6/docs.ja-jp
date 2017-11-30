---
title: "IMetaDataEmit::SetPinvokeMap メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a10482b12f9a34b0f247779f22c7cc70f871324a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="02119-102">IMetaDataEmit::SetPinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="02119-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="02119-103">前回の呼び出しで定義されているメソッドの PInvoke シグネチャの機能の変更を設定または[imetadataemit::definepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="02119-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02119-104">構文</span><span class="sxs-lookup"><span data-stu-id="02119-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02119-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="02119-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="02119-106">[in]`mdToken`マッピング情報が適用されます。</span><span class="sxs-lookup"><span data-stu-id="02119-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="02119-107">[in]マッピングを実行する PInvoke を使用するフラグ。</span><span class="sxs-lookup"><span data-stu-id="02119-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="02119-108">これは、ビットマスク`CorPinvokeMap`値。</span><span class="sxs-lookup"><span data-stu-id="02119-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="02119-109">[in]ターゲットの名前は、ネイティブ DLL でエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="02119-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="02119-110">[in]`mdModuleRef`トークン ターゲットのアンマネージ DLL です。</span><span class="sxs-lookup"><span data-stu-id="02119-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02119-111">要件</span><span class="sxs-lookup"><span data-stu-id="02119-111">Requirements</span></span>  
 <span data-ttu-id="02119-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="02119-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02119-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="02119-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02119-114">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="02119-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02119-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02119-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02119-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="02119-116">See Also</span></span>  
 [<span data-ttu-id="02119-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="02119-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="02119-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="02119-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
