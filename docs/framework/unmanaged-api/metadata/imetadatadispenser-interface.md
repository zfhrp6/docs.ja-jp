---
title: IMetaDataDispenser インターフェイス
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b7c183a6ef61b97920fef5c80b4abad50da25bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444871"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="0536c-102">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0536c-102">IMetaDataDispenser Interface</span></span>
<span data-ttu-id="0536c-103">既存のものを開いたり、新しいメタデータ スコープを作成するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="0536c-103">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0536c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0536c-104">Methods</span></span>  
  
|<span data-ttu-id="0536c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0536c-105">Method</span></span>|<span data-ttu-id="0536c-106">説明</span><span class="sxs-lookup"><span data-stu-id="0536c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0536c-107">DefineScope メソッド</span><span class="sxs-lookup"><span data-stu-id="0536c-107">DefineScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-definescope-method.md)|<span data-ttu-id="0536c-108">新しいメタデータを作成するメモリ内には、新しい領域を作成します。</span><span class="sxs-lookup"><span data-stu-id="0536c-108">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="0536c-109">OpenScope メソッド</span><span class="sxs-lookup"><span data-stu-id="0536c-109">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)|<span data-ttu-id="0536c-110">既存のディスク上のファイルを開き、そのメタデータをメモリにマップします。</span><span class="sxs-lookup"><span data-stu-id="0536c-110">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="0536c-111">OpenScopeOnMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="0536c-111">OpenScopeOnMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="0536c-112">既存のメタデータを含んでいるメモリの領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="0536c-112">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="0536c-113">つまり、このメソッドは、既存のデータはメタデータとして扱われますメモリの指定された領域を開きます。</span><span class="sxs-lookup"><span data-stu-id="0536c-113">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0536c-114">要件</span><span class="sxs-lookup"><span data-stu-id="0536c-114">Requirements</span></span>  
 <span data-ttu-id="0536c-115">**Platform:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0536c-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0536c-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0536c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0536c-117">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="0536c-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0536c-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0536c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0536c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0536c-119">See Also</span></span>  
 [<span data-ttu-id="0536c-120">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0536c-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="0536c-121">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0536c-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
