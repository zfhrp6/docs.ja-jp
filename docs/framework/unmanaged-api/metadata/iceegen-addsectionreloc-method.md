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
ms.openlocfilehash: a74f01e3904c6f3f472110288abbec42fa892fdc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="f3e6f-102">ICeeGen::AddSectionReloc メソッド</span><span class="sxs-lookup"><span data-stu-id="f3e6f-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="f3e6f-103">コード ベースを .reloc 命令を追加します。</span><span class="sxs-lookup"><span data-stu-id="f3e6f-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="f3e6f-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="f3e6f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e6f-105">構文</span><span class="sxs-lookup"><span data-stu-id="f3e6f-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3e6f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3e6f-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="f3e6f-107">[in].Reloc 命令を追加するメモリ内のコードのセクション。</span><span class="sxs-lookup"><span data-stu-id="f3e6f-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="f3e6f-108">[in]このセクションのオフセット。</span><span class="sxs-lookup"><span data-stu-id="f3e6f-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="f3e6f-109">[in]これには、セクション`offset`参照します。</span><span class="sxs-lookup"><span data-stu-id="f3e6f-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="f3e6f-110">[in]1 つ、 [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)を追加する .reloc 命令の種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="f3e6f-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3e6f-111">要件</span><span class="sxs-lookup"><span data-stu-id="f3e6f-111">Requirements</span></span>  
 <span data-ttu-id="f3e6f-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f3e6f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3e6f-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3e6f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3e6f-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f3e6f-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3e6f-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3e6f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3e6f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3e6f-116">See Also</span></span>  
 [<span data-ttu-id="f3e6f-117">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3e6f-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
