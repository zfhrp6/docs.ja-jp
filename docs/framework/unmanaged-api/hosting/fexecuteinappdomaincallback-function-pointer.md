---
title: FExecuteInAppDomainCallback 関数ポインター
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c3cafe3a8912702a093f9df7234112c0057b440
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431301"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="44372-102">FExecuteInAppDomainCallback 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="44372-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="44372-103">マネージ コードを実行する共通言語ランタイム (CLR) によって呼び出される関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="44372-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="44372-104">この関数ポインターが削除されて、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="44372-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44372-105">構文</span><span class="sxs-lookup"><span data-stu-id="44372-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44372-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="44372-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="44372-107">[in]実行されるマネージ コードが含まれる非透過の呼び出し元が割り当てたメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="44372-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="44372-108">割り当ておよびこのメモリの有効期間は、呼び出し元 (つまり、CLR) によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="44372-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="44372-109">これは、CLR のマネージ ヒープのメモリではありません。</span><span class="sxs-lookup"><span data-stu-id="44372-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44372-110">要件</span><span class="sxs-lookup"><span data-stu-id="44372-110">Requirements</span></span>  
 <span data-ttu-id="44372-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="44372-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44372-112">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="44372-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44372-113">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="44372-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="44372-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44372-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44372-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="44372-115">See Also</span></span>  
 <span data-ttu-id="44372-116">
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span><span class="sxs-lookup"><span data-stu-id="44372-116">[Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)</span></span>
