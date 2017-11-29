---
title: "IMetaDataTables::GetGuid メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetGuid
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 52b96fbe582a5c8e1818462a5e28970dbaf50605
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="7991f-102">IMetaDataTables::GetGuid メソッド</span><span class="sxs-lookup"><span data-stu-id="7991f-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="7991f-103">指定したインデックス位置の行から GUID を取得します。</span><span class="sxs-lookup"><span data-stu-id="7991f-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7991f-104">構文</span><span class="sxs-lookup"><span data-stu-id="7991f-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7991f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7991f-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="7991f-106">[in]GUID を取得する行のインデックス。</span><span class="sxs-lookup"><span data-stu-id="7991f-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="7991f-107">[out]GUID を指すポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7991f-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7991f-108">コメント</span><span class="sxs-lookup"><span data-stu-id="7991f-108">Remarks</span></span>  
 <span data-ttu-id="7991f-109">このメソッドの使用方法は、一貫性のある結果を返さないためお勧めしませんしないでください。</span><span class="sxs-lookup"><span data-stu-id="7991f-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="7991f-110">GUID のテーブルについては、共通言語基盤 (CLI) ドキュメント、特に「Partition II:: Metadata Definition and Semantics」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7991f-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="7991f-111">ドキュメントはオンラインで入手できます。MSDN の「[ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212)」 (ECMA の C# および共通言語基盤の標準規格) と、ECMA のインターナショナル Web サイトにある「[Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7991f-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7991f-112">要件</span><span class="sxs-lookup"><span data-stu-id="7991f-112">Requirements</span></span>  
 <span data-ttu-id="7991f-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7991f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7991f-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7991f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7991f-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="7991f-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7991f-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7991f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7991f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7991f-117">See Also</span></span>  
 [<span data-ttu-id="7991f-118">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7991f-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="7991f-119">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7991f-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
