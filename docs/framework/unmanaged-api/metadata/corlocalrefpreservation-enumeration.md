---
title: CorLocalRefPreservation 列挙型
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee808ba403a513b897134420b45ebe8cd3537571
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="ab268-102">CorLocalRefPreservation 列挙型</span><span class="sxs-lookup"><span data-stu-id="ab268-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="ab268-103">ローカル参照の処理のためのフラグ値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ab268-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab268-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab268-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="ab268-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ab268-105">Members</span></span>  
  
|<span data-ttu-id="ab268-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ab268-106">Member</span></span>|<span data-ttu-id="ab268-107">説明</span><span class="sxs-lookup"><span data-stu-id="ab268-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="ab268-108">ローカルの参照を保持されません。</span><span class="sxs-lookup"><span data-stu-id="ab268-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="ab268-109">ローカル型の参照を保持します。</span><span class="sxs-lookup"><span data-stu-id="ab268-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="ab268-110">ローカル メンバー参照を保持します。</span><span class="sxs-lookup"><span data-stu-id="ab268-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab268-111">要件</span><span class="sxs-lookup"><span data-stu-id="ab268-111">Requirements</span></span>  
 <span data-ttu-id="ab268-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ab268-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab268-113">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ab268-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ab268-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab268-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab268-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab268-115">See Also</span></span>  
 [<span data-ttu-id="ab268-116">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="ab268-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
