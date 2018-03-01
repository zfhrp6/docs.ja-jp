---
title: "IMetaDataTables::GetGuid メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 58dbcb7ebf56f126d89a42a1f5df6247266cb38c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="e779f-102">IMetaDataTables::GetGuid メソッド</span><span class="sxs-lookup"><span data-stu-id="e779f-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="e779f-103">指定したインデックス位置の行から GUID を取得します。</span><span class="sxs-lookup"><span data-stu-id="e779f-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e779f-104">構文</span><span class="sxs-lookup"><span data-stu-id="e779f-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e779f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e779f-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="e779f-106">[in]GUID を取得する行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="e779f-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="e779f-107">[out]GUID を指すポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e779f-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e779f-108">コメント</span><span class="sxs-lookup"><span data-stu-id="e779f-108">Remarks</span></span>  
 <span data-ttu-id="e779f-109">このメソッドの使用方法は、一貫性のある結果を返さないためお勧めしませんしないでください。</span><span class="sxs-lookup"><span data-stu-id="e779f-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e779f-110">GUID のテーブルについては、共通言語基盤 (CLI) ドキュメント、特に「Partition II:: Metadata Definition and Semantics」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e779f-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e779f-111">ドキュメントはオンラインで入手できます。MSDN の「[ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212)」 (ECMA の C# および共通言語基盤の標準規格) と、ECMA のインターナショナル Web サイトにある「[Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e779f-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e779f-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="e779f-112">Requirements</span></span>  
 <span data-ttu-id="e779f-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e779f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e779f-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e779f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e779f-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="e779f-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e779f-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e779f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e779f-117">参照</span><span class="sxs-lookup"><span data-stu-id="e779f-117">See Also</span></span>  
 [<span data-ttu-id="e779f-118">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e779f-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="e779f-119">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e779f-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
