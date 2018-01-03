---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54cc369b309d1ffe20d0f3e6a2d4ae4e0443c85f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="c41cd-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="c41cd-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="c41cd-103">IL オフセットの非同期メソッドをラップするコンパイラで生成された catch ハンドラーを設定します。</span><span class="sxs-lookup"><span data-stu-id="c41cd-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="c41cd-104">デバッガーは生成された catch の IL オフセットを使用してが非ユーザー コードで場合でも、ユーザー コード メソッドで発生する可能性があるかのように catch を処理します。</span><span class="sxs-lookup"><span data-stu-id="c41cd-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="c41cd-105">具体的への応答で使用されている、 **CatchHandlerFound**例外イベント。</span><span class="sxs-lookup"><span data-stu-id="c41cd-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c41cd-106">構文</span><span class="sxs-lookup"><span data-stu-id="c41cd-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c41cd-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c41cd-107">Parameters</span></span>  
  
|<span data-ttu-id="c41cd-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c41cd-108">Parameter</span></span>|<span data-ttu-id="c41cd-109">説明</span><span class="sxs-lookup"><span data-stu-id="c41cd-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="c41cd-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="c41cd-110">Return Value</span></span>  
 <span data-ttu-id="c41cd-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="c41cd-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c41cd-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="c41cd-112">Requirements</span></span>  
 <span data-ttu-id="c41cd-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c41cd-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c41cd-114">参照</span><span class="sxs-lookup"><span data-stu-id="c41cd-114">See Also</span></span>  
 [<span data-ttu-id="c41cd-115">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c41cd-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
