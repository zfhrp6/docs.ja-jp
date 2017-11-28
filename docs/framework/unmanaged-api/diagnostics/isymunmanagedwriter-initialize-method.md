---
title: "ISymUnmanagedWriter::Initialize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bae368919941e6a0b234736f789320b62405a17b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="01775-102">ISymUnmanagedWriter::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="01775-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="01775-103">このライターが関連付けられるメタデータ エミッタ インターフェイスを設定し、デバッグ シンボルが書き込まれる出力ファイル名を設定します。</span><span class="sxs-lookup"><span data-stu-id="01775-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="01775-104">このメソッドを 1 回だけ呼び出すことができるし、その他のライター メソッドより前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="01775-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="01775-105">一部の開発者は、ファイル名を必要があります。</span><span class="sxs-lookup"><span data-stu-id="01775-105">Some writers may require a file name.</span></span> <span data-ttu-id="01775-106">ただし、ファイル名には、ファイル名を使用しないライターへの悪影響を及ぼすことがなく、このメソッドに常に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="01775-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01775-107">構文</span><span class="sxs-lookup"><span data-stu-id="01775-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01775-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01775-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="01775-109">[in]メタデータ エミッタ インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="01775-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="01775-110">[in]デバッグ シンボルの書き込み先となるファイル名。</span><span class="sxs-lookup"><span data-stu-id="01775-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="01775-111">ファイル名を使用しないライターに対してファイル名を指定した場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="01775-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="01775-112">[in]シンボルのライターにシンボルを出力、指定した場合、指定された<xref:System.Runtime.InteropServices.ComTypes.IStream>で指定されたファイルにではなく、`filename`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="01775-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="01775-113">
          `pIStream` パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="01775-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="01775-114">[in]`true`場合、これは、完全な再構築`false`インクリメンタル コンパイルの場合。</span><span class="sxs-lookup"><span data-stu-id="01775-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01775-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="01775-115">Return Value</span></span>  
 <span data-ttu-id="01775-116">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="01775-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01775-117">要件</span><span class="sxs-lookup"><span data-stu-id="01775-117">Requirements</span></span>  
 <span data-ttu-id="01775-118">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="01775-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01775-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="01775-119">See Also</span></span>  
 [<span data-ttu-id="01775-120">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01775-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="01775-121">Initialize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="01775-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
