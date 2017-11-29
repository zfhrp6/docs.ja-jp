---
title: "IMetaDataTables::GetRow メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetRow
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 281824ace7696ab0fc6b3a96e0cdf307a9419313
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="dfb41-102">IMetaDataTables::GetRow メソッド</span><span class="sxs-lookup"><span data-stu-id="dfb41-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="dfb41-103">指定したテーブルのインデックスにある表で、指定した行のインデックス行を取得します。</span><span class="sxs-lookup"><span data-stu-id="dfb41-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfb41-104">構文</span><span class="sxs-lookup"><span data-stu-id="dfb41-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfb41-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dfb41-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="dfb41-106">[in]行の取得元となるテーブルのインデックス。</span><span class="sxs-lookup"><span data-stu-id="dfb41-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="dfb41-107">[in]取得する行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="dfb41-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="dfb41-108">[out]行へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dfb41-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfb41-109">コメント</span><span class="sxs-lookup"><span data-stu-id="dfb41-109">Remarks</span></span>  
 <span data-ttu-id="dfb41-110">このメソッドの使用方法は、一貫性のある結果を返さないためお勧めしませんしないでください。</span><span class="sxs-lookup"><span data-stu-id="dfb41-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="dfb41-111">GUID のテーブルについては、共通言語基盤 (CLI) ドキュメント、特に「Partition II:: Metadata Definition and Semantics」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfb41-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="dfb41-112">ドキュメントはオンラインで入手できます。MSDN の「[ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212)」 (ECMA の C# および共通言語基盤の標準規格) と、ECMA のインターナショナル Web サイトにある「[Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfb41-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfb41-113">要件</span><span class="sxs-lookup"><span data-stu-id="dfb41-113">Requirements</span></span>  
 <span data-ttu-id="dfb41-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dfb41-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfb41-115">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dfb41-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dfb41-116">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="dfb41-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dfb41-117">**.NET framework のバージョン**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfb41-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb41-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfb41-118">See Also</span></span>  
 [<span data-ttu-id="dfb41-119">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dfb41-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="dfb41-120">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dfb41-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
