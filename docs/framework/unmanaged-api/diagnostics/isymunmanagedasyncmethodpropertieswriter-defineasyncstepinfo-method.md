---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e305ca13e419a40e9838a46a61fe7a435b7ce56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="9281a-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="9281a-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="9281a-103">非同期のグループを定義する、現在のメソッドでの操作を待機します。</span><span class="sxs-lookup"><span data-stu-id="9281a-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="9281a-104">各 yield オフセットでは、潜在的な yield を識別する、await の戻り値の命令と一致します。</span><span class="sxs-lookup"><span data-stu-id="9281a-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="9281a-105">各`breakpointMethod` / `breakpointOffset`ペアによる、非同期操作が再開、(する可能性があります、別の方法。</span><span class="sxs-lookup"><span data-stu-id="9281a-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9281a-106">構文</span><span class="sxs-lookup"><span data-stu-id="9281a-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9281a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9281a-107">Parameters</span></span>  
  
|<span data-ttu-id="9281a-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9281a-108">Parameter</span></span>|<span data-ttu-id="9281a-109">説明</span><span class="sxs-lookup"><span data-stu-id="9281a-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="9281a-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="9281a-110">Return Value</span></span>  
 <span data-ttu-id="9281a-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="9281a-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9281a-112">要件</span><span class="sxs-lookup"><span data-stu-id="9281a-112">Requirements</span></span>  
 <span data-ttu-id="9281a-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9281a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9281a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9281a-114">See Also</span></span>  
 [<span data-ttu-id="9281a-115">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9281a-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
