---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68c5d6662d8cbecca06268bd5010878c4e476f47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="7a895-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="7a895-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="7a895-103">非同期操作を開始する開始メソッドを設定します。</span><span class="sxs-lookup"><span data-stu-id="7a895-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a895-104">構文</span><span class="sxs-lookup"><span data-stu-id="7a895-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a895-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a895-105">Parameters</span></span>  
  
|<span data-ttu-id="7a895-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a895-106">Parameter</span></span>|<span data-ttu-id="7a895-107">説明</span><span class="sxs-lookup"><span data-stu-id="7a895-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="7a895-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="7a895-108">Return Value</span></span>  
 <span data-ttu-id="7a895-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="7a895-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a895-110">要件</span><span class="sxs-lookup"><span data-stu-id="7a895-110">Requirements</span></span>  
 <span data-ttu-id="7a895-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7a895-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a895-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a895-112">See Also</span></span>  
 [<span data-ttu-id="7a895-113">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a895-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
