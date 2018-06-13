---
title: ISymUnmanagedWriter4 インターフェイス
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e8478aed662142b9ff4b73f9cb192f8d2306e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429687"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="5b65c-102">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5b65c-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="5b65c-103">ISymUnmanagedWriter4 インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="5b65c-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b65c-104">構文</span><span class="sxs-lookup"><span data-stu-id="5b65c-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="5b65c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5b65c-105">Methods</span></span>  
 <span data-ttu-id="5b65c-106">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5b65c-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="5b65c-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="5b65c-107">Method</span></span>|<span data-ttu-id="5b65c-108">説明</span><span class="sxs-lookup"><span data-stu-id="5b65c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b65c-109">GetDebugInfoWithPadding メソッド</span><span class="sxs-lookup"><span data-stu-id="5b65c-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="5b65c-110">同様に機能[GetDebugInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)パス文字列は、文字列データの固定サイズの終端の null 文字の後に続くゼロで埋め 点を除いて`MAX_PATH`です。</span><span class="sxs-lookup"><span data-stu-id="5b65c-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="5b65c-111">自体のパス文字列の長さは場合にのみの余白に割り当てられますより小さい`MAX_PATH`です。</span><span class="sxs-lookup"><span data-stu-id="5b65c-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="5b65c-112">これにより、ツールをその差分 PE ファイルに記述を簡単にします。</span><span class="sxs-lookup"><span data-stu-id="5b65c-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5b65c-113">要件</span><span class="sxs-lookup"><span data-stu-id="5b65c-113">Requirements</span></span>  
 <span data-ttu-id="5b65c-114">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5b65c-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b65c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b65c-115">See Also</span></span>  
 [<span data-ttu-id="5b65c-116">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5b65c-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="5b65c-117">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5b65c-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
