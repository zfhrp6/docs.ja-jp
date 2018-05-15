---
title: IMetaDataTables2::GetMetaDataStreamInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 756b0ff726c31bf096a1c1b70004c3ff82fe9979
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="75b3c-102">IMetaDataTables2::GetMetaDataStreamInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="75b3c-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="75b3c-103">名前、サイズ、および指定したインデックス位置にあるメタデータ ストリームの内容を取得します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b3c-104">構文</span><span class="sxs-lookup"><span data-stu-id="75b3c-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75b3c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="75b3c-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="75b3c-106">[in]要求されたメタデータ ストリームのインデックス。</span><span class="sxs-lookup"><span data-stu-id="75b3c-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="75b3c-107">[out]ストリームの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="75b3c-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="75b3c-108">[out]メタデータ ストリームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="75b3c-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="75b3c-109">[out]サイズをバイト単位での`ppv`します。</span><span class="sxs-lookup"><span data-stu-id="75b3c-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75b3c-110">要件</span><span class="sxs-lookup"><span data-stu-id="75b3c-110">Requirements</span></span>  
 <span data-ttu-id="75b3c-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="75b3c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75b3c-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="75b3c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75b3c-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="75b3c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75b3c-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75b3c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b3c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="75b3c-115">See Also</span></span>  
 [<span data-ttu-id="75b3c-116">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75b3c-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [<span data-ttu-id="75b3c-117">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75b3c-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
