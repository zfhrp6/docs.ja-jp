---
title: "StrongNameKeyDelete 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyDelete
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyDelete
helpviewer_keywords: StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3acd8ae5f330e23642a679962a04ccb4f7e8ec6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="190a9-102">StrongNameKeyDelete 関数</span><span class="sxs-lookup"><span data-stu-id="190a9-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="190a9-103">指定したキー コンテナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="190a9-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="190a9-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="190a9-104">This function has been deprecated.</span></span> <span data-ttu-id="190a9-105">使用して、 [iclrstrongname::strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="190a9-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="190a9-106">構文</span><span class="sxs-lookup"><span data-stu-id="190a9-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="190a9-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="190a9-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="190a9-108">[in]削除するキー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="190a9-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="190a9-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="190a9-109">Return Value</span></span>  
 <span data-ttu-id="190a9-110">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="190a9-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="190a9-111">コメント</span><span class="sxs-lookup"><span data-stu-id="190a9-111">Remarks</span></span>  
 <span data-ttu-id="190a9-112">使用して、 [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) importa に公開/秘密キー ペアのコンテナーに機能します。</span><span class="sxs-lookup"><span data-stu-id="190a9-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="190a9-113">場合、`StrongNameKeyDelete`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="190a9-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="190a9-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="190a9-114">Requirements</span></span>  
 <span data-ttu-id="190a9-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="190a9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="190a9-116">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="190a9-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="190a9-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="190a9-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="190a9-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="190a9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="190a9-119">参照</span><span class="sxs-lookup"><span data-stu-id="190a9-119">See Also</span></span>  
 [<span data-ttu-id="190a9-120">StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="190a9-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="190a9-121">StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="190a9-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="190a9-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="190a9-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
