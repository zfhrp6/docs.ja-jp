---
title: ICorRuntimeHost::CreateDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea2353f1375667619db47ac5e1f037ce68dbded5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438143"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="5a082-102">ICorRuntimeHost::CreateDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="5a082-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="5a082-103">アプリケーション ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="5a082-103">Creates an application domain.</span></span> <span data-ttu-id="5a082-104">呼び出し元は、型のインターフェイス ポインターを受け取ります<xref:System._AppDomain>型のインスタンスに<xref:System.AppDomain?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="5a082-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a082-105">構文</span><span class="sxs-lookup"><span data-stu-id="5a082-105">Syntax</span></span>  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a082-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5a082-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="5a082-107">[in]ドメインにわかりやすい名前を指定するために使用する省略可能なパラメーター。</span><span class="sxs-lookup"><span data-stu-id="5a082-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="5a082-108">このフレンドリ名は、ドメインを識別するデバッガーなどのユーザー インターフェイスで表示できます。</span><span class="sxs-lookup"><span data-stu-id="5a082-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="5a082-109">[in]ポインターの省略可能な配列`IIdentity`権限セットを確立するためにセキュリティ ポリシーによってマップされている証拠を表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="5a082-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="5a082-110">`IIdentity`オブジェクトを取得するには呼び出すことによって、 [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5a082-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="5a082-111">[out]型のインターフェイス ポインター<xref:System._AppDomain>のインスタンスに<xref:System.AppDomain?displayProperty=nameWithType>ドメインをさらに制御を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a082-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a082-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="5a082-112">Return Value</span></span>  
  
|<span data-ttu-id="5a082-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a082-113">HRESULT</span></span>|<span data-ttu-id="5a082-114">説明</span><span class="sxs-lookup"><span data-stu-id="5a082-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a082-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a082-115">S_OK</span></span>|<span data-ttu-id="5a082-116">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="5a082-116">The operation was successful.</span></span>|  
|<span data-ttu-id="5a082-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5a082-117">S_FALSE</span></span>|<span data-ttu-id="5a082-118">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="5a082-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5a082-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5a082-119">E_FAIL</span></span>|<span data-ttu-id="5a082-120">未知の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5a082-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5a082-121">メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。</span><span class="sxs-lookup"><span data-stu-id="5a082-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5a082-122">Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="5a082-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5a082-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5a082-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5a082-124">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="5a082-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a082-125">要件</span><span class="sxs-lookup"><span data-stu-id="5a082-125">Requirements</span></span>  
 <span data-ttu-id="5a082-126">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a082-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a082-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a082-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a082-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5a082-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a082-129">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="5a082-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a082-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a082-130">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="5a082-131">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a082-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
