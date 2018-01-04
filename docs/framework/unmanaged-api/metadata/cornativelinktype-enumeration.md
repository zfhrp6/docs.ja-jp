---
title: "CorNativeLinkType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeLinkType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeLinkType
helpviewer_keywords: CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f19a4366958249881c1f4c33919f239f33c21b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="dfdf3-102">CorNativeLinkType 列挙型</span><span class="sxs-lookup"><span data-stu-id="dfdf3-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="dfdf3-103">ネイティブ コード内のリンクの種類を示す値を提供します。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfdf3-104">構文</span><span class="sxs-lookup"><span data-stu-id="dfdf3-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="dfdf3-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="dfdf3-105">Members</span></span>  
  
|<span data-ttu-id="dfdf3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="dfdf3-106">Member</span></span>|<span data-ttu-id="dfdf3-107">説明</span><span class="sxs-lookup"><span data-stu-id="dfdf3-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="dfdf3-108">キーワードのいずれも指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="dfdf3-109">ANSI キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="dfdf3-110">Unicode キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="dfdf3-111">Auto キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="dfdf3-112">OLE キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="dfdf3-113">使用しません。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfdf3-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="dfdf3-114">Requirements</span></span>  
 <span data-ttu-id="dfdf3-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfdf3-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dfdf3-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dfdf3-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="dfdf3-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dfdf3-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfdf3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdf3-119">参照</span><span class="sxs-lookup"><span data-stu-id="dfdf3-119">See Also</span></span>  
 [<span data-ttu-id="dfdf3-120">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="dfdf3-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
