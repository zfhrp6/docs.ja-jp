---
title: ICorPublish::EnumProcesses メソッド
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2779138a0999e34ad6424d76ddfebbcfdf611d58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422898"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="52b80-102">ICorPublish::EnumProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="52b80-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="52b80-103">このコンピューターで実行されている管理対象プロセスの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="52b80-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52b80-104">構文</span><span class="sxs-lookup"><span data-stu-id="52b80-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52b80-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52b80-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="52b80-106">値、 [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)を取得するプロセスの種類を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="52b80-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="52b80-107">現在のバージョンでのみ COR_PUB_MANAGEDONLY は有効です。</span><span class="sxs-lookup"><span data-stu-id="52b80-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="52b80-108">アドレスへのポインター、 [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)プロセスの列挙子であるインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="52b80-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52b80-109">コメント</span><span class="sxs-lookup"><span data-stu-id="52b80-109">Remarks</span></span>  
 <span data-ttu-id="52b80-110">プロセスの列挙子のコレクションが実行中のプロセスのスナップショットに基づいて、`EnumProcesses`メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="52b80-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="52b80-111">列挙子は前に終了または後に起動するプロセスは含まれません`EnumProcesses`と呼びます。</span><span class="sxs-lookup"><span data-stu-id="52b80-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="52b80-112">`EnumProcesses`メソッドは、これで 2 回以上呼び出すことは[ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)プロセスの新しい最新の状態のコレクションを作成するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="52b80-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="52b80-113">後続の呼び出しでない既存のコレクションを受ける、`EnumProcesses`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="52b80-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52b80-114">要件</span><span class="sxs-lookup"><span data-stu-id="52b80-114">Requirements</span></span>  
 <span data-ttu-id="52b80-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="52b80-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52b80-116">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="52b80-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="52b80-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52b80-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52b80-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52b80-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b80-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="52b80-119">See Also</span></span>  
 [<span data-ttu-id="52b80-120">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52b80-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
