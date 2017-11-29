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
ms.openlocfilehash: b8da034590bc5e0b2cbd9456d9d5b4ef4970f259
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="9ecc2-102">CorNativeLinkType 列挙型</span><span class="sxs-lookup"><span data-stu-id="9ecc2-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="9ecc2-103">ネイティブ コード内のリンクの種類を示す値を提供します。</span><span class="sxs-lookup"><span data-stu-id="9ecc2-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ecc2-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ecc2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9ecc2-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="9ecc2-105">Members</span></span>  
  
|<span data-ttu-id="9ecc2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9ecc2-106">Member</span></span>|<span data-ttu-id="9ecc2-107">説明</span><span class="sxs-lookup"><span data-stu-id="9ecc2-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="9ecc2-108">キーワードのいずれも指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="9ecc2-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="9ecc2-109">ANSI キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="9ecc2-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="9ecc2-110">Unicode キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="9ecc2-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="9ecc2-111">Auto キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="9ecc2-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="9ecc2-112">OLE キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="9ecc2-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="9ecc2-113">使用しません。</span><span class="sxs-lookup"><span data-stu-id="9ecc2-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ecc2-114">要件</span><span class="sxs-lookup"><span data-stu-id="9ecc2-114">Requirements</span></span>  
 <span data-ttu-id="9ecc2-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ecc2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ecc2-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9ecc2-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ecc2-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9ecc2-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9ecc2-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ecc2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecc2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ecc2-119">See Also</span></span>  
 [<span data-ttu-id="9ecc2-120">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="9ecc2-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
