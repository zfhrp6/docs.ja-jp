---
title: "IMetaDataImport::GetParamForMethodIndex メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamForMethodIndex
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cda4ffde7d38d74ddf7a81b6f0af4a556693094d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="ad701-102">IMetaDataImport::GetParamForMethodIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="ad701-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="ad701-103">指定した MethodDef トークンによって表されるメソッドの指定されたパラメーターを表すトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="ad701-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad701-104">構文</span><span class="sxs-lookup"><span data-stu-id="ad701-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad701-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad701-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="ad701-106">[in]パラメーターのトークンを返すメソッドを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="ad701-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="ad701-107">[in]要求されたパラメーターが発生する、パラメーター リスト内の序数位置。</span><span class="sxs-lookup"><span data-stu-id="ad701-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="ad701-108">パラメーターは、ゼロの位置が、メソッドの戻り値を持つ、1 から始まる番号が付けられます。</span><span class="sxs-lookup"><span data-stu-id="ad701-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="ad701-109">[out]要求されたパラメーターを表す ParamDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ad701-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad701-110">要件</span><span class="sxs-lookup"><span data-stu-id="ad701-110">Requirements</span></span>  
 <span data-ttu-id="ad701-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad701-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad701-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad701-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad701-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ad701-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad701-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad701-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad701-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad701-115">See Also</span></span>  
 [<span data-ttu-id="ad701-116">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad701-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ad701-117">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad701-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
