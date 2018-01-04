---
title: "ISymUnmanagedWriter::GetDebugInfo メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.GetDebugInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f071bfe88397d6431fb50403c3969d82c5cfe8fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="f7462-102">ISymUnmanagedWriter::GetDebugInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="f7462-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="f7462-103">ポータブル実行可能 (PE) ファイル ヘッダーのデバッグ ディレクトリ エントリを書き込むときにコンパイラに必要な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="f7462-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="f7462-104">シンボル ライターを除くのすべてのフィールドは`TimeDateStamp`と`PointerToRawData`です。</span><span class="sxs-lookup"><span data-stu-id="f7462-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="f7462-105">(コンパイラ、これら 2 つのフィールドを適切に設定します。)</span><span class="sxs-lookup"><span data-stu-id="f7462-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="f7462-106">このメソッドを呼び出す、PE ファイルにデータの blob を出力、設定する必要があります、コンパイラ、 `PointerToRawData` IMAGE_DEBUG_DIRECTORY、出力されたデータをポイントして、IMAGE_DEBUG_DIRECTORY を PE ファイルに書き込むフィールド。</span><span class="sxs-lookup"><span data-stu-id="f7462-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="f7462-107">コンパイラを設定する必要がありますも、`TimeDateStamp`と一致するフィールド、 `TimeDateStamp` PE ファイルが生成されるのです。</span><span class="sxs-lookup"><span data-stu-id="f7462-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7462-108">構文</span><span class="sxs-lookup"><span data-stu-id="f7462-108">Syntax</span></span>  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7462-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f7462-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="f7462-110">[入力、出力].シンボルのライターが入力する IMAGE_DEBUG_DIRECTORY へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f7462-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="f7462-111">[in]A`DWORD`デバッグ データのサイズを格納します。</span><span class="sxs-lookup"><span data-stu-id="f7462-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="f7462-112">[out]ポインター、`DWORD`デバッグ データの格納に必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="f7462-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="f7462-113">[out]シンボル ストアのデバッグ データを保持するのに十分な大きさであるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f7462-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7462-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="f7462-114">Return Value</span></span>  
 <span data-ttu-id="f7462-115">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="f7462-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7462-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="f7462-116">Requirements</span></span>  
 <span data-ttu-id="f7462-117">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f7462-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7462-118">参照</span><span class="sxs-lookup"><span data-stu-id="f7462-118">See Also</span></span>  
 [<span data-ttu-id="f7462-119">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7462-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
