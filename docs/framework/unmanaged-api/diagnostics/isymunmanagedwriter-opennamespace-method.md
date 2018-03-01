---
title: "ISymUnmanagedWriter::OpenNamespace メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77d50f6bac87d5a110b53a69044f96f547c51904
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="ccea2-102">ISymUnmanagedWriter::OpenNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="ccea2-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="ccea2-103">新しい名前空間を開きます。</span><span class="sxs-lookup"><span data-stu-id="ccea2-103">Opens a new namespace.</span></span> <span data-ttu-id="ccea2-104">名前空間を使用するメソッドまたは変数を定義する前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ccea2-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="ccea2-105">名前空間は、入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ccea2-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccea2-106">構文</span><span class="sxs-lookup"><span data-stu-id="ccea2-106">Syntax</span></span>  
  
```  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccea2-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ccea2-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ccea2-108">[in]新しい名前空間の名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ccea2-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccea2-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ccea2-109">Return Value</span></span>  
 <span data-ttu-id="ccea2-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ccea2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccea2-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="ccea2-111">Requirements</span></span>  
 <span data-ttu-id="ccea2-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ccea2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccea2-113">参照</span><span class="sxs-lookup"><span data-stu-id="ccea2-113">See Also</span></span>  
 [<span data-ttu-id="ccea2-114">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ccea2-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="ccea2-115">CloseNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="ccea2-115">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)
