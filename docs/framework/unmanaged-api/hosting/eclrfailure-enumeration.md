---
title: EClrFailure 列挙型
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef4e12015adc3d6e67ad9c8ba8b152cd775b85e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431930"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="1ffd4-102">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="1ffd4-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="1ffd4-103">ホストがポリシーのアクションを設定できるエラーのセットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ffd4-104">構文</span><span class="sxs-lookup"><span data-stu-id="1ffd4-104">Syntax</span></span>  
  
```  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="1ffd4-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1ffd4-105">Members</span></span>  
  
|<span data-ttu-id="1ffd4-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1ffd4-106">Member</span></span>|<span data-ttu-id="1ffd4-107">説明</span><span class="sxs-lookup"><span data-stu-id="1ffd4-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="1ffd4-108">コードの重要ではない領域で、(スレッド、メモリのブロックまたはロック) などのリソースの割り当ての試行中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="1ffd4-109">コードの重要な領域で、(スレッド、メモリのブロックまたはロック) などのリソースの割り当ての試行中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="1ffd4-110">共通言語ランタイム (CLR) は、プロセスでマネージ コードを実行することはありません。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="1ffd4-111">今後は、ホスティングの関数に呼び出すには、HOST_E_CLRNOTAVAILABLE の HRESULT 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="1ffd4-112">スレッドがから戻ったときにロックの解除に失敗しました、<xref:System.AppDomain>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="1ffd4-113">ホストは、スレッドを終了させるには、このエラーを設定できません。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="1ffd4-114">スタック オーバーフローが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="1ffd4-115">読み取りまたは書き込み保護されているメモリを試みました。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="1ffd4-116">サポートされていません、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-116">Not supported in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="1ffd4-117">コード コントラクト エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-117">A code contract failure occurred.</span></span> <span data-ttu-id="1ffd4-118">参照してください[コード コントラクト](../../../../docs/framework/debug-trace-profile/code-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ffd4-119">コメント</span><span class="sxs-lookup"><span data-stu-id="1ffd4-119">Remarks</span></span>  
 <span data-ttu-id="1ffd4-120">参照してください、 [iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)メソッドの一覧については[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)値が、ホストを使用して、エラー状態のポリシーのアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="1ffd4-121">コードの詳細については、重要および重大でない地域は、次を参照してください。 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ffd4-122">要件</span><span class="sxs-lookup"><span data-stu-id="1ffd4-122">Requirements</span></span>  
 <span data-ttu-id="1ffd4-123">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ffd4-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ffd4-124">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ffd4-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ffd4-125">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ffd4-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ffd4-126">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ffd4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffd4-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ffd4-127">See Also</span></span>  
 [<span data-ttu-id="1ffd4-128">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ffd4-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="1ffd4-129">SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="1ffd4-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)  
 [<span data-ttu-id="1ffd4-130">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ffd4-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="1ffd4-131">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="1ffd4-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
