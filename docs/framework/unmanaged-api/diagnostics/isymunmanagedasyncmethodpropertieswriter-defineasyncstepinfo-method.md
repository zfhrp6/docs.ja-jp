---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo メソッド
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ebd4bb1d674a27785ccbe5460a65fed764638ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435878"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="6bb00-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="6bb00-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="6bb00-103">非同期のグループを定義する、現在のメソッドでの操作を待機します。</span><span class="sxs-lookup"><span data-stu-id="6bb00-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="6bb00-104">各 yield オフセットでは、潜在的な yield を識別する、await の戻り値の命令と一致します。</span><span class="sxs-lookup"><span data-stu-id="6bb00-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="6bb00-105">各`breakpointMethod` / `breakpointOffset`ペアによる、非同期操作が再開、(する可能性があります、別の方法。</span><span class="sxs-lookup"><span data-stu-id="6bb00-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb00-106">構文</span><span class="sxs-lookup"><span data-stu-id="6bb00-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6bb00-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6bb00-107">Parameters</span></span>  
  
|<span data-ttu-id="6bb00-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6bb00-108">Parameter</span></span>|<span data-ttu-id="6bb00-109">説明</span><span class="sxs-lookup"><span data-stu-id="6bb00-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="6bb00-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="6bb00-110">Return Value</span></span>  
 <span data-ttu-id="6bb00-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="6bb00-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bb00-112">要件</span><span class="sxs-lookup"><span data-stu-id="6bb00-112">Requirements</span></span>  
 <span data-ttu-id="6bb00-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6bb00-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb00-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bb00-114">See Also</span></span>  
 [<span data-ttu-id="6bb00-115">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6bb00-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
