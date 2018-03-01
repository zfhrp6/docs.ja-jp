---
title: "ISymUnmanagedReader::ReplaceSymbolStore メソッド"
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
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1bedceac4661204bb72e59981450d7fee488857b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="39187-102">ISymUnmanagedReader::ReplaceSymbolStore メソッド</span><span class="sxs-lookup"><span data-stu-id="39187-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="39187-103">既存のシンボル ストアをデルタ シンボル ストアで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="39187-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="39187-104">このメソッドがに似ていますが、 [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)メソッド、指定のデルタは、更新プログラムではなく、完全な置き換えとして機能する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="39187-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39187-105">1 つだけを指定する必要があります、`filename`または`pIStream`パラメーターは、両方は使用できません。</span><span class="sxs-lookup"><span data-stu-id="39187-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="39187-106">場合`filename`を指定すると、そのファイル内のシンボル、シンボル ストアが更新されます。</span><span class="sxs-lookup"><span data-stu-id="39187-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="39187-107">場合`pIStream`を指定すると、ストアからのデータで更新されます、<xref:System.Runtime.InteropServices.ComTypes.IStream>です。</span><span class="sxs-lookup"><span data-stu-id="39187-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39187-108">構文</span><span class="sxs-lookup"><span data-stu-id="39187-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39187-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="39187-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="39187-110">[in]シンボル ストアを含むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="39187-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="39187-111">[in]代わりに使用する、ファイル ストリーム、`filename`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="39187-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39187-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="39187-112">Return Value</span></span>  
 <span data-ttu-id="39187-113">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="39187-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39187-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="39187-114">Requirements</span></span>  
 <span data-ttu-id="39187-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="39187-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39187-116">参照</span><span class="sxs-lookup"><span data-stu-id="39187-116">See Also</span></span>  
 [<span data-ttu-id="39187-117">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="39187-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
