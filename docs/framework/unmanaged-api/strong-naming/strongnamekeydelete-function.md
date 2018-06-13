---
title: StrongNameKeyDelete 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a35ec4e3c3110616ac20cd31db134371838deda0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461930"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="d18c0-102">StrongNameKeyDelete 関数</span><span class="sxs-lookup"><span data-stu-id="d18c0-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="d18c0-103">指定したキー コンテナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="d18c0-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="d18c0-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="d18c0-104">This function has been deprecated.</span></span> <span data-ttu-id="d18c0-105">使用して、 [iclrstrongname::strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="d18c0-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d18c0-106">構文</span><span class="sxs-lookup"><span data-stu-id="d18c0-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d18c0-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d18c0-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d18c0-108">[in]削除するキー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="d18c0-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d18c0-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d18c0-109">Return Value</span></span>  
 <span data-ttu-id="d18c0-110">`true` 正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="d18c0-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d18c0-111">コメント</span><span class="sxs-lookup"><span data-stu-id="d18c0-111">Remarks</span></span>  
 <span data-ttu-id="d18c0-112">使用して、 [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) importa に公開/秘密キー ペアのコンテナーに機能します。</span><span class="sxs-lookup"><span data-stu-id="d18c0-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="d18c0-113">場合、`StrongNameKeyDelete`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="d18c0-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d18c0-114">要件</span><span class="sxs-lookup"><span data-stu-id="d18c0-114">Requirements</span></span>  
 <span data-ttu-id="d18c0-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d18c0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d18c0-116">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d18c0-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d18c0-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d18c0-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d18c0-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d18c0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d18c0-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d18c0-119">See Also</span></span>  
 [<span data-ttu-id="d18c0-120">StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="d18c0-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="d18c0-121">StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="d18c0-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="d18c0-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d18c0-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
