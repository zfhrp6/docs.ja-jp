---
title: IMetaDataTables::GetNextGuid メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca2c2b7c09f0b64fc8a2ffd6bd8455caa4c22215
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448525"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="87413-102">IMetaDataTables::GetNextGuid メソッド</span><span class="sxs-lookup"><span data-stu-id="87413-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="87413-103">現在のテーブルの列には、次の GUID 値のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="87413-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87413-104">構文</span><span class="sxs-lookup"><span data-stu-id="87413-104">Syntax</span></span>  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87413-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87413-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="87413-106">[in]GUID のテーブル列からインデックス値。</span><span class="sxs-lookup"><span data-stu-id="87413-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="87413-107">[out]次の GUID 値のインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="87413-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87413-108">コメント</span><span class="sxs-lookup"><span data-stu-id="87413-108">Remarks</span></span>  
 <span data-ttu-id="87413-109">このメソッドの使用方法は、一貫性のある結果を返さないためお勧めしませんしないでください。</span><span class="sxs-lookup"><span data-stu-id="87413-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="87413-110">GUID のテーブルについては、共通言語基盤 (CLI) ドキュメント、特に「Partition II:: Metadata Definition and Semantics」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87413-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="87413-111">ドキュメントはオンラインで入手できます。MSDN の「[ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212)」 (ECMA の C# および共通言語基盤の標準規格) と、ECMA のインターナショナル Web サイトにある「[Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87413-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87413-112">要件</span><span class="sxs-lookup"><span data-stu-id="87413-112">Requirements</span></span>  
 <span data-ttu-id="87413-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="87413-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87413-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="87413-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87413-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="87413-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87413-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87413-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87413-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="87413-117">See Also</span></span>  
 [<span data-ttu-id="87413-118">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87413-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="87413-119">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87413-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
