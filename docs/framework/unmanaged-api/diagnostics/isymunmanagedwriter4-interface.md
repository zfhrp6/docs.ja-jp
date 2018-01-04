---
title: "ISymUnmanagedWriter4 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5531b491da70cb78de1234e750c2e15390c10ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="3ba33-102">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ba33-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="3ba33-103">ISymUnmanagedWriter4 インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3ba33-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ba33-104">構文</span><span class="sxs-lookup"><span data-stu-id="3ba33-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="3ba33-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3ba33-105">Methods</span></span>  
 <span data-ttu-id="3ba33-106">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ba33-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="3ba33-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="3ba33-107">Method</span></span>|<span data-ttu-id="3ba33-108">説明</span><span class="sxs-lookup"><span data-stu-id="3ba33-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ba33-109">GetDebugInfoWithPadding メソッド</span><span class="sxs-lookup"><span data-stu-id="3ba33-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="3ba33-110">同様に機能[GetDebugInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)パス文字列は、文字列データの固定サイズの終端の null 文字の後に続くゼロで埋め 点を除いて`MAX_PATH`です。</span><span class="sxs-lookup"><span data-stu-id="3ba33-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="3ba33-111">自体のパス文字列の長さは場合にのみの余白に割り当てられますより小さい`MAX_PATH`です。</span><span class="sxs-lookup"><span data-stu-id="3ba33-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="3ba33-112">これにより、ツールをその差分 PE ファイルに記述を簡単にします。</span><span class="sxs-lookup"><span data-stu-id="3ba33-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ba33-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="3ba33-113">Requirements</span></span>  
 <span data-ttu-id="3ba33-114">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3ba33-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba33-115">参照</span><span class="sxs-lookup"><span data-stu-id="3ba33-115">See Also</span></span>  
 [<span data-ttu-id="3ba33-116">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ba33-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="3ba33-117">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ba33-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
