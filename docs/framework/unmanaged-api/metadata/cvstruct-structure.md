---
title: "CVStruct 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CVStruct
api_location: mscoree.dll
api_type: COM
f1_keywords: CVStruct
helpviewer_keywords: CVStruct structure [.NET Framework metadata]
ms.assetid: e9e4e497-d5fb-464b-991c-3bdd824664fd
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 95c1aeb0cacef929e99e5121f29e2f69b320caec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cvstruct-structure"></a><span data-ttu-id="a6600-102">CVStruct 構造体</span><span class="sxs-lookup"><span data-stu-id="a6600-102">CVStruct Structure</span></span>
<span data-ttu-id="a6600-103">モジュールまたは複合イメージをインストールするときに使用する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6600-103">Contains information that is used when installing a module or a composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6600-104">構文</span><span class="sxs-lookup"><span data-stu-id="a6600-104">Syntax</span></span>  
  
```  
typedef struct {  
    short Major;  
    short Minor;  
    short Sub;  
    short Build;  
} CVStruct;  
```  
  
## <a name="members"></a><span data-ttu-id="a6600-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a6600-105">Members</span></span>  
  
|<span data-ttu-id="a6600-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a6600-106">Member</span></span>|<span data-ttu-id="a6600-107">説明</span><span class="sxs-lookup"><span data-stu-id="a6600-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a6600-108">Major</span><span class="sxs-lookup"><span data-stu-id="a6600-108">Major</span></span>|<span data-ttu-id="a6600-109">メジャー バージョンのビルド番号です。</span><span class="sxs-lookup"><span data-stu-id="a6600-109">Major version build number.</span></span>|  
|<span data-ttu-id="a6600-110">Minor</span><span class="sxs-lookup"><span data-stu-id="a6600-110">Minor</span></span>|<span data-ttu-id="a6600-111">ビルド番号のマイナー バージョンです。</span><span class="sxs-lookup"><span data-stu-id="a6600-111">Minor version build number.</span></span>|  
|<span data-ttu-id="a6600-112">Sub</span><span class="sxs-lookup"><span data-stu-id="a6600-112">Sub</span></span>|<span data-ttu-id="a6600-113">サブ ビルド番号です。</span><span class="sxs-lookup"><span data-stu-id="a6600-113">Sub-build number.</span></span>|  
|<span data-ttu-id="a6600-114">ビルド</span><span class="sxs-lookup"><span data-stu-id="a6600-114">Build</span></span>|<span data-ttu-id="a6600-115">ビルド番号です。</span><span class="sxs-lookup"><span data-stu-id="a6600-115">Build number.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6600-116">要件</span><span class="sxs-lookup"><span data-stu-id="a6600-116">Requirements</span></span>  
 <span data-ttu-id="a6600-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a6600-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6600-118">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a6600-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6600-119">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="a6600-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6600-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6600-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6600-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6600-121">See Also</span></span>  
 [<span data-ttu-id="a6600-122">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="a6600-122">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
