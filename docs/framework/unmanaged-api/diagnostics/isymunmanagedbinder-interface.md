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
ms.openlocfilehash: 5061ce28c4a09f445267c99420bf1942d99076bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="a665b-102">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a665b-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="a665b-103">アンマネージ コードのシンボル バインダーを表します。</span><span class="sxs-lookup"><span data-stu-id="a665b-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a665b-104">信頼できないソースからプログラム データベース (PDB) ファイルを開く、セキュリティ上のリスクを勧めします。</span><span class="sxs-lookup"><span data-stu-id="a665b-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a665b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a665b-105">Methods</span></span>  
  
|<span data-ttu-id="a665b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a665b-106">Method</span></span>|<span data-ttu-id="a665b-107">説明</span><span class="sxs-lookup"><span data-stu-id="a665b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a665b-108">GetReaderForFile メソッド</span><span class="sxs-lookup"><span data-stu-id="a665b-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="a665b-109">メタデータ インターフェイスおよびファイル名を指定して、正しい返します <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 構造体、モジュールに関連付けられているデバッグ シンボルを読み取ることです。</span><span class="sxs-lookup"><span data-stu-id="a665b-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="a665b-110">GetReaderFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="a665b-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="a665b-111">メタデータ インターフェイスおよびをシンボル ストアを格納するストリームを指定して、正しい返します <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> デバッグを読み取る構造は、特定のシンボル ストアからシンボルします。</span><span class="sxs-lookup"><span data-stu-id="a665b-111">Given a metadata interface and a stream that contains the symbol store, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a665b-112">要件</span><span class="sxs-lookup"><span data-stu-id="a665b-112">Requirements</span></span>  
 <span data-ttu-id="a665b-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a665b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a665b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a665b-114">See Also</span></span>  
 [<span data-ttu-id="a665b-115">シンボル ストア診断インターフェイスします。</span><span class="sxs-lookup"><span data-stu-id="a665b-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="a665b-116">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a665b-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="a665b-117">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a665b-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
