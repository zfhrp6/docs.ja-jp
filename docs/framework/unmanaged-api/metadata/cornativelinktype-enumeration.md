---
title: CorNativeLinkType 列挙型
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bf8848851dc99c60b8c151ed34cd536fa9a8fed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443262"
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="28052-102">CorNativeLinkType 列挙型</span><span class="sxs-lookup"><span data-stu-id="28052-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="28052-103">ネイティブ コード内のリンクの種類を示す値を提供します。</span><span class="sxs-lookup"><span data-stu-id="28052-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28052-104">構文</span><span class="sxs-lookup"><span data-stu-id="28052-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="28052-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="28052-105">Members</span></span>  
  
|<span data-ttu-id="28052-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="28052-106">Member</span></span>|<span data-ttu-id="28052-107">説明</span><span class="sxs-lookup"><span data-stu-id="28052-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="28052-108">キーワードのいずれも指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="28052-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="28052-109">ANSI キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="28052-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="28052-110">Unicode キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="28052-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="28052-111">Auto キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="28052-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="28052-112">OLE キーワードが指定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="28052-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="28052-113">使用しません。</span><span class="sxs-lookup"><span data-stu-id="28052-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28052-114">要件</span><span class="sxs-lookup"><span data-stu-id="28052-114">Requirements</span></span>  
 <span data-ttu-id="28052-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="28052-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28052-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="28052-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="28052-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="28052-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="28052-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28052-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28052-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="28052-119">See Also</span></span>  
 [<span data-ttu-id="28052-120">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="28052-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
