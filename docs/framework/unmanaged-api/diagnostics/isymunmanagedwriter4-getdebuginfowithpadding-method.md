---
title: "ISymUnmanagedWriter4::GetDebugInfoWithPadding メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9f2f0aad37fcd63e2345cd32a00b44412ed8c7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="a0dba-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding メソッド</span><span class="sxs-lookup"><span data-stu-id="a0dba-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="a0dba-103">同様に機能[GetDebugInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)パス文字列は、文字列データの固定サイズの終端の null 文字の後に続くゼロで埋め 点を除いて`MAX_PATH`です。</span><span class="sxs-lookup"><span data-stu-id="a0dba-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="a0dba-104">自体のパス文字列の長さは場合にのみの余白に割り当てられますより小さい`MAX_PATH`です。</span><span class="sxs-lookup"><span data-stu-id="a0dba-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="a0dba-105">これにより、ツールをその差分 PE ファイルに記述を簡単にします。</span><span class="sxs-lookup"><span data-stu-id="a0dba-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0dba-106">構文</span><span class="sxs-lookup"><span data-stu-id="a0dba-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0dba-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0dba-107">Parameters</span></span>  
  
|<span data-ttu-id="a0dba-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0dba-108">Parameter</span></span>|<span data-ttu-id="a0dba-109">説明</span><span class="sxs-lookup"><span data-stu-id="a0dba-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="a0dba-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0dba-110">Return Value</span></span>  
 <span data-ttu-id="a0dba-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="a0dba-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0dba-112">要件</span><span class="sxs-lookup"><span data-stu-id="a0dba-112">Requirements</span></span>  
 <span data-ttu-id="a0dba-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a0dba-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0dba-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0dba-114">See Also</span></span>  
 [<span data-ttu-id="a0dba-115">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0dba-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
