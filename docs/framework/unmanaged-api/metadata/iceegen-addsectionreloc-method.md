---
title: "ICeeGen::AddSectionReloc メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.AddSectionReloc
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e4bb3b1e436f51726ce50f80e1fd88c10f20fd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="4fa3a-102">ICeeGen::AddSectionReloc メソッド</span><span class="sxs-lookup"><span data-stu-id="4fa3a-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="4fa3a-103">コード ベースを .reloc 命令を追加します。</span><span class="sxs-lookup"><span data-stu-id="4fa3a-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="4fa3a-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="4fa3a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa3a-105">構文</span><span class="sxs-lookup"><span data-stu-id="4fa3a-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fa3a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4fa3a-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="4fa3a-107">[in].Reloc 命令を追加するメモリ内のコードのセクション。</span><span class="sxs-lookup"><span data-stu-id="4fa3a-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="4fa3a-108">[in]このセクションのオフセット。</span><span class="sxs-lookup"><span data-stu-id="4fa3a-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="4fa3a-109">[in]これには、セクション`offset`参照します。</span><span class="sxs-lookup"><span data-stu-id="4fa3a-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="4fa3a-110">[in]1 つ、 [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)を追加する .reloc 命令の種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="4fa3a-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fa3a-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="4fa3a-111">Requirements</span></span>  
 <span data-ttu-id="4fa3a-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4fa3a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fa3a-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4fa3a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fa3a-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="4fa3a-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4fa3a-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fa3a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa3a-116">参照</span><span class="sxs-lookup"><span data-stu-id="4fa3a-116">See Also</span></span>  
 [<span data-ttu-id="4fa3a-117">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4fa3a-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
