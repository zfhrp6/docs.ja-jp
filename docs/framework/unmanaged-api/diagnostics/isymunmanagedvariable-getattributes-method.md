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
ms.openlocfilehash: 41bdbf20d3905ba218802a6801c7394b237f6e0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="67f19-102">ISymUnmanagedVariable::GetAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="67f19-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="67f19-103">この変数の属性のフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="67f19-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67f19-104">構文</span><span class="sxs-lookup"><span data-stu-id="67f19-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67f19-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="67f19-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="67f19-106">[out]ポインター、`ULONG32`属性を受け取る。</span><span class="sxs-lookup"><span data-stu-id="67f19-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="67f19-107">返される値で定義されている値のいずれかになります、 [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="67f19-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67f19-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="67f19-108">Return Value</span></span>  
 <span data-ttu-id="67f19-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="67f19-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67f19-110">要件</span><span class="sxs-lookup"><span data-stu-id="67f19-110">Requirements</span></span>  
 <span data-ttu-id="67f19-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="67f19-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f19-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="67f19-112">See Also</span></span>  
 [<span data-ttu-id="67f19-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67f19-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
