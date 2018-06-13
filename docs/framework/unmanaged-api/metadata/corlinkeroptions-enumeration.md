---
title: CorLinkerOptions 列挙型
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d154985e9c1614e6b8f13a55410ead0cb5e861b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441056"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="daefd-102">CorLinkerOptions 列挙型</span><span class="sxs-lookup"><span data-stu-id="daefd-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="daefd-103">メタデータ リンカーのオプションを選択するためのフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="daefd-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daefd-104">構文</span><span class="sxs-lookup"><span data-stu-id="daefd-104">Syntax</span></span>  
  
```  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="daefd-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="daefd-105">Members</span></span>  
  
|<span data-ttu-id="daefd-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="daefd-106">Member</span></span>|<span data-ttu-id="daefd-107">説明</span><span class="sxs-lookup"><span data-stu-id="daefd-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="daefd-108">プライベート型とグローバル関数は保持されません。</span><span class="sxs-lookup"><span data-stu-id="daefd-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="daefd-109">プライベート型とグローバル関数が保持されます。</span><span class="sxs-lookup"><span data-stu-id="daefd-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="daefd-110">要件</span><span class="sxs-lookup"><span data-stu-id="daefd-110">Requirements</span></span>  
 <span data-ttu-id="daefd-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="daefd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daefd-112">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="daefd-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="daefd-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daefd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daefd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="daefd-114">See Also</span></span>  
 [<span data-ttu-id="daefd-115">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="daefd-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
