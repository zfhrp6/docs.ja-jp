---
title: AssemblyRefFlags 列挙型
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de120516655c1a0578e88ecc2890701ed9fc2f6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443701"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="15452-102">AssemblyRefFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="15452-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="15452-103">アセンブリ参照の機能を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="15452-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15452-104">構文</span><span class="sxs-lookup"><span data-stu-id="15452-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="15452-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="15452-105">Members</span></span>  
  
|<span data-ttu-id="15452-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="15452-106">Member</span></span>|<span data-ttu-id="15452-107">説明</span><span class="sxs-lookup"><span data-stu-id="15452-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="15452-108">アセンブリ参照がアセンブリの発行者に関する完全、ハッシュされていない情報が含まれているを指定します。</span><span class="sxs-lookup"><span data-stu-id="15452-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15452-109">要件</span><span class="sxs-lookup"><span data-stu-id="15452-109">Requirements</span></span>  
 <span data-ttu-id="15452-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="15452-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15452-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="15452-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15452-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15452-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15452-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="15452-113">See Also</span></span>  
 [<span data-ttu-id="15452-114">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="15452-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="15452-115">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="15452-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="15452-116">DefineAssemblyRef メソッド</span><span class="sxs-lookup"><span data-stu-id="15452-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
