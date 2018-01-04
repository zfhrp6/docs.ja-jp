---
title: "ISymUnmanagedReader2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2
helpviewer_keywords: ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f4b88d891d7b5c1d92006276a290841372aad7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="103a7-102">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="103a7-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="103a7-103">ドキュメント、メソッド、およびシンボル ストア内の変数へのアクセスを提供するシンボル リーダーを表します。</span><span class="sxs-lookup"><span data-stu-id="103a7-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="103a7-104">このインターフェイスは、 [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="103a7-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="103a7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="103a7-105">Methods</span></span>  
  
|<span data-ttu-id="103a7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="103a7-106">Method</span></span>|<span data-ttu-id="103a7-107">説明</span><span class="sxs-lookup"><span data-stu-id="103a7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="103a7-108">GetMethodByVersionPreRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="103a7-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="103a7-109">指定したメソッドのトークンと、エディット コンティニュ バージョン番号、シンボル リーダー メソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="103a7-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="103a7-110">GetMethodsInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="103a7-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="103a7-111">指定のドキュメントに行情報を持つすべてのメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="103a7-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="103a7-112">GetSymAttributePreRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="103a7-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="103a7-113">その名前に基づくカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="103a7-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="103a7-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="103a7-114">Requirements</span></span>  
 <span data-ttu-id="103a7-115">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="103a7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="103a7-116">参照</span><span class="sxs-lookup"><span data-stu-id="103a7-116">See Also</span></span>  
 [<span data-ttu-id="103a7-117">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="103a7-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="103a7-118">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="103a7-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
