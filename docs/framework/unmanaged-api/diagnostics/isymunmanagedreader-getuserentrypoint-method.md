---
title: ISymUnmanagedReader::GetUserEntryPoint メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b4c334d82320066bf9459907660fe6b7e2acefd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425322"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="aaf93-102">ISymUnmanagedReader::GetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="aaf93-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="aaf93-103">存在する場合は、モジュールのユーザー エントリ ポイントとして指定されたメソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="aaf93-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="aaf93-104">たとえば、このメソッドは、メイン メソッドの前に、コンパイラによって生成されたスタブではなく、ユーザーのメイン メソッド可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aaf93-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf93-105">構文</span><span class="sxs-lookup"><span data-stu-id="aaf93-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aaf93-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aaf93-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="aaf93-107">[out]エントリ ポイントを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aaf93-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaf93-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="aaf93-108">Return Value</span></span>  
 <span data-ttu-id="aaf93-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="aaf93-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaf93-110">要件</span><span class="sxs-lookup"><span data-stu-id="aaf93-110">Requirements</span></span>  
 <span data-ttu-id="aaf93-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aaf93-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf93-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="aaf93-112">See Also</span></span>  
 [<span data-ttu-id="aaf93-113">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aaf93-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
