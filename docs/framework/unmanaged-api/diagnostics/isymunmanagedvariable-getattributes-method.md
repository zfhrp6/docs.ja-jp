---
title: "ISymUnmanagedVariable::GetAttributes メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAttributes
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fa57fcb214f465a57af9638d6f5a44acf746225
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="f8f90-102">ISymUnmanagedVariable::GetAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="f8f90-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="f8f90-103">この変数の属性のフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="f8f90-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8f90-104">構文</span><span class="sxs-lookup"><span data-stu-id="f8f90-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8f90-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f8f90-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f8f90-106">[out]ポインター、`ULONG32`属性を受け取る。</span><span class="sxs-lookup"><span data-stu-id="f8f90-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="f8f90-107">返される値で定義されている値のいずれかになります、 [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="f8f90-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8f90-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f8f90-108">Return Value</span></span>  
 <span data-ttu-id="f8f90-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="f8f90-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8f90-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="f8f90-110">Requirements</span></span>  
 <span data-ttu-id="f8f90-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f8f90-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f90-112">参照</span><span class="sxs-lookup"><span data-stu-id="f8f90-112">See Also</span></span>  
 [<span data-ttu-id="f8f90-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8f90-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
