---
title: ICeeGen::AddSectionReloc メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c281d03c6e3774938cfa6e4b4b3a541738b38489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444344"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="108c1-102">ICeeGen::AddSectionReloc メソッド</span><span class="sxs-lookup"><span data-stu-id="108c1-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="108c1-103">コード ベースを .reloc 命令を追加します。</span><span class="sxs-lookup"><span data-stu-id="108c1-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="108c1-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="108c1-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="108c1-105">構文</span><span class="sxs-lookup"><span data-stu-id="108c1-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="108c1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="108c1-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="108c1-107">[in].Reloc 命令を追加するメモリ内のコードのセクション。</span><span class="sxs-lookup"><span data-stu-id="108c1-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="108c1-108">[in]このセクションのオフセット。</span><span class="sxs-lookup"><span data-stu-id="108c1-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="108c1-109">[in]これには、セクション`offset`参照します。</span><span class="sxs-lookup"><span data-stu-id="108c1-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="108c1-110">[in]1 つ、 [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)を追加する .reloc 命令の種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="108c1-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="108c1-111">要件</span><span class="sxs-lookup"><span data-stu-id="108c1-111">Requirements</span></span>  
 <span data-ttu-id="108c1-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="108c1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="108c1-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="108c1-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="108c1-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="108c1-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="108c1-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="108c1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="108c1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="108c1-116">See Also</span></span>  
 [<span data-ttu-id="108c1-117">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="108c1-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
