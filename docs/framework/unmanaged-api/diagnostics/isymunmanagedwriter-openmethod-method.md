---
title: ISymUnmanagedWriter::OpenMethod メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc41acd6a4f2ef2557d3b39523c5e398c887c454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427909"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="faa59-102">ISymUnmanagedWriter::OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="faa59-102">ISymUnmanagedWriter::OpenMethod Method</span></span>
<span data-ttu-id="faa59-103">シンボル情報は生成先のメソッドを開きます。</span><span class="sxs-lookup"><span data-stu-id="faa59-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="faa59-104">特定のメソッドでは、シーケンス ポイント、パラメーター、および構文のスコープを定義する呼び出しの現在のメソッドになります。</span><span class="sxs-lookup"><span data-stu-id="faa59-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="faa59-105">メソッド全体を囲む暗黙的な構文のスコープがあります。</span><span class="sxs-lookup"><span data-stu-id="faa59-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="faa59-106">以前に閉じられたメソッドを再び開くには、そのメソッドの以前に定義されたシンボルが消去されます。</span><span class="sxs-lookup"><span data-stu-id="faa59-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="faa59-107">一度に 1 つだけの open メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="faa59-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa59-108">構文</span><span class="sxs-lookup"><span data-stu-id="faa59-108">Syntax</span></span>  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="faa59-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="faa59-109">Parameters</span></span>  
 `method`  
 <span data-ttu-id="faa59-110">[in]開かれるメソッドのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="faa59-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="faa59-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="faa59-111">Return Value</span></span>  
 <span data-ttu-id="faa59-112">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="faa59-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faa59-113">要件</span><span class="sxs-lookup"><span data-stu-id="faa59-113">Requirements</span></span>  
 <span data-ttu-id="faa59-114">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="faa59-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa59-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="faa59-115">See Also</span></span>  
 [<span data-ttu-id="faa59-116">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="faa59-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="faa59-117">CloseMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="faa59-117">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [<span data-ttu-id="faa59-118">OpenMethod2 メソッド</span><span class="sxs-lookup"><span data-stu-id="faa59-118">OpenMethod2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
