---
title: IMetaDataTables::GetBlob メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 743fb1c77e2dd74487a7498be25ea23b4919032a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447300"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="b51eb-102">IMetaDataTables::GetBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="b51eb-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="b51eb-103">指定された列インデックスにあるバイナリ ラージ オブジェクト (BLOB) へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b51eb-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b51eb-104">構文</span><span class="sxs-lookup"><span data-stu-id="b51eb-104">Syntax</span></span>  
  
```  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b51eb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b51eb-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="b51eb-106">[in]取得元のメモリ アドレス`ppData`です。</span><span class="sxs-lookup"><span data-stu-id="b51eb-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="b51eb-107">[out]サイズ (バイト単位) へのポインターの`ppData`します。</span><span class="sxs-lookup"><span data-stu-id="b51eb-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="b51eb-108">[out]バイナリ データへのポインターへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b51eb-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b51eb-109">要件</span><span class="sxs-lookup"><span data-stu-id="b51eb-109">Requirements</span></span>  
 <span data-ttu-id="b51eb-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b51eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b51eb-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b51eb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b51eb-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="b51eb-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b51eb-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b51eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b51eb-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b51eb-114">See Also</span></span>  
 [<span data-ttu-id="b51eb-115">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b51eb-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="b51eb-116">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b51eb-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
