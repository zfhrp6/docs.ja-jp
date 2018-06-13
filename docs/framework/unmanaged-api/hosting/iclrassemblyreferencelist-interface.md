---
title: ICLRAssemblyReferenceList インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 388b26a5559435ea57300751987d14bc5cb9d50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435298"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="60b8b-102">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60b8b-102">ICLRAssemblyReferenceList Interface</span></span>
<span data-ttu-id="60b8b-103">ホストではなく、共通言語ランタイム (CLR) によって読み込まれるアセンブリの一覧を管理します。</span><span class="sxs-lookup"><span data-stu-id="60b8b-103">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60b8b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="60b8b-104">Methods</span></span>  
  
|<span data-ttu-id="60b8b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="60b8b-105">Method</span></span>|<span data-ttu-id="60b8b-106">説明</span><span class="sxs-lookup"><span data-stu-id="60b8b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="60b8b-107">IsAssemblyReferenceInList メソッド</span><span class="sxs-lookup"><span data-stu-id="60b8b-107">IsAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="60b8b-108">指定されたポインターがリスト内のアセンブリを参照するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="60b8b-108">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="60b8b-109">IsStringAssemblyReferenceInList メソッド</span><span class="sxs-lookup"><span data-stu-id="60b8b-109">IsStringAssemblyReferenceInList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="60b8b-110">指定された名前が一覧内のアセンブリの名前に一致するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="60b8b-110">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60b8b-111">コメント</span><span class="sxs-lookup"><span data-stu-id="60b8b-111">Remarks</span></span>  
 <span data-ttu-id="60b8b-112">呼び出す、 [iclrassemblyidentitymanager::getclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)のインスタンスへのポインターを取得するメソッド`ICLRAssemblyReferenceList`です。</span><span class="sxs-lookup"><span data-stu-id="60b8b-112">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60b8b-113">要件</span><span class="sxs-lookup"><span data-stu-id="60b8b-113">Requirements</span></span>  
 <span data-ttu-id="60b8b-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="60b8b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60b8b-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="60b8b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60b8b-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="60b8b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60b8b-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60b8b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60b8b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="60b8b-118">See Also</span></span>  
 [<span data-ttu-id="60b8b-119">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60b8b-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="60b8b-120">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60b8b-120">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="60b8b-121">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60b8b-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
