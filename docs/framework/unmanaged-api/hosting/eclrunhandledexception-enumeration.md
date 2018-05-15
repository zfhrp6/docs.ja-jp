---
title: EClrUnhandledException 列挙型
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eeff8aa0336c0c497e306825c6c77f4f8745ca7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="289b8-102">EClrUnhandledException 列挙型</span><span class="sxs-lookup"><span data-stu-id="289b8-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="289b8-103">ユーザー コードで処理されない例外を管理するためのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="289b8-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="289b8-104">構文</span><span class="sxs-lookup"><span data-stu-id="289b8-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="289b8-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="289b8-105">Members</span></span>  
  
|<span data-ttu-id="289b8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="289b8-106">Member</span></span>|<span data-ttu-id="289b8-107">説明</span><span class="sxs-lookup"><span data-stu-id="289b8-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="289b8-108">既定の動作が発生することを指定します。</span><span class="sxs-lookup"><span data-stu-id="289b8-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="289b8-109">プロセスは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="289b8-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="289b8-110">共通言語ランタイム (CLR) が未処理の例外を無視し、により、さらにアクションを判断する、ホストを指定します。</span><span class="sxs-lookup"><span data-stu-id="289b8-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="289b8-111">コメント</span><span class="sxs-lookup"><span data-stu-id="289b8-111">Remarks</span></span>  
 <span data-ttu-id="289b8-112">CLR が以前のバージョンと同様に動作するを指定する、`eHostDeterminedPolicy`メンバー。</span><span class="sxs-lookup"><span data-stu-id="289b8-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="289b8-113">要件</span><span class="sxs-lookup"><span data-stu-id="289b8-113">Requirements</span></span>  
 <span data-ttu-id="289b8-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="289b8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="289b8-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="289b8-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="289b8-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="289b8-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="289b8-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="289b8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289b8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="289b8-118">See Also</span></span>  
 [<span data-ttu-id="289b8-119">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="289b8-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="289b8-120">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="289b8-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="289b8-121">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="289b8-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="289b8-122">SetUnhandledExceptionPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="289b8-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="289b8-123">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="289b8-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="289b8-124">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="289b8-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
