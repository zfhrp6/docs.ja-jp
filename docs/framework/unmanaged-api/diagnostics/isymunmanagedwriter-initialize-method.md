---
title: ISymUnmanagedWriter::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44046560f4f788c4a7d695ff18c9c01740fea35a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428036"
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="ffddc-102">ISymUnmanagedWriter::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="ffddc-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="ffddc-103">このライターが関連付けられるメタデータ エミッタ インターフェイスを設定し、デバッグ シンボルが書き込まれる出力ファイル名を設定します。</span><span class="sxs-lookup"><span data-stu-id="ffddc-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="ffddc-104">このメソッドを 1 回だけ呼び出すことができるし、その他のライター メソッドより前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffddc-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="ffddc-105">一部の開発者は、ファイル名を必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffddc-105">Some writers may require a file name.</span></span> <span data-ttu-id="ffddc-106">ただし、ファイル名には、ファイル名を使用しないライターへの悪影響を及ぼすことがなく、このメソッドに常に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="ffddc-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffddc-107">構文</span><span class="sxs-lookup"><span data-stu-id="ffddc-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffddc-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ffddc-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="ffddc-109">[in]メタデータ エミッタ インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ffddc-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="ffddc-110">[in]デバッグ シンボルの書き込み先となるファイル名。</span><span class="sxs-lookup"><span data-stu-id="ffddc-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="ffddc-111">ファイル名を使用しないライターに対してファイル名を指定した場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="ffddc-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="ffddc-112">[in]シンボルのライターにシンボルを出力、指定した場合、指定された<xref:System.Runtime.InteropServices.ComTypes.IStream>で指定されたファイルにではなく、`filename`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="ffddc-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="ffddc-113">
          `pIStream` パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ffddc-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="ffddc-114">[in]`true`場合、これは、完全な再構築`false`インクリメンタル コンパイルの場合。</span><span class="sxs-lookup"><span data-stu-id="ffddc-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffddc-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="ffddc-115">Return Value</span></span>  
 <span data-ttu-id="ffddc-116">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ffddc-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffddc-117">要件</span><span class="sxs-lookup"><span data-stu-id="ffddc-117">Requirements</span></span>  
 <span data-ttu-id="ffddc-118">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ffddc-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffddc-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffddc-119">See Also</span></span>  
 [<span data-ttu-id="ffddc-120">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffddc-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="ffddc-121">Initialize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="ffddc-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
