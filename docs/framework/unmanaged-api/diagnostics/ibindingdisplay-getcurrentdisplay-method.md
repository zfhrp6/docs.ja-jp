---
title: "IBindingDisplay::GetCurrentDisplay メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.GetCurrentDisplay
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4e9ba86efe44fdcfb717970bf664198068d89d36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="f396f-102">IBindingDisplay::GetCurrentDisplay メソッド</span><span class="sxs-lookup"><span data-stu-id="f396f-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="f396f-103">現在のバインディングの表示情報を返します。</span><span class="sxs-lookup"><span data-stu-id="f396f-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f396f-104">構文</span><span class="sxs-lookup"><span data-stu-id="f396f-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f396f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f396f-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="f396f-106">[out, retval]バインディングの表示情報を含む safearray を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="f396f-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f396f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f396f-107">Remarks</span></span>  
 <span data-ttu-id="f396f-108">[Ibindingdisplay::initializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)メソッドが以前に成功しましたが、デバッガーでプログラムを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f396f-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="f396f-109">呼び出し元の返された割り当てを解除する必要があります`SAFEARRAY`を使用してメモリ[SafeArrayDestroy](http://msdn.microsoft.com/en-us/fc94f7e7-b903-4c78-905c-54df1f8d13fa)です。</span><span class="sxs-lookup"><span data-stu-id="f396f-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](http://msdn.microsoft.com/en-us/fc94f7e7-b903-4c78-905c-54df1f8d13fa).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f396f-110">要件</span><span class="sxs-lookup"><span data-stu-id="f396f-110">Requirements</span></span>  
 <span data-ttu-id="f396f-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f396f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f396f-112">**ヘッダー:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="f396f-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="f396f-113">**ライブラリ:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="f396f-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="f396f-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f396f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f396f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f396f-115">See Also</span></span>  
 [<span data-ttu-id="f396f-116">IBindingDisplay インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f396f-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 [<span data-ttu-id="f396f-117">InitializeForProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="f396f-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
