---
title: IMetaDataEmit::SetPinvokeMap メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPinvokeMap
helpviewer_keywords:
- IMetaDataEmit::SetPinvokeMap method [.NET Framework metadata]
- SetPinvokeMap method [.NET Framework metadata]
ms.assetid: c6bfd574-1da3-4ba7-82f2-46ca5efcbaba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84b2c0571a7991829e65b45759bd61fa4009aa71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445878"
---
# <a name="imetadataemitsetpinvokemap-method"></a><span data-ttu-id="e03ab-102">IMetaDataEmit::SetPinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="e03ab-102">IMetaDataEmit::SetPinvokeMap Method</span></span>
<span data-ttu-id="e03ab-103">前回の呼び出しで定義されているメソッドの PInvoke シグネチャの機能の変更を設定または[imetadataemit::definepinvokemap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="e03ab-103">Sets or changes features of a method's PInvoke signature, as defined by a prior call to [IMetaDataEmit::DefinePinvokeMap](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepinvokemap-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e03ab-104">構文</span><span class="sxs-lookup"><span data-stu-id="e03ab-104">Syntax</span></span>  
  
```  
HRESULT SetPinvokeMap (   
    [in]  mdToken      tk,   
    [in]  DWORD        dwMappingFlags,  
    [in]  LPCWSTR      szImportName,   
    [in]  mdModuleRef  mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e03ab-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e03ab-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e03ab-106">[in]`mdToken`マッピング情報が適用されます。</span><span class="sxs-lookup"><span data-stu-id="e03ab-106">[in] The `mdToken` to which mapping information applies.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="e03ab-107">[in]マッピングを実行する PInvoke を使用するフラグ。</span><span class="sxs-lookup"><span data-stu-id="e03ab-107">[in] Flags used by PInvoke to do the mapping.</span></span> <span data-ttu-id="e03ab-108">これは、ビットマスク`CorPinvokeMap`値。</span><span class="sxs-lookup"><span data-stu-id="e03ab-108">This is a bitmask of `CorPinvokeMap` values.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="e03ab-109">[in]ターゲットの名前は、ネイティブ DLL でエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="e03ab-109">[in] The name of the target export in the native DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="e03ab-110">[in]`mdModuleRef`トークン ターゲットのアンマネージ DLL です。</span><span class="sxs-lookup"><span data-stu-id="e03ab-110">[in] The `mdModuleRef` token for the target unmanaged DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e03ab-111">要件</span><span class="sxs-lookup"><span data-stu-id="e03ab-111">Requirements</span></span>  
 <span data-ttu-id="e03ab-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e03ab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e03ab-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e03ab-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e03ab-114">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="e03ab-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e03ab-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e03ab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03ab-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e03ab-116">See Also</span></span>  
 [<span data-ttu-id="e03ab-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e03ab-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e03ab-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e03ab-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
