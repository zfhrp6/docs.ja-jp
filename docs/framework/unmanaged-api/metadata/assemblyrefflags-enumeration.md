---
title: "AssemblyRefFlags 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyRefFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyRefFlags
helpviewer_keywords: AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc64d03725df89eac91c85549e287eeb2510037c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="bb38f-102">AssemblyRefFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="bb38f-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="bb38f-103">アセンブリ参照の機能を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bb38f-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb38f-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb38f-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="bb38f-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="bb38f-105">Members</span></span>  
  
|<span data-ttu-id="bb38f-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="bb38f-106">Member</span></span>|<span data-ttu-id="bb38f-107">説明</span><span class="sxs-lookup"><span data-stu-id="bb38f-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="bb38f-108">アセンブリ参照がアセンブリの発行者に関する完全、ハッシュされていない情報が含まれているを指定します。</span><span class="sxs-lookup"><span data-stu-id="bb38f-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb38f-109">要件</span><span class="sxs-lookup"><span data-stu-id="bb38f-109">Requirements</span></span>  
 <span data-ttu-id="bb38f-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb38f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb38f-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb38f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb38f-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb38f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb38f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb38f-113">See Also</span></span>  
 [<span data-ttu-id="bb38f-114">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="bb38f-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="bb38f-115">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb38f-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="bb38f-116">DefineAssemblyRef メソッド</span><span class="sxs-lookup"><span data-stu-id="bb38f-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
