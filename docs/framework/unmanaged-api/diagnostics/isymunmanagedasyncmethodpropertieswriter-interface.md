---
title: "ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99d61fdb9f7e3eb2bc10de7584061d8922bf9285
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="c694a-102">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c694a-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="c694a-103">各メソッドのシンボルの省略可能な非同期メソッドの情報を定義できます。</span><span class="sxs-lookup"><span data-stu-id="c694a-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="c694a-104">常に開かれているメソッド; で使用します。つまり、呼び出しの間、 [OpenMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)と[CloseMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="c694a-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c694a-105">構文</span><span class="sxs-lookup"><span data-stu-id="c694a-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="c694a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c694a-106">Methods</span></span>  
 <span data-ttu-id="c694a-107">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c694a-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="c694a-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="c694a-108">Method</span></span>|<span data-ttu-id="c694a-109">説明</span><span class="sxs-lookup"><span data-stu-id="c694a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c694a-110">DefineAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="c694a-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="c694a-111">非同期のグループを定義する、現在のメソッドでの操作を待機します。</span><span class="sxs-lookup"><span data-stu-id="c694a-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="c694a-112">各 yield オフセットでは、潜在的な yield を識別する、await の戻り値の命令と一致します。</span><span class="sxs-lookup"><span data-stu-id="c694a-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="c694a-113">各`breakpointMethod` / `breakpointOffset`ペアを識別、非同期操作が再開されます。 別の方法である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c694a-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="c694a-114">DefineCatchHandlerILOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="c694a-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="c694a-115">IL オフセットの非同期メソッドをラップするコンパイラで生成された catch ハンドラーを設定します。</span><span class="sxs-lookup"><span data-stu-id="c694a-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="c694a-116">デバッガーは生成された catch の IL オフセットを使用して、ユーザー コード メソッドで発生することも、非ユーザー コードの場合と同様に catch を処理します。</span><span class="sxs-lookup"><span data-stu-id="c694a-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="c694a-117">具体的への応答で使用されている、 **CatchHandlerFound**例外イベント。</span><span class="sxs-lookup"><span data-stu-id="c694a-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="c694a-118">DefineKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="c694a-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="c694a-119">非同期操作を開始する開始メソッドを設定します。</span><span class="sxs-lookup"><span data-stu-id="c694a-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c694a-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="c694a-120">Requirements</span></span>  
 <span data-ttu-id="c694a-121">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c694a-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c694a-122">参照</span><span class="sxs-lookup"><span data-stu-id="c694a-122">See Also</span></span>  
 [<span data-ttu-id="c694a-123">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c694a-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
