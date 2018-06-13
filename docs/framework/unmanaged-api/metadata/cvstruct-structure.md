---
title: CVStruct 構造体
ms.date: 03/30/2017
api_name:
- CVStruct
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CVStruct
helpviewer_keywords:
- CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 195f311d58f2169d715bb33986ee6e591622f377
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445044"
---
# <a name="cvstruct-structure"></a><span data-ttu-id="49a92-102">CVStruct 構造体</span><span class="sxs-lookup"><span data-stu-id="49a92-102">CVStruct Structure</span></span>
<span data-ttu-id="49a92-103">モジュールまたは複合イメージをインストールするときに使用する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="49a92-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49a92-104">構文</span><span class="sxs-lookup"><span data-stu-id="49a92-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="49a92-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="49a92-105">Members</span></span>  
  
|<span data-ttu-id="49a92-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="49a92-106">Member</span></span>|<span data-ttu-id="49a92-107">説明</span><span class="sxs-lookup"><span data-stu-id="49a92-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="49a92-108">Major</span><span class="sxs-lookup"><span data-stu-id="49a92-108">Major</span></span>|<span data-ttu-id="49a92-109">メジャー バージョンのビルド番号です。</span><span class="sxs-lookup"><span data-stu-id="49a92-109">Major version build number.</span></span>|  
|<span data-ttu-id="49a92-110">マイナー</span><span class="sxs-lookup"><span data-stu-id="49a92-110">Minor</span></span>|<span data-ttu-id="49a92-111">ビルド番号のマイナー バージョンです。</span><span class="sxs-lookup"><span data-stu-id="49a92-111">Minor version build number.</span></span>|  
|<span data-ttu-id="49a92-112">Sub</span><span class="sxs-lookup"><span data-stu-id="49a92-112">Sub</span></span>|<span data-ttu-id="49a92-113">サブ ビルド番号です。</span><span class="sxs-lookup"><span data-stu-id="49a92-113">Sub-build number.</span></span>|  
|<span data-ttu-id="49a92-114">ビルド</span><span class="sxs-lookup"><span data-stu-id="49a92-114">Build</span></span>|<span data-ttu-id="49a92-115">ビルド番号です。</span><span class="sxs-lookup"><span data-stu-id="49a92-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49a92-116">要件</span><span class="sxs-lookup"><span data-stu-id="49a92-116">Requirements</span></span>  
 <span data-ttu-id="49a92-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="49a92-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49a92-118">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="49a92-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49a92-119">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="49a92-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="49a92-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49a92-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49a92-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="49a92-121">See Also</span></span>  
 [<span data-ttu-id="49a92-122">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="49a92-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
