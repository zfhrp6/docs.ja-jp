---
title: "ICLRMetadataLocator インターフェイス"
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
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a06997c47a85ced56dc579759192f7256def4f5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="93d1c-102">ICLRMetadataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93d1c-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="93d1c-103">データ アクセス サービス層でターゲット プロセス内でアセンブリのメタデータを検索するために使用します。</span><span class="sxs-lookup"><span data-stu-id="93d1c-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93d1c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="93d1c-104">Methods</span></span>  
  
|<span data-ttu-id="93d1c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="93d1c-105">Method</span></span>|<span data-ttu-id="93d1c-106">説明</span><span class="sxs-lookup"><span data-stu-id="93d1c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93d1c-107">GetMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="93d1c-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="93d1c-108">ターゲット プロセスからイメージのメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="93d1c-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93d1c-109">コメント</span><span class="sxs-lookup"><span data-stu-id="93d1c-109">Remarks</span></span>  
 <span data-ttu-id="93d1c-110">API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93d1c-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="93d1c-111">たとえば、ライブ プロセスの実装は、メモリ ダンプの異なるでしょう。</span><span class="sxs-lookup"><span data-stu-id="93d1c-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93d1c-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="93d1c-112">Requirements</span></span>  
 <span data-ttu-id="93d1c-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="93d1c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93d1c-114">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="93d1c-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="93d1c-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93d1c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93d1c-116">**.**</span><span class="sxs-lookup"><span data-stu-id="93d1c-116">**.**</span></span> <span data-ttu-id="93d1c-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93d1c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93d1c-118">参照</span><span class="sxs-lookup"><span data-stu-id="93d1c-118">See Also</span></span>  
 [<span data-ttu-id="93d1c-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93d1c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
