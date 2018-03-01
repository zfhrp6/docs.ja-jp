---
title: "IMetaDataDispenser インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 678796357b36beb26ebbf34edc713ff6f15a7c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="cae04-102">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cae04-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="cae04-103">既存のものを開いたり、新しいメタデータ スコープを作成するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="cae04-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cae04-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="cae04-104">Methods</span></span>  
  
|<span data-ttu-id="cae04-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cae04-105">Method</span></span>|<span data-ttu-id="cae04-106">説明</span><span class="sxs-lookup"><span data-stu-id="cae04-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cae04-107">DefineScope メソッド</span><span class="sxs-lookup"><span data-stu-id="cae04-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="cae04-108">新しいメタデータを作成するメモリ内には、新しい領域を作成します。</span><span class="sxs-lookup"><span data-stu-id="cae04-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="cae04-109">OpenScope メソッド</span><span class="sxs-lookup"><span data-stu-id="cae04-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="cae04-110">既存のディスク上のファイルを開き、そのメタデータをメモリにマップします。</span><span class="sxs-lookup"><span data-stu-id="cae04-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="cae04-111">OpenScopeOnMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="cae04-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="cae04-112">既存のメタデータを含んでいるメモリの領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="cae04-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="cae04-113">つまり、このメソッドは、既存のデータはメタデータとして扱われますメモリの指定された領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="cae04-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cae04-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="cae04-114">Requirements</span></span>  
 <span data-ttu-id="cae04-115">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cae04-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cae04-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cae04-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cae04-117">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="cae04-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cae04-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cae04-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae04-119">参照</span><span class="sxs-lookup"><span data-stu-id="cae04-119">See Also</span></span>  
 [<span data-ttu-id="cae04-120">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cae04-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="cae04-121">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cae04-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
