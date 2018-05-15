---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding メソッド
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a703c7c8adf5d770ea74f8ed869568978f3b42f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="db820-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding メソッド</span><span class="sxs-lookup"><span data-stu-id="db820-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="db820-103">同様に機能[GetDebugInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)パス文字列は、文字列データの固定サイズの終端の null 文字の後に続くゼロで埋め 点を除いて`MAX_PATH`です。</span><span class="sxs-lookup"><span data-stu-id="db820-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="db820-104">自体のパス文字列の長さは場合にのみの余白に割り当てられますより小さい`MAX_PATH`です。</span><span class="sxs-lookup"><span data-stu-id="db820-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="db820-105">これにより、ツールをその差分 PE ファイルに記述を簡単にします。</span><span class="sxs-lookup"><span data-stu-id="db820-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db820-106">構文</span><span class="sxs-lookup"><span data-stu-id="db820-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db820-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="db820-107">Parameters</span></span>  
  
|<span data-ttu-id="db820-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="db820-108">Parameter</span></span>|<span data-ttu-id="db820-109">説明</span><span class="sxs-lookup"><span data-stu-id="db820-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="db820-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="db820-110">Return Value</span></span>  
 <span data-ttu-id="db820-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="db820-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db820-112">要件</span><span class="sxs-lookup"><span data-stu-id="db820-112">Requirements</span></span>  
 <span data-ttu-id="db820-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="db820-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db820-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="db820-114">See Also</span></span>  
 [<span data-ttu-id="db820-115">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="db820-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
