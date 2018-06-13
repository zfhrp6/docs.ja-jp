---
title: ISymUnmanagedWriter::CloseMethod メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71be697a8a1decd9b5f780d047c3dbb397e351d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426891"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="ebfdf-102">ISymUnmanagedWriter::CloseMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="ebfdf-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="ebfdf-103">現在のメソッドを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ebfdf-103">Closes the current method.</span></span> <span data-ttu-id="ebfdf-104">メソッドが閉じられた後は、内部にシンボルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="ebfdf-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebfdf-105">構文</span><span class="sxs-lookup"><span data-stu-id="ebfdf-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ebfdf-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="ebfdf-106">Return Value</span></span>  
 <span data-ttu-id="ebfdf-107">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ebfdf-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebfdf-108">要件</span><span class="sxs-lookup"><span data-stu-id="ebfdf-108">Requirements</span></span>  
 <span data-ttu-id="ebfdf-109">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ebfdf-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfdf-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebfdf-110">See Also</span></span>  
 [<span data-ttu-id="ebfdf-111">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ebfdf-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="ebfdf-112">OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="ebfdf-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
