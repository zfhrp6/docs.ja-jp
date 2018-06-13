---
title: ICorDebugModule::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d1e0f0d57440f0074a7ca179955a7a13e41f5d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415855"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="42ef6-102">ICorDebugModule::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="42ef6-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="42ef6-103">このモジュールのテーブルのエントリのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="42ef6-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42ef6-104">構文</span><span class="sxs-lookup"><span data-stu-id="42ef6-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42ef6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42ef6-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="42ef6-106">[out]ポインター、`mdModule`モジュールのメタデータを参照するトークン。</span><span class="sxs-lookup"><span data-stu-id="42ef6-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42ef6-107">コメント</span><span class="sxs-lookup"><span data-stu-id="42ef6-107">Remarks</span></span>  
 <span data-ttu-id="42ef6-108">トークンを渡すことができます、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)、 [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)、および[IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)メタデータ インポート インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="42ef6-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42ef6-109">要件</span><span class="sxs-lookup"><span data-stu-id="42ef6-109">Requirements</span></span>  
 <span data-ttu-id="42ef6-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="42ef6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42ef6-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42ef6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42ef6-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42ef6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42ef6-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42ef6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ef6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="42ef6-114">See Also</span></span>  
 [<span data-ttu-id="42ef6-115">メタデータ</span><span class="sxs-lookup"><span data-stu-id="42ef6-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
