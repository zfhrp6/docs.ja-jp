---
title: "CeeSectionRelocExtra 共用体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CeeSectionRelocExtra Union
api_location: mscoree.dll
api_type: COM
f1_keywords: CeeSectionRelocExtra
helpviewer_keywords: CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9591967dc70d54bd020414077fcc57b8007db9d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="13d63-102">CeeSectionRelocExtra 共用体</span><span class="sxs-lookup"><span data-stu-id="13d63-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="13d63-103">によって使用されるアドレスのオフセットを表す、 [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)セクションを再配置するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="13d63-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13d63-104">構文</span><span class="sxs-lookup"><span data-stu-id="13d63-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="13d63-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="13d63-105">Members</span></span>  
  
|<span data-ttu-id="13d63-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="13d63-106">Member</span></span>|<span data-ttu-id="13d63-107">説明</span><span class="sxs-lookup"><span data-stu-id="13d63-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="13d63-108">セクションの上位アドレスを調整します。</span><span class="sxs-lookup"><span data-stu-id="13d63-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13d63-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="13d63-109">Requirements</span></span>  
 <span data-ttu-id="13d63-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="13d63-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13d63-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13d63-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13d63-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="13d63-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13d63-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13d63-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13d63-114">参照</span><span class="sxs-lookup"><span data-stu-id="13d63-114">See Also</span></span>  
 [<span data-ttu-id="13d63-115">メタデータ共用体</span><span class="sxs-lookup"><span data-stu-id="13d63-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
