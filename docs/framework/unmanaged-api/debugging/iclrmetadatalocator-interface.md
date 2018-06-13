---
title: ICLRMetadataLocator インターフェイス
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd7a67237d89864915f8b4f1f7361d1f113d1e5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404743"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="f3252-102">ICLRMetadataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3252-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="f3252-103">データ アクセス サービス層でターゲット プロセス内でアセンブリのメタデータを検索するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f3252-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3252-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f3252-104">Methods</span></span>  
  
|<span data-ttu-id="f3252-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f3252-105">Method</span></span>|<span data-ttu-id="f3252-106">説明</span><span class="sxs-lookup"><span data-stu-id="f3252-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3252-107">GetMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="f3252-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="f3252-108">ターゲット プロセスからイメージのメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="f3252-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3252-109">コメント</span><span class="sxs-lookup"><span data-stu-id="f3252-109">Remarks</span></span>  
 <span data-ttu-id="f3252-110">API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3252-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="f3252-111">たとえば、ライブ プロセスの実装は、メモリ ダンプの異なるでしょう。</span><span class="sxs-lookup"><span data-stu-id="f3252-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3252-112">要件</span><span class="sxs-lookup"><span data-stu-id="f3252-112">Requirements</span></span>  
 <span data-ttu-id="f3252-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f3252-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3252-114">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f3252-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f3252-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3252-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3252-116">**.**</span><span class="sxs-lookup"><span data-stu-id="f3252-116">**.**</span></span> <span data-ttu-id="f3252-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3252-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3252-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3252-118">See Also</span></span>  
 [<span data-ttu-id="f3252-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3252-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
