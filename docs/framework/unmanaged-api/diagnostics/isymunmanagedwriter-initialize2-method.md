---
title: "ISymUnmanagedWriter::Initialize2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e76543c35a717b95ae37985648986abaf16bf85d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="03e22-102">ISymUnmanagedWriter::Initialize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="03e22-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="03e22-103">このライターが関連付けられるメタデータ エミッタ インターフェイスを設定し、デバッグ シンボルが書き込まれる出力ファイル名を設定します。</span><span class="sxs-lookup"><span data-stu-id="03e22-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="03e22-104">このメソッドを使用して、プログラム データベース (PDB) ファイルの最終的な場所を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="03e22-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e22-105">構文</span><span class="sxs-lookup"><span data-stu-id="03e22-105">Syntax</span></span>  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03e22-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03e22-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="03e22-107">[in]メタデータ エミッタ インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="03e22-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="03e22-108">[in]ポインター、`WCHAR`デバッグ シンボルの書き込み先となるファイル名を格納しています。</span><span class="sxs-lookup"><span data-stu-id="03e22-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="03e22-109">ファイル名を使用しないライターに対してファイル名を指定した場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="03e22-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="03e22-110">[in]シンボルのライターにシンボルを生成する、指定した場合、指定された<xref:System.Runtime.InteropServices.ComTypes.IStream>で指定されたファイルにではなく、`filename`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="03e22-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="03e22-111">
          `pIStream` パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="03e22-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="03e22-112">[in]`true`場合、これは、完全な再構築`false`インクリメンタル コンパイルの場合。</span><span class="sxs-lookup"><span data-stu-id="03e22-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="03e22-113">[in]ポインター、 `WCHAR` PDB ファイルの最終的な場所にパス文字列はします。</span><span class="sxs-lookup"><span data-stu-id="03e22-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03e22-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="03e22-114">Return Value</span></span>  
 <span data-ttu-id="03e22-115">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="03e22-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e22-116">要件</span><span class="sxs-lookup"><span data-stu-id="03e22-116">Requirements</span></span>  
 <span data-ttu-id="03e22-117">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="03e22-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e22-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="03e22-118">See Also</span></span>  
 [<span data-ttu-id="03e22-119">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03e22-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="03e22-120">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="03e22-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
