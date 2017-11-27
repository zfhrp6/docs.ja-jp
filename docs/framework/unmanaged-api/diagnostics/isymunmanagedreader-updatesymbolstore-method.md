---
title: "ISymUnmanagedReader::UpdateSymbolStore メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.UpdateSymbolStore
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cfea77814069f6689f7492608548836fdafa591b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="f8743-102">ISymUnmanagedReader::UpdateSymbolStore メソッド</span><span class="sxs-lookup"><span data-stu-id="f8743-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="f8743-103">既存のシンボル ストアをデルタ シンボル ストアで更新します。</span><span class="sxs-lookup"><span data-stu-id="f8743-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="f8743-104">このメソッドは、元のポータブル実行可能 (PE) ファイルにデルタを一致するように、シンボル ストアを更新するエディット コンティニュのシナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="f8743-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8743-105">1 つだけを指定する必要があります、`filename`または`pIStream`パラメーターは、両方は使用できません。</span><span class="sxs-lookup"><span data-stu-id="f8743-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="f8743-106">場合`filename`を指定すると、そのファイル内のシンボル、シンボル ストアが更新されます。</span><span class="sxs-lookup"><span data-stu-id="f8743-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="f8743-107">場合`pIStream`を指定すると、ストアからのデータで更新されます、<xref:System.Runtime.InteropServices.ComTypes.IStream>です。</span><span class="sxs-lookup"><span data-stu-id="f8743-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8743-108">構文</span><span class="sxs-lookup"><span data-stu-id="f8743-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8743-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f8743-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="f8743-110">[in]シンボル ストアを格納しているファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="f8743-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="f8743-111">[in]代わりに使用する、ファイル ストリーム、`filename`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="f8743-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8743-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="f8743-112">Return Value</span></span>  
 <span data-ttu-id="f8743-113">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="f8743-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8743-114">要件</span><span class="sxs-lookup"><span data-stu-id="f8743-114">Requirements</span></span>  
 <span data-ttu-id="f8743-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f8743-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8743-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8743-116">See Also</span></span>  
 [<span data-ttu-id="f8743-117">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8743-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
