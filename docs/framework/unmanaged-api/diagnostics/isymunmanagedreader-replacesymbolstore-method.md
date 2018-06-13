---
title: ISymUnmanagedReader::ReplaceSymbolStore メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03607cf96d73e96eef63fe62b86b50be02f34421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428203"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="ca3f2-102">ISymUnmanagedReader::ReplaceSymbolStore メソッド</span><span class="sxs-lookup"><span data-stu-id="ca3f2-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="ca3f2-103">既存のシンボル ストアをデルタ シンボル ストアで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ca3f2-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="ca3f2-104">このメソッドがに似ていますが、 [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)メソッド、指定のデルタは、更新プログラムではなく、完全な置き換えとして機能する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="ca3f2-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca3f2-105">1 つだけを指定する必要があります、`filename`または`pIStream`パラメーターは、両方は使用できません。</span><span class="sxs-lookup"><span data-stu-id="ca3f2-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="ca3f2-106">場合`filename`を指定すると、そのファイル内のシンボル、シンボル ストアが更新されます。</span><span class="sxs-lookup"><span data-stu-id="ca3f2-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="ca3f2-107">場合`pIStream`を指定すると、ストアからのデータで更新されます、<xref:System.Runtime.InteropServices.ComTypes.IStream>です。</span><span class="sxs-lookup"><span data-stu-id="ca3f2-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca3f2-108">構文</span><span class="sxs-lookup"><span data-stu-id="ca3f2-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca3f2-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ca3f2-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="ca3f2-110">[in]シンボル ストアを含むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="ca3f2-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="ca3f2-111">[in]代わりに使用する、ファイル ストリーム、`filename`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="ca3f2-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca3f2-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="ca3f2-112">Return Value</span></span>  
 <span data-ttu-id="ca3f2-113">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ca3f2-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca3f2-114">要件</span><span class="sxs-lookup"><span data-stu-id="ca3f2-114">Requirements</span></span>  
 <span data-ttu-id="ca3f2-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ca3f2-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca3f2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca3f2-116">See Also</span></span>  
 [<span data-ttu-id="ca3f2-117">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca3f2-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
