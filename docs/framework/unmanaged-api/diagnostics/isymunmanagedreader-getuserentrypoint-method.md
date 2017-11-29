---
title: "ISymUnmanagedReader::GetUserEntryPoint メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 08a89ba20b48c3d7faa3f3d27d4c57c55b33c355
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="17735-102">ISymUnmanagedReader::GetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="17735-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="17735-103">存在する場合は、モジュールのユーザー エントリ ポイントとして指定されたメソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="17735-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="17735-104">たとえば、このメソッドは、メイン メソッドの前に、コンパイラによって生成されたスタブではなく、ユーザーのメイン メソッド可能性があります。</span><span class="sxs-lookup"><span data-stu-id="17735-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17735-105">構文</span><span class="sxs-lookup"><span data-stu-id="17735-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17735-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17735-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="17735-107">[out]エントリ ポイントを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="17735-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17735-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="17735-108">Return Value</span></span>  
 <span data-ttu-id="17735-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="17735-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17735-110">要件</span><span class="sxs-lookup"><span data-stu-id="17735-110">Requirements</span></span>  
 <span data-ttu-id="17735-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="17735-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17735-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="17735-112">See Also</span></span>  
 [<span data-ttu-id="17735-113">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17735-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
