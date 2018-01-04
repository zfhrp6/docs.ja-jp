---
title: "ISymUnmanagedBinder インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder
helpviewer_keywords: ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79d3758f57976d08d4599de500e2e12e4d67cb4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="dd7f6-102">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd7f6-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="dd7f6-103">アンマネージ コードのシンボル バインダーを表します。</span><span class="sxs-lookup"><span data-stu-id="dd7f6-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dd7f6-104">信頼できないソースからプログラム データベース (PDB) ファイルを開く、セキュリティ上のリスクを勧めします。</span><span class="sxs-lookup"><span data-stu-id="dd7f6-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd7f6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dd7f6-105">Methods</span></span>  
  
|<span data-ttu-id="dd7f6-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="dd7f6-106">Method</span></span>|<span data-ttu-id="dd7f6-107">説明</span><span class="sxs-lookup"><span data-stu-id="dd7f6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd7f6-108">GetReaderForFile メソッド</span><span class="sxs-lookup"><span data-stu-id="dd7f6-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="dd7f6-109">メタデータ インターフェイスおよびファイル名を指定して、正しい返します[ISymUnmanagedReader](isymunmanagedreader-interface.md)構造体、モジュールに関連付けられているデバッグ シンボルを読み取ることです。</span><span class="sxs-lookup"><span data-stu-id="dd7f6-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="dd7f6-110">GetReaderFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="dd7f6-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="dd7f6-111">メタデータ インターフェイスおよびをシンボル ストアを格納するストリームを指定して、正しい返します[ISymUnmanagedReader](isymunmanagedreader-interface.md)デバッグは読み取りを構造体は、特定のシンボル ストアからシンボルします。</span><span class="sxs-lookup"><span data-stu-id="dd7f6-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd7f6-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="dd7f6-112">Requirements</span></span>  
 <span data-ttu-id="dd7f6-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dd7f6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd7f6-114">参照</span><span class="sxs-lookup"><span data-stu-id="dd7f6-114">See Also</span></span>  
 [<span data-ttu-id="dd7f6-115">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd7f6-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="dd7f6-116">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd7f6-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="dd7f6-117">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd7f6-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
