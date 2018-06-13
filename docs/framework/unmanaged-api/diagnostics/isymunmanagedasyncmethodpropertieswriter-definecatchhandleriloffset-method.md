---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce462c4e7e9c8fb11ee74a91f3ece2465a44a834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425432"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="865f3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="865f3-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="865f3-103">IL オフセットの非同期メソッドをラップするコンパイラで生成された catch ハンドラーを設定します。</span><span class="sxs-lookup"><span data-stu-id="865f3-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="865f3-104">デバッガーは生成された catch の IL オフセットを使用してが非ユーザー コードで場合でも、ユーザー コード メソッドで発生する可能性があるかのように catch を処理します。</span><span class="sxs-lookup"><span data-stu-id="865f3-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="865f3-105">具体的への応答で使用されている、 **CatchHandlerFound**例外イベント。</span><span class="sxs-lookup"><span data-stu-id="865f3-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865f3-106">構文</span><span class="sxs-lookup"><span data-stu-id="865f3-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="865f3-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="865f3-107">Parameters</span></span>  
  
|<span data-ttu-id="865f3-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="865f3-108">Parameter</span></span>|<span data-ttu-id="865f3-109">説明</span><span class="sxs-lookup"><span data-stu-id="865f3-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="865f3-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="865f3-110">Return Value</span></span>  
 <span data-ttu-id="865f3-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="865f3-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="865f3-112">要件</span><span class="sxs-lookup"><span data-stu-id="865f3-112">Requirements</span></span>  
 <span data-ttu-id="865f3-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="865f3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865f3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="865f3-114">See Also</span></span>  
 [<span data-ttu-id="865f3-115">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="865f3-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
