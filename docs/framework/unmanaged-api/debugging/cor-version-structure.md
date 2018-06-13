---
title: COR_VERSION 構造体
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2668e36debebb5ba71277912f37833eba584fde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403280"
---
# <a name="corversion-structure"></a><span data-ttu-id="8f952-102">COR_VERSION 構造体</span><span class="sxs-lookup"><span data-stu-id="8f952-102">COR_VERSION Structure</span></span>
<span data-ttu-id="8f952-103">共通言語ランタイムの標準の 4 つの部分のバージョン番号を保存します。</span><span class="sxs-lookup"><span data-stu-id="8f952-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f952-104">構文</span><span class="sxs-lookup"><span data-stu-id="8f952-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="8f952-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="8f952-105">Members</span></span>  
  
|<span data-ttu-id="8f952-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8f952-106">Member</span></span>|<span data-ttu-id="8f952-107">説明</span><span class="sxs-lookup"><span data-stu-id="8f952-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="8f952-108">メジャー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="8f952-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="8f952-109">マイナー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="8f952-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="8f952-110">ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="8f952-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="8f952-111">サブ ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="8f952-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f952-112">コメント</span><span class="sxs-lookup"><span data-stu-id="8f952-112">Remarks</span></span>  
 <span data-ttu-id="8f952-113">バージョン番号が 1.0.3705.288 の場合は、1 はメジャー バージョン番号、マイナー バージョン番号は 0 では、ビルド番号は 3705、288 はサブ ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="8f952-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f952-114">要件</span><span class="sxs-lookup"><span data-stu-id="8f952-114">Requirements</span></span>  
 <span data-ttu-id="8f952-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8f952-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f952-116">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="8f952-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="8f952-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f952-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f952-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f952-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f952-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f952-119">See Also</span></span>  
 [<span data-ttu-id="8f952-120">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="8f952-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="8f952-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8f952-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
