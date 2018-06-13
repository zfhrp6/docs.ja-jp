---
title: ISymUnmanagedReader::GetSymbolStoreFileName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b36f4007f286938169cc5d583908493916b9e6f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425341"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="d84c8-102">ISymUnmanagedReader::GetSymbolStoreFileName メソッド</span><span class="sxs-lookup"><span data-stu-id="d84c8-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="d84c8-103">シンボル ストアのディスク上のファイル名を提供します。</span><span class="sxs-lookup"><span data-stu-id="d84c8-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d84c8-104">構文</span><span class="sxs-lookup"><span data-stu-id="d84c8-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d84c8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d84c8-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d84c8-106">[in]サイズ、`szName`バッファー。</span><span class="sxs-lookup"><span data-stu-id="d84c8-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d84c8-107">[out]返される名前の長さを受け取る変数を指すポインター`szName`終端の null を含むです。</span><span class="sxs-lookup"><span data-stu-id="d84c8-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="d84c8-108">[out]シンボル ストアのファイル名を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d84c8-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d84c8-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d84c8-109">Return Value</span></span>  
 <span data-ttu-id="d84c8-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="d84c8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d84c8-111">要件</span><span class="sxs-lookup"><span data-stu-id="d84c8-111">Requirements</span></span>  
 <span data-ttu-id="d84c8-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d84c8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d84c8-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d84c8-113">See Also</span></span>  
 [<span data-ttu-id="d84c8-114">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d84c8-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
