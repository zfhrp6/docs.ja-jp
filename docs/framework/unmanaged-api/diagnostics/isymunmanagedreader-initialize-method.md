---
title: ISymUnmanagedReader::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d141d23f02b2abc92e3d4455aebe1a4057b6bb85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426474"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="ab965-102">ISymUnmanagedReader::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="ab965-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="ab965-103">このリーダーは、モジュールのファイル名と共に、関連付けられるメタデータ インポーターのインターフェイスで、シンボル リーダーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="ab965-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab965-104">このメソッドは、1 回だけ呼び出すことができ、その他のリーダー メソッドより前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab965-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab965-105">構文</span><span class="sxs-lookup"><span data-stu-id="ab965-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab965-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ab965-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="ab965-107">[in]このリーダーが関連付けられるメタデータ インポーターのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="ab965-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="ab965-108">[in]モジュールのファイル名。</span><span class="sxs-lookup"><span data-stu-id="ab965-108">[in] The file name of the module.</span></span> <span data-ttu-id="ab965-109">使用することができます、`pIStream`パラメーター代わりにします。</span><span class="sxs-lookup"><span data-stu-id="ab965-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="ab965-110">[in]検索するパス。</span><span class="sxs-lookup"><span data-stu-id="ab965-110">[in] The path to search.</span></span> <span data-ttu-id="ab965-111">このパラメーターは省略できます。</span><span class="sxs-lookup"><span data-stu-id="ab965-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="ab965-112">[in]Filename パラメーターの代わりとして使用するファイル ストリーム。</span><span class="sxs-lookup"><span data-stu-id="ab965-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab965-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="ab965-113">Return Value</span></span>  
 <span data-ttu-id="ab965-114">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ab965-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab965-115">コメント</span><span class="sxs-lookup"><span data-stu-id="ab965-115">Remarks</span></span>  
 <span data-ttu-id="ab965-116">1 つだけを指定する必要があります、`filename`または`pIStream`パラメーターは、両方は使用できません。</span><span class="sxs-lookup"><span data-stu-id="ab965-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="ab965-117">
          `searchPath` パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ab965-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab965-118">要件</span><span class="sxs-lookup"><span data-stu-id="ab965-118">Requirements</span></span>  
 <span data-ttu-id="ab965-119">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ab965-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab965-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab965-120">See Also</span></span>  
 [<span data-ttu-id="ab965-121">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ab965-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
