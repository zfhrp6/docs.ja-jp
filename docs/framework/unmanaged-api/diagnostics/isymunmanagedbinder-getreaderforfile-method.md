---
title: "ISymUnmanagedBinder::GetReaderForFile メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderForFile
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c50bb4ca36043fc2491c9a0615b682c94c422e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="362ac-102">ISymUnmanagedBinder::GetReaderForFile メソッド</span><span class="sxs-lookup"><span data-stu-id="362ac-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="362ac-103">メタデータ インターフェイスおよびファイル名を指定して、正しい返します <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 構造体、モジュールに関連付けられているデバッグ シンボルを読み取ることです。</span><span class="sxs-lookup"><span data-stu-id="362ac-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="362ac-104">実行可能ファイルの横にある場合にのみ、このメソッドは、プログラム データベース (PDB) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="362ac-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="362ac-105">セキュリティのために変更されています。</span><span class="sxs-lookup"><span data-stu-id="362ac-105">This change has been made for security purposes.</span></span> <span data-ttu-id="362ac-106">PDB ファイルをより広範な検索を実行する場合を使用して、 [isymunmanagedbinder 2::getreaderforfile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="362ac-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="362ac-107">構文</span><span class="sxs-lookup"><span data-stu-id="362ac-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="362ac-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="362ac-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="362ac-109">[in]メタデータ インポート インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="362ac-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="362ac-110">[in]ファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="362ac-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="362ac-111">[in]検索パスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="362ac-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="362ac-112">[out]設定されているポインターに返された <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="362ac-112">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="362ac-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="362ac-113">Return Value</span></span>  
 <span data-ttu-id="362ac-114">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="362ac-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="362ac-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="362ac-115">Requirements</span></span>  
 <span data-ttu-id="362ac-116">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="362ac-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="362ac-117">参照</span><span class="sxs-lookup"><span data-stu-id="362ac-117">See Also</span></span>  
 [<span data-ttu-id="362ac-118">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="362ac-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="362ac-119">GetReaderForFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="362ac-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
