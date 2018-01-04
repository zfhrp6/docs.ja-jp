---
title: "CorRefToDefCheck 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRefToDefCheck
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRefToDefCheck
helpviewer_keywords: CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 366110eca3c4621866213b2c9fc4bcf99103d0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="cb65d-102">CorRefToDefCheck 列挙型</span><span class="sxs-lookup"><span data-stu-id="cb65d-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="cb65d-103">コードを最適化するために定義に変換される、参照先アイテムを制御するフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb65d-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb65d-104">構文</span><span class="sxs-lookup"><span data-stu-id="cb65d-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="cb65d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="cb65d-105">Members</span></span>  
  
|<span data-ttu-id="cb65d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cb65d-106">Member</span></span>|<span data-ttu-id="cb65d-107">説明</span><span class="sxs-lookup"><span data-stu-id="cb65d-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="cb65d-108">定義に変換する必要があります型参照とメンバーの参照を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb65d-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="cb65d-109">これは既定値 (`MDTypeRefToDef` &#124;です。`MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="cb65d-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="cb65d-110">参照されているすべての項目は定義に変換することを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb65d-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="cb65d-111">定義を参照先の項目を変換なしかを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb65d-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="cb65d-112">型参照のみが型定義に変換されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb65d-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="cb65d-113">メンバーの参照だけが定義に変換されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb65d-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="cb65d-114">つまり、メンバー参照は、メソッドの定義またはフィールドの定義のいずれかに変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb65d-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb65d-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="cb65d-115">Requirements</span></span>  
 <span data-ttu-id="cb65d-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb65d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb65d-117">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cb65d-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cb65d-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb65d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb65d-119">参照</span><span class="sxs-lookup"><span data-stu-id="cb65d-119">See Also</span></span>  
 [<span data-ttu-id="cb65d-120">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="cb65d-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
