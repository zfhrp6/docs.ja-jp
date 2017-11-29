---
title: "ICorDebugModule::GetToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c06c4c8ac937864748cbac8872de9b3994db2464
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="ef60f-102">ICorDebugModule::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="ef60f-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="ef60f-103">このモジュールのテーブルのエントリのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="ef60f-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef60f-104">構文</span><span class="sxs-lookup"><span data-stu-id="ef60f-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef60f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ef60f-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="ef60f-106">[out]ポインター、`mdModule`モジュールのメタデータを参照するトークン。</span><span class="sxs-lookup"><span data-stu-id="ef60f-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef60f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ef60f-107">Remarks</span></span>  
 <span data-ttu-id="ef60f-108">トークンを渡すことができます、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)、 [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)、および[IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)メタデータ インポート インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="ef60f-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef60f-109">要件</span><span class="sxs-lookup"><span data-stu-id="ef60f-109">Requirements</span></span>  
 <span data-ttu-id="ef60f-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef60f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef60f-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef60f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef60f-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef60f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef60f-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef60f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef60f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef60f-114">See Also</span></span>  
 [<span data-ttu-id="ef60f-115">メタデータ</span><span class="sxs-lookup"><span data-stu-id="ef60f-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
