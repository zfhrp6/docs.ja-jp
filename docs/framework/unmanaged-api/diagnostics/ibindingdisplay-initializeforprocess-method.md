---
title: IBindingDisplay::InitializeForProcess メソッド
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8954c2f6ecaf2767dd01b0601096d9e3f6df9b98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425455"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="ef1b3-102">IBindingDisplay::InitializeForProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="ef1b3-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="ef1b3-103">初期化、 [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ef1b3-103">Initializes the [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef1b3-104">構文</span><span class="sxs-lookup"><span data-stu-id="ef1b3-104">Syntax</span></span>  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef1b3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ef1b3-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="ef1b3-106">[in]プロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="ef1b3-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef1b3-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ef1b3-107">Remarks</span></span>  
 <span data-ttu-id="ef1b3-108">デバッガーの呼び出し、`InitializeForProcess`メソッド作成時にバインディングの表示を初期化します。</span><span class="sxs-lookup"><span data-stu-id="ef1b3-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="ef1b3-109">`InitializeForProcess` その他のメソッドの前に、作成時に呼び出す必要があります`IBindingDisplay`と呼びます。</span><span class="sxs-lookup"><span data-stu-id="ef1b3-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef1b3-110">要件</span><span class="sxs-lookup"><span data-stu-id="ef1b3-110">Requirements</span></span>  
 <span data-ttu-id="ef1b3-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef1b3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef1b3-112">**ヘッダー:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="ef1b3-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="ef1b3-113">**ライブラリ:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="ef1b3-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="ef1b3-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef1b3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef1b3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef1b3-115">See Also</span></span>  
 [<span data-ttu-id="ef1b3-116">IBindingDisplay インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef1b3-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
