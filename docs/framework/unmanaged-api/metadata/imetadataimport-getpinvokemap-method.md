---
title: IMetaDataImport::GetPinvokeMap メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2174537e9605ad35e4f6f878954e318c7032b080
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448349"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="712b0-102">IMetaDataImport::GetPinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="712b0-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="712b0-103">PInvoke 呼び出しの対象アセンブリを表す ModuleRef トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="712b0-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712b0-104">構文</span><span class="sxs-lookup"><span data-stu-id="712b0-104">Syntax</span></span>  
  
```  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="712b0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="712b0-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="712b0-106">[in]PInvoke マッピング メタデータを取得する FieldDef または MethodDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="712b0-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="712b0-107">[out]フラグを使用してマップへのポインター。</span><span class="sxs-lookup"><span data-stu-id="712b0-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="712b0-108">この値からビットマスクである、 [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="712b0-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="712b0-109">[out]アンマネージ ターゲット DLL の名前。</span><span class="sxs-lookup"><span data-stu-id="712b0-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="712b0-110">[in]ワイド文字単位のサイズ`szImportName`です。</span><span class="sxs-lookup"><span data-stu-id="712b0-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="712b0-111">[out]ワイド文字数で返される`szImportName`です。</span><span class="sxs-lookup"><span data-stu-id="712b0-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="712b0-112">[out]アンマネージ ターゲット オブジェクト ライブラリを表す ModuleRef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="712b0-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="712b0-113">要件</span><span class="sxs-lookup"><span data-stu-id="712b0-113">Requirements</span></span>  
 <span data-ttu-id="712b0-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="712b0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="712b0-115">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="712b0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="712b0-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="712b0-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="712b0-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="712b0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="712b0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="712b0-118">See Also</span></span>  
 [<span data-ttu-id="712b0-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="712b0-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="712b0-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="712b0-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
