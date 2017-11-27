---
title: "CorPropertyAttr 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPropertyAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPropertyAttr
helpviewer_keywords: CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a87676064f39dc01d04e881bbf46476fb12a1c65
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="c6901-102">CorPropertyAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="c6901-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="c6901-103">プロパティのメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c6901-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6901-104">構文</span><span class="sxs-lookup"><span data-stu-id="c6901-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="c6901-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c6901-105">Members</span></span>  
  
|<span data-ttu-id="c6901-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c6901-106">Member</span></span>|<span data-ttu-id="c6901-107">説明</span><span class="sxs-lookup"><span data-stu-id="c6901-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="c6901-108">プロパティは、特別なことと、その名前が記述されているを指定する方法です。</span><span class="sxs-lookup"><span data-stu-id="c6901-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="c6901-109">共通言語ランタイムでは、内部使用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="c6901-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="c6901-110">共通言語ランタイム メタデータの内部 Api がプロパティ名のエンコードを確認する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6901-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="c6901-111">既定値を持つプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="c6901-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="c6901-112">使用されません。</span><span class="sxs-lookup"><span data-stu-id="c6901-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6901-113">要件</span><span class="sxs-lookup"><span data-stu-id="c6901-113">Requirements</span></span>  
 <span data-ttu-id="c6901-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c6901-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6901-115">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c6901-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c6901-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6901-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6901-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6901-117">See Also</span></span>  
 [<span data-ttu-id="c6901-118">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="c6901-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
